
[Go back](./index.md)


**Written by / Skrevet af [Theis Pieter](https://tphollebeek.netlify.app/)**


# Express `Request`, `Response` og Middleware
## Forord
I en express endpoint funktion, f.eks. `/welcome`,
```js
app.get('/welcome', (request, response) => ...);
```
Forkortes `request` og `response` næsten altid til:
```js
app.get('/welcome', (req, res) => ...);
```
Så hvis der står `req` eller `res` er det dette der referreres til.

---

I de fleste links, peges der til `side.dk`. 

Det bruges bare som en pladsholder for hvad IPen til din hjemmeside rigtigt ville være, f.eks. `localhost:8000`, og er ikke en rigtig hjemmeside.
# `request` ("anmodning")
## Dit `req` objekt:
- Er en class, der håndterer alt det data, som klienten har sendt med deres anmodning.

## De vigtige dele:
### `req.query`: query string, 
- Et query, er det data der foreholder sig efter `?` i en url.
    
    Dvs. at hvis klienten går ind på `side.dk/welcome?user=person&greeting=hello`, så ville `req.query` være et objekt som dette:
    ```json
    {
        "user": "person",
        "greeting": "hello"
    }
    ```
### `req.params`: URL Parameters
- En URL Parameter, er noget data du kan få fra selve URLen, uden at skulle bruge f.eks. queries.
    
    Dvs. at hvis du havde et endpoint, for at kunne gå ind på en brugers profil der lignede dette:
    ```js
    app.get('/:id/profile', (req, res) => ...);
    ```
    Og så gik ind på `test.dk/1234/profile`,
    ville `req.params` ligne dette:
    ```json
    {
        "id": "1234"
    }
    ```
    Du kan have mere end én parameter i ét endpoint, hvis det kræves, f.eks. hvis du har et endpoint, hvor brugeren kan få et billede ud fra form og farve.
    ```js
    app.get('/:shape/:color', (req, res) => ...);
    ```
    Og brugeren så går ind på `/firkant/gul`, ville `req.params` ligne dette:
    ```json
    {
        "shape": "firkant",
        "color": "gul"
    }
### `req.body`: den request body, som klienten sender
- ### **[ !!! ]: `req.body` kræver middleware for at fungere som forventet**

- En request body er typisk data der ikke forekommer i URLen, og bruges til de fleste requests, der ikke er `GET`, f.eks. `POST` eller `PUT`.

    Hvis du har et endpoint `/login` med `POST`, for at håndtere logins, og du så fra klienten sender en `POST` request med fetch der ligner dette:
    ```js
    fetch('side.dk', {
        headers: ...,
        method: 'POST',
        body: JSON.stringify({
            username: 'bruger',
            password: 'kode1234'
        }),
    })
    ```
    Ville `req.body` så ligne dette:
    ```json
    {
        "username": "bruger",
        "password": "kode1234"
    }
    ```

    Du kan også se, at vi fra klienten faktisk ikke sender et json objekt, men i stedet sender et json-formatteret string. Det ville normalt skulle konverteres til et normalt objekt på serveren, men det behøver du heldigvis ikke, da din middleware gør det for dig automatisk.
### `req.cookies`: klienten's cookies
- ### **[ !!! ]: `req.cookies` kræver middleware for at fungere som forventet**

- Cookies er noget data, som browseren gemmer på lokalt. Hvis du logger ind på noget, gemmer den typisk at du er logget ind med cookies, gennem noget der hedder en `token`.
    
    Cookies fjernes typisk efter at browseren lukkes, medmindre andet er specificeret på selveste cookien; en cookie der fjernes efter browseren bliver lukket kaldes en "**session cookie**".
    
    Cookies bliver automatisk sendt med enhver request, lige meget hvilken side de er fra, medmindre at der er specificeret i cookien at den kun skal sendes hvis man er på siden som den kom fra.

    Hvis du havde et endpoint, der hedder `/setcookies`, som så sender en cookie kaldet `cookie_type` med en værdi af `chocolate_chip`
    ```js
    app.get('/setcookies', (req, res) => res.cookie('cookie_type', 'chocolate_chip'));
    ```
    Og har et endpoint `/getcookies`.
    ```js
    app.get('/getcookies', (req, res) => ...);
    ```
    Ville `req.cookies` ligne dette:
    ```json
    {
        "cookie_type": "chocolate_chip"
    }
    ```
# `response` ("svar")
## Dit `res` objekt:
- Er en class, der håndterer det svar, som du ville give til klienten's anmodning.
## De vigtige dele:
### `res.status`: set en status på svaret
- En "**response status**" er en kort kode der forklarer noget information om hvordan behandlingen af klientens anmodning gik.
    
    Her er en liste af de statuskoder, du nok oftes kommer til at bruge: 
    
    | Kode | Navn                  | Bruges til
    |------|-----------------------|------------
    |`200` | OK                    | Når serveren havde success i at håndtere anmodningen.
    |`201` | Created               | Når serveren havde success, og skabte noget, f.eks. en besked på en blogside.
    |`400` | Bad Request           | Serveren kunne ikke håndtere anmodningen, på grund af at klientens anmodning ikke var korrekt. F.eks. du logger ind uden at sende en adgangskode.
    |`401` | Unauthorized          | Når klienten ikke må få adgang til den resource, og serveren ikke kender deres identitet, f.eks. hvis de prøver at gå ind på `/admin`, men de ikke er logget ind.
    |`403` | Forbidden             | Når klienten ikke må få adgang til den resource, men serveren kender deres identitet, f.eks. hvis de prøver at gå ind på `/admin`, men de bare er en normal bruger.
    |`404` | Not Found             | Ressourcen klienten vil have, findes ikke. Sker også hvis du prøver at sende en request til noget der ikke eksister, f.eks. `/djiawjdiawjd`.
    |`500` | Internal Server Error | Der opstod en fejl på serveren, mens den prøvede at håndtere anmodningen.
    |`501` | Not Implemented       | Ressourcen eksisterer, men den er ikke udviklet endnu.
    |`502` | Bad Gateway           | Noget gik galt mens serveren prøvede at sende klienten et sted hen

    Statuskoderne mellem `100-199` bruges for at svare på information omkring anmodningen; disse håndteres typisk automatisk og er ikke noget du behøver at bruge.

    Statuskoderne mellem `200-299` bruges, hvis anmodningen blev behandlet uden fejl.

    Statuskoderne mellem `300-399` bruges, hvis anmodningen endte med at sende dig videre til et nyt sted, f.eks. fra `/admin` til `/login`.

    Statuskoderne mellem `400-499` bruges, hvis anmodningen ikke kunne behandes på grund af noget som klienten gjorde forkert.

    Statuskoderne mellem `500-599` bruges, hvis anmodningen ikke kunne behandles på grund af noget som serveren gjorde forkert.

### `res.send`: send lidt af hvert
- Som forklaret så sender `res.send` umiddelbart lige hvad du vil.

    Det bruges oftes til at sende tekst eller json.
    
    Hvis du sender tekst tilbage, renderer browseren teksten, som om det var html, f.eks. hvis du havde et endpoint `/welcome`, som sender en velkomstbesked tilbage med **fed skrift**,

    ```js
    app.get('/welcome', (req, res) => res.send('<b>Welcome!</b>'));
    ```

    Og så går ind på `side.dk/welcome`, ville det være korrekt formatteret.

    Jeg vil dog anbefale at bruge `res.sendFile` og bare sende html-filer i stedet, hvis du vil sende html.

    Du kan desuden også bruge det til at sende JSON objekter:

    ```js
    app.get('/welcome-json', (req, res) => res.send({'msg': 'welcome'}));
    ```

    Jeg vil dog anbefale, at du bruger `res.json` for dette i stedet, da det er mere klart hvad du sender tilbage.

### `res.sendFile`: send filer
- Som den forklarer, bruges det til at sende filer fra serveren til klienten.

### `res.json`: send json data
- Dette gør akkurat det samme som at bare sende json med `res.send`, men det er mere forklarende at du sender json, når du bruger `res.json` frem for `res.send`.

### `res.cookie`: send en cookie
- Dette sender et svar til klienten, at de skal gemme noget data gennem cookies lokalt.
    
    Hvis du vil, kan du også sætte nogle `options`, "indstillinger", som den cookie der sættes skal have, f.eks. hvornår den skal udløbe, hvor sikker den er og hvis den skal sende hvis du ikke er på samme side.

    Her er nogen af de `options` du nok kommer til at bruge mest, ellers kan du finde en fuld liste fra express docs.
    
    | Navn     | Format | Info
    |----------|--------|------
    | maxAge   | Number | hvor gammel din cookie kan være, før den udløber, i millisekunder. hvis den ikke sættes eller er sat til 0, bliver cookien til en session cookie
    | expires  | Date   | Date objekt der siger hvornår cookien skal udløbe i GMT. Du kommer dog nok mest til at bruge maxAge
    | httpOnly | Bool   | markerer at man ikke skal kunne få adgang til cookien med JavaScript, hvilket gør den mere sikker mod snyd
    | secure   | Bool   | markerer at cookien kun skal sendes over HTTPS forbindelser, hvilket gør den mere sikker mod snyd
    | sameSite | Bool   | markerer at cookien kun skal sendes hvis du er på samme side, hvilket gør den mere sikker mod snyd

    Hvis du ikke sætter `options`, finder den ud af hvad den skal sende selv, men jeg vil anbefale at sætte `httpOnly` og `sameSite` selv.

# Middleware
## Middleware:
- Middleware i express bruges til at håndtere klientens anmodning før den kommer til sin endelige destination.

    Du bruger middleware ved at skrive `app.use(<middleware>)`.

    Det middleware du nok kommer til at bruge mest er `cors`, `express.json`, `express.urlencoded`, `cookie-parser` og routere.

    Middlewaren `cors` og `cookie-parser` følger ikke med express normalt, de skal downloades med henholdsvis `npm install cors` og `npm install cookieParser`

    De gør henholdsvis at du bruger cors (Cross-Origin Resource Sharing), hvilket er et krav hvis du skal indlæse noget fra en anden side end din egen, og at du kan læse data som er sendt i `json` eller `urlencoded` format, f.eks. `req.body`, og `cookieParser` gør, at du har adgang til `req.cookies`.

    Selv hvis du ikke planlægger at skulle bruge cors, json eller cookies ville jeg stærkt anbefale at bruge det alligevel, da det så redder dig fra at skulle bruge tid på at finde ud af hvorfor `req.body` ikke eksisterer eller lignende, hvis du alligevel skulle bruge det senere hen.

    Et eksempel på en server med middleware kunne ligne sådan:
    ```js
    import express from "express";
    import cookieParser from 'cookie-parser';
    import cors from "cors";

    const app = express();
    app.use(cors());
    app.use(express.json());
    app.use(express.urlencoded({ extended: false}));
    app.use(cookieParser());
    ```

**Written by / Skrevet af [Theis Pieter](https://tphollebeek.netlify.app/)**

[Go back](./index.md)
