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

#### Perform a GET request on window.onload event and display the results in a block of elements in html:
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

## Full Axios Documentation
https://github.com/axios/axios/blob/master/README.md
