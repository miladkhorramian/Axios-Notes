# Axios-Notes
Descripted Notes for Axios Ajax Interacting with Json PlaceHolder.

Include Axios by CDN.

`<script src="https://cdnjs.cloudflare.com/ajax/libs/axios/0.19.0/axios.min.js"></script>`

### Get 5 Objects and Print Each Result in a line:

`
// USING FOREACH LOOP TO GET DATA
axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(res => {
        res.data.forEach(function(index){
            console.log(index.id);
        })
    })
    .catch(err => console.error(err));
`
