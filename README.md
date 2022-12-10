### Linki do dokumentacji postmana

Skrypty w postmanie: 
https://learning.postman.com/docs/writing-scripts/intro-to-scripts/

Dokumentacja testów:
https://learning.postman.com/docs/writing-scripts/script-references/test-examples/

Dokumentacja JavaScript dla postman:
https://learning.postman.com/docs/writing-scripts/script-references/postman-sandbox-api-reference/


### Zmienne w oostmanie

Tworzenie zmiennej / zmiennej globalnej / zmiennej środowiskowej / zmiennej w kolekcji

```js 
pm.variables.set("variable_key", "variable_value");
pm.globals.set("variable_key", "variable_value");
pm.environment.set("variable_key", "variable_value");
pm.collectionVariables.set("variable_key", "variable_value");
```

Pobieranie wartości zmiennej / zmiennej globalnej / zmiennej środowiskowej / zmiennej w kolekcji

```js 
pm.variables.get("variable_key");
pm.globals.get("variable_key");
pm.environment.get("variable_key");
pm.collectionVariables.get("variable_key");
```

### Query param  w pre-request script 


Dodawanie query param z poziomu pre-request scriptu
```js 
pm.request.addQueryParams("key=value")
```

Dodawanie query param z poziomu pre-request scriptu gdzie wartość jest brana ze zmiennej o nazwie 'xxx'
```js 
pm.request.addQueryParams("key={{xxx}}")
```


### Testy

Sprawdzenie, że response code to 200
```js 
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

```

Sprawdzenie, że response code to 201 lub 200
```js 
pm.test("Successful POST request", function () {
    pm.expect(pm.response.code).to.be.oneOf([201, 202]);
});
```

Sprawdzenie, że response body zawiera string
```js 
pm.test("Body matches string", function () {
    pm.expect(pm.response.text()).to.include("string_you_want_to_search");
});
```

Sprawdzenie, że id w obiekcie json ma wartość 100
```js 
pm.test("Your test name", function () {
    var jsonData = pm.response.json();
    pm.expect(jsonData.id).to.eql(100);
});
```

Sprawdzenie, że json jest równy konkretnemu stringowi
```js 
pm.test("Body is correct", function () {
    pm.response.to.have.body("response_body_string");
});
```

Sprawdzenie, że response zawiera nagłówek Content-Type
```js 
pm.test("Content-Type is present", function () {
    pm.response.to.have.header("Content-Type");
});
```


Sprawdzenie, że response time jest mniejsze niż 200ms
```js 
pm.test("Response time is less than 200ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(200);
});
```

