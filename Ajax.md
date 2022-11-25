# Ajax
## Ajax
- Ajax stands for "Asynchronous Javascript And XML".
- Ajax allows web change content dynamically without reloading the page.


## 1. Ajax Basic

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
Json will appear slower that h1 element because Ajax is asynchronous.
![image](https://user-images.githubusercontent.com/79159894/203877196-2196c557-6c61-49cf-8e31-a8a80fe5ede2.png)

## 2. Use get to sned parameter

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


## 3-1. Use post request to sned String parameter

- parameters are in form data
![image](https://user-images.githubusercontent.com/79159894/203881855-15a8b537-349e-40b9-aa35-72f823918fb4.png)

## 3-2. Use post to send parameter json

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
- Request json      
![image](https://user-images.githubusercontent.com/79159894/203882705-de549d00-4a2a-4589-a1cf-da68b776d783.png)

## 4. Ajax test Server

### install Flask in python
Open terminal in vscode
```
PS D:\web_20221123> pip install flask --user
```
- Build a py file for server
```python
from flask import Flask, request, render_template

app = Flask(__name__)  # Flask is the framework to build web server


@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'GET':
        return 'get request success'
    elif request.method == 'POST':
        return "post request success"


@app.route('/')
def test():
    return render_template('ajax_03.html')  # test ajax_03.html


if __name__ == "__main__":
    app.run(debug=True)  # debug = True to let error display on webpage
```
- Right click, select `run python in terminal`
![image](https://user-images.githubusercontent.com/79159894/203896532-0131f0ca-d03c-4e77-b74c-89fa0554611e.png)

- Go to `http://127.0.0.1:5000/`
- We can see `ajax_03.html` running on it.

![image](https://user-images.githubusercontent.com/79159894/203896662-51471ec4-b801-4ca7-ab58-413c6c70a644.png)
https://stackoverflow.com/questions/51912999/could-not-install-packages-due-to-an-environmenterror-winerror-5-access-is-de


## Use Ajax in JQuery

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Ajax 5 JQuery</title>
    <!-- import jquert -->
    <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
</head>

<body>

    <script>
        // ready jquery
        $(document).ready(function () {
            // when click the button
            $("#fetch").click(function (event) {
                // get the id and title from json
                $.getJSON("https://jsonplaceholder.typicode.com/posts", function (emp) {
                    // use for loop to print them in table
                    for (let i = 0; i < emp.length; i++) {
                        $("table").append(
                            "<tr>" + "<td>" + emp[i].id +
                            "</td>" + "<td>" + emp[i].title + "</td>" + "</tr>")
                    }


                })
            })
        })
    </script>

    <h1>click to fetch the id and title from json</h1>
    <input type="button" id="fetch" value="Fetch Data">

    <table>
        <tr>
            <td>id</td>
            <td>title</td>
        </tr>
    </table>

</body>

</html>
```
### Before click
![image](https://user-images.githubusercontent.com/79159894/203903357-15cbfd11-646d-4ae7-a9b1-de273369894e.png)

### After clicked - Get the all id and title
![image](https://user-images.githubusercontent.com/79159894/203903318-8c5be452-0d38-40b3-a743-71c14f3707ad.png)

https://www.bilibili.com/video/BV16W4y1x7eR?p=11&spm_id_from=pageDriver&vd_source=004e8f10a21c55becb57d8295b5ff681
