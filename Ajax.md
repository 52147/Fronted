# Ajax
## 1. Ajax
- Ajax is "Asynchronous Javascript And XML"
- Ajax allow web change content dynamically without reloading the page.


## Ajax Basic

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
