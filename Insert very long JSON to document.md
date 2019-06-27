As mongo shell is js based, using `insertOne()` or `insertMany()` throws error `+0000 E QUERY    [js] SyntaxError: unterminated string literal @(shell):*:****`
because of string length restriction in js. The Simple work around is as follows:

#### Method: 1
```
var file = cat('/root/sample.json');
use <dbName>
var o = JSON.parse(file);
db.<documentName>.insert(o)
```
---
o/p:  WriteResult({ "nInserted" : 1 })
___
#### Method: 2
```
mongoimport --jsonArray --db test --collection docs --file example2.json
```
or
```
mongoimport --db test --collection docs --file example2.json
```
---
O/P:  WriteResult({ "nInserted" : 1 })
___
