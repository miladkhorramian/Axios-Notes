# Axios-Notes
Descripted Notes for Axios Ajax Interacting with Json PlaceHolder.

Include Axios by CDN.
```
<script src="https://cdnjs.cloudflare.com/ajax/libs/axios/0.19.0/axios.min.js"></script>
```

#### Make an Axios Get request and print the results in console.
`axios.get('URL')` returns an object.
```
axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(res => {
        console.log(res);
    })
    .catch(err => console.error(err));
```

#### Perform a `POST` request.
```
axios.post('https://jsonplaceholder.typicode.com/posts' , {
  title: 'New', completed: false  
})
    .then(res => {
    console.log(res);
    })
    .catch(err => {console.error(err)});
```
#### Get 5 Objects and Print Each Result in a line:
```
axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(res => {
        res.data.forEach(function(index){
            console.log(index.id);
        })
    })
    .catch(err => console.error(err));
```

#### Get different properties and print each in a different line:
We use `axios.get('URL')` and store in an array. Only get `data`.
```
axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(res => {
        var jsonObject;
        jsonObject = res.data;
        for (var i in jsonObject){
            console.log(res.data[i].id + '\n' + res.data[i].title + '\n' + res.data[i].body);
        }
    })
    .catch(err => console.error(err));
```

#### Perform a `GET` request on window.onload event and display the results in a block of elements in html:
```
window.onload = function(){
    var postRow = document.getElementById('YOUR HTML ELEMENT ID'); //The element you want to display posts in.
    
    axios.get('https://jsonplaceholder.typicode.com/posts?_limit=5')
        .then(res => {
            console.log('Axios get request responded');
            for(var i = 0;i < res.data.length;i++){
                var post;
                post = document.createElement('div');
                post.innerHTML = `
                    <h1>${res.data[i].title}</h1>
                    <p>${res.data[i].body}</p>
                `;
                postRow.appendChild(post);
            }
        })
        .catch(err => console.error(err));  
};
```
##### Real Example
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Get and Build a Block</title>
    <script src="https://cdnjs.cloudflare.com/ajax/libs/axios/0.19.0/axios.min.js"></script>
    <script>
        window.onload = function(){
        
            var postRow = document.getElementById('postRow'); //Id of the div to insert posts in.
            
            axios.get('https://jsonplaceholder.typicode.com/posts?_limit=5')
                .then(res => {
                    console.log('Axios get request responded');
                    for(var i = 0;i < res.data.length;i++){
                        var post;
                        post = document.createElement('div');
                        post.classList.add('post');
                        post.innerHTML = `
                    <h1>${res.data[i].title}</h1>
                    <p>${res.data[i].body}</p>
                `;
                        postRow.appendChild(post);
                    }
                })
                .catch(err => console.error(err));
        };
    </script>
    <style>
        *{box-sizing:border-box}
        html, body {height: 100%;}
        body {margin: 0;padding: 0}
        h1, h2, h3, h4, h5, h6, div, p, span {font-family:Lato;}
        .post{float:left;width:19%;padding:4px 10px;border:1px solid #000;margin:10px .5%}
        .heading{font-size:1.4em;font-weight:bolder}
        .description{font-size:1.2em}
    </style>
</head>
<body>
<div id="postRow" style="width:90%;margin:auto"></div>
    <h1 id="head">Simple JS Test</h1>
</body>
</html>
```

## Full Axios Documentation
https://github.com/axios/axios/blob/master/README.md
