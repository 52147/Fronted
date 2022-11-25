# Ajax
## 1. Ajax
- Ajax is "Asynchronous Javascript And XML"
- Ajax allow web change content dynamically without reloading the page.


## Ajax Basic

```html
<!DOCTYPE html>
<html>

<head>
    <title>01-Ajax Basic Use</title>
    <meta charset="UTF-8" />
</head>

<body>
    <h1>Ajax 01 Basic Use</h1>
    <div id="app"></div>
    <script>
        // 1. create Ajax object
        var xhr = new XMLHttpRequest();
        // 2. tell Ajax to use what way to send the request to where
        xhr.open("get", "http://httpbin.org/get");
        // 3. send the request
        xhr.send();
        // 4. handle the response
        xhr.onload = function () {
            app = document.getElementById("app");
            app.innerHTML = xhr.responseText;
            // console.log(xhr.responseText);
        };
    </script>
</body>

</html>
```
Json will appear slower because Ajax is asynchronous.
![image](https://user-images.githubusercontent.com/79159894/203877196-2196c557-6c61-49cf-8e31-a8a80fe5ede2.png)

## Use get to pass parameter

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ajax 02 send parameter use get request</title>
</head>

<body>

    <h1>Ajax 02 send parameter use get request</h1>
    name: <input type="text" id="name"><br />
    password: <input type="password" id="pwd"><br />
    <input type="button" value="reveive data" onclick="submitForm()">

    <script>
        function submitForm() {
            var name = document.getElementById("name").value;
            var pwd = document.getElementById("pwd").value;

            url = "http://httpbin.org/get"
            url = url + "?name=" + name + "&pwd=" + pwd
            var xhr = new XMLHttpRequest()
            xhr.open('get', url)
            xhr.send()
            xhr.onload = function () {
                console.log(xhr.responseText)
            }
        }
    </script>

</body>

</html>
```

Name and password be added in url.
![image](https://user-images.githubusercontent.com/79159894/203878573-27137b80-e950-48e6-b64b-46f2ac5d9782.png)
![image](https://user-images.githubusercontent.com/79159894/203878633-14de1d97-b908-43c8-b42c-827619653245.png)


## Use post request to pass String parameter
```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ajax 03 use post request to send parameter</title>
</head>

<body>
    <h1>Ajax 03 use post request to send parameter</h1>
    name:<input type="text" id="name"><br />
    password:<input type="password" id="pwd"><br />
    <input type="button" value="receive data-str" onclick="submitForm1()">
    <input type="button" value="receive data-json" onclick="submitForm2()">

    <script>
        function submitForm1() {
            var name = document.getElementById("name").value;
            var pwd = document.getElementById("pwd").value;
            url = "http://httpbin.org/get";
            params = "name = " + name + "&pwd=" + pwd;
            var xhr = new XMLHttpRequest()
            xhr.open('post', url)
            xhr.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded');
            xhr.send(params)
            xhr.onload = function () {
                console.log(xhr.responseText)
            }
        }

        function submitForm2() {
            var name = document.getElementById("name").value;
            var pwd = document.getElementById("pwd").value;
            url = "http://httpbin.org/get";
            // json params
            params = {
                "name": name,
                "pwd": pwd
            };
            // convert json to string
            params = JSON.stringify(params)
            var xhr = new XMLHttpRequest()
            xhr.open('post', url)
            xhr.setRequestHeader('Content-Type', 'application/json');
            xhr.send(params)
            xhr.onload = function () {
                console.log(xhr.responseText)
            }
        }
    </script>

</body>

</html>
```
- parameters are in form data
![image](https://user-images.githubusercontent.com/79159894/203881855-15a8b537-349e-40b9-aa35-72f823918fb4.png)

## Use post get parameter json

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ajax 04 State use</title>
</head>

<body>
    <h1>Ajax 04 State use</h1>
    <input type="button" value="send data" onclick="submitForm()">

    <script>
        function submitForm() {
            var xhr = new XMLHttpRequest();
            xhr.open("open", url);
            xhr.send();
            // when server is ready what function we want to do
            xhr.onreadystatechange = function () {
                console.log(xhr.readyState);
            }
        }
    </script>

</body>

</html>
```
- Request json
![image](https://user-images.githubusercontent.com/79159894/203882705-de549d00-4a2a-4589-a1cf-da68b776d783.png)


