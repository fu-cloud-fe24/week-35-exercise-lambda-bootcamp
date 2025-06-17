# Vecka 35 : AWS Lambda Bootcamp

## Innan du sätter igång

**Samtliga övningar kräver att din Lambdafunktion anropas via _egen URL_. Den skapas under `Configuration`sen `Lambda URL`, sälj sedan `None`. Nu ska du se en fin URL som leder direkt till din Lambdafunktion, ex.**

```
https://atj0pr0sitjwrhg5k53jf5a0ltyse.lambda-url.eu-north-1.on.aws/
```

## Basics

1. Skapa en funktion som vid anrop returnerar textsträngen:

```
Hejsan hallå, din snea tå!
```

2. Skapa en funktion som vid anrop returnerar vilken route du än anger.

```
<lamba_URL>/hello // hello
<lambda_URL>/pannkaka // pannkaka
<lambda_URL>/lsfjhsadfyusdfhjkasdhjkf // lsfjhsadfyusdfhjkasdhjkf
```

3. Skapa en funktion som på routen `/cat` returnerar textsträngen "Mjau!" och vid routen `/dog`returnerar "Woff!".

```
<lamba_URL>/cat // Mjau!
<lambda_URL>/dog // Woff!
```

4. Skapa en funktion som vid anrop returnerar vilken metod (GET, PUT, POST, PATCH etc ) som används. Testa anropa den med några olika metoder via en _http-klient_, ex. [Postman](https://postman.com).

```
GET <lamba_URL> // GET
POST <lamba_URL> // POST
PATCH <lambda_URL> // PATCH
```

5. Skapa en funktion som slumpar fram ett skämt ur en array med 5st fördefinerade skämt. Ju sämre skämt, desto bättre.

```
GET <lamba_URL>/joke // Where does bad light end up? - In prism.
```

6. Skapa en funktion som vid alla andra metoder än PUT returerar error:

```js
{
    statusCode: 405,
    body: JSON.stringify({ message: 'Method not allowed.'})
}
```

Vid PUT ska följande returneras:

```js
{
    statusCode: 200,
    body: JSON.stringify({ message: 'Welcome!'})
}
```

7. Skapa en funktion som tar emot en POST med nedan JSON. Funktionen ska returnera ett svar där texten står omvänt.

```json
{
  "text": "Hello there!" // !ereht olleH
}
```

## Mer än Basic

8. Gör en funktion som genererar ett _slumpat lösenord_. Man ska kunna justera längden genom att skicka in en `Query param`.

```
<lambda_URL>/password?len=30 // genererar ett 30 tecken långt lösenord
```

9. Gör övning 8, men gör lösenordsgeneratorn konfigurerbar genom att posta in ett object med följande params:

```js
{
    length: Number, // Lösenordets minsta längd
    capital: Boolean, // Lösenordet innehåller minst 1 stor bokstav
    lower: Boolean, // Lösenordet innehåller minst 1 liten bokstav
    numbers: Boolean, // Lösenordet innehåller minst 1 siffra
    symbols: Boolean // Lösenordet innehåller minst 1 symbol
}
```

Lösenordet som genereras måste vara minst 8 tecken långt.

## AWS CLI - Koda API lokalt
Koda upp ett todo-api lokalt på din dator, och använd ditt AWS CLI för att zippa och deploya dina filer.
API:et skall innehålla en array av objekt som ser ut enligt följande:
```
{
    id : 1,
    task : 'Hitta pengar',
    done : false
}
```
Skapa upp funktionalitet för att utföra de fyra vanligaste HTTP-metoderna (GET, POST, PUT, DELETE).

### Basic

#### GET
Genom ett GET-anrop skall man kunna hämta alla todouppgifter i arrayen.

#### POST
Genom ett POST-anrop där du skickar med ett nytt objekt i eventets body skall du lägga till den nya todon i arrayen.

### Level Up

#### GET
Använd dig av query parametrar för att hämta en specifik todo.

#### PUT
Genom ett PUT-anrop där du anger vilken todo som skall uppdateras i en query parameter, så skall den angivna todon toggla "done".

#### DELETE
Genom ett DELETE-anrop där du anger vilken todo som skall tas bort i en query parameter, så skall den angivna todon raderas.
