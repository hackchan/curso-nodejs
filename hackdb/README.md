# hackdb

##usage
```js
const setupDatabase = require('hackdb')

setupDatabase(config).then(db =>{
    const {Agent, Metric} = db
})

. catch(err =>{
    console.log(err)
})

```