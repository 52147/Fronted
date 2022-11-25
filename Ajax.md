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
    <title>Ajax 02 pass parameter use get request</title>
</head>

<body>

    <h1>Ajax 02 pass parameter use get request</h1>
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

