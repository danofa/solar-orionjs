# solar-orionjs
Solarwinds Orion nodejs module

Usage:
```
var orion = require("solar-orionjs")({
    server: "127.0.0.1",
    port: 17778,
    auth: { 
        username:"admin",
        password:""
    }   
});
```    
---
## Functions

<dl>
<dt><a href="#Orion">Orion()</a></dt>
<dd><p>Class definition</p>
</dd>
<dt><a href="#query">query(query, callback)</a></dt>
<dd><p>Performs a SWQL query</p>
</dd>
<dt><a href="#update">update(update, swisUri, callback)</a></dt>
<dd><p>Update Orion object</p>
</dd>
<dt><a href="#read">read(swisUri, callback)</a></dt>
<dd><p>Read Orion object</p>
</dd>
<dt><a href="#create">create(data, object, callback)</a></dt>
<dd><p>Create Orion object</p>
</dd>
<dt><a href="#invoke">invoke(verb, data, callback)</a></dt>
<dd><p>Performs an Orion verb invoke</p>
</dd>
<dt><a href="#remove">remove(swisUri, callback)</a></dt>
<dd><p>remove Orion object</p>
</dd>
<dt><a href="#removeBulk">removeBulk(swisUris, callback)</a></dt>
<dd><p>Bulk remove Orion objects</p>
</dd>
<dt><a href="#getOptions">getOptions()</a> ⇒ <code>object</code></dt>
<dd><p>Get options</p>
</dd>
<dt><a href="#setOptions">setOptions(options)</a></dt>
<dd><p>Set options</p>
</dd>
</dl>

<a name="Orion"></a>

## Orion()
Class definition

**Kind**: global function  
**Example**  
```js
var orion = require("solar-orionjs")({
     server: "127.0.0.1",
     port: 17778,
     auth: {
         username: "admin",
         password: "password"
     }
});
```
<a name="query"></a>

## query(query, callback)
Performs a SWQL query

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| query | <code>Object</code> | JSON Query object in form of {query:"<query>"} |
| callback | <code>function</code> | callback function on return |

**Example**  
```js
orion.query({query:"SELECT NodeID, URI from Orion.Nodes"}, 
     function (result){
         console.log(result);
     });

// Also with the parameter syntax:

orion.query({query:"SELECT NodeID, URI from Orion.Nodes WHERE NodeID = @id", param:{id:5}}, 
     function (result){
         console.log(result);
     }); 
```
<a name="update"></a>

## update(update, swisUri, callback)
Update Orion object

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| update | <code>Object</code> | JSON object of update |
| swisUri | <code>String</code> | the swis URI of the object to be updated |
| callback | <code>function</code> | callback function on return |

**Example**  
```js
orion.update({Caption:"new node caption"}, 
     "swis://hostname/Orion/Orion.Nodes/NodeID=1", 
     function (result){
         console.log(result);
     });
```
<a name="read"></a>

## read(swisUri, callback)
Read Orion object

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| swisUri | <code>String</code> | the swis URI of the object to be read |
| callback | <code>function</code> | callback function on return |

**Example**  
```js
orion.read("swis://hostname/Orion/Orion.Nodes/NodeID=1", 
     function (result){
         console.log(result);
     });
```
<a name="create"></a>

## create(data, object, callback)
Create Orion object

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| data | <code>Object</code> | JSON object of update |
| object | <code>String</code> | the object to be created |
| callback | <code>function</code> | callback function on return |

<a name="invoke"></a>

## invoke(verb, data, callback)
Performs an Orion verb invoke

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| verb | <code>String</code> | Verb to invoke, eg Orion.Nodes/Unmanage |
| data | <code>Array</code> | An array of the data to be passed to Verb |
| callback | <code>function</code> | callback function on return |

**Example**  
```js
var now = new Date();
var later = new Date();
later.setHours(later.getHours() + 3);

orion.invoke("Orion.Nodes/Unmanage", [ "N:1", now, later, false ], 
   function (result){
       console.log(result);
   });
```
<a name="remove"></a>

## remove(swisUri, callback)
remove Orion object

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| swisUri | <code>String</code> | the swisURI of the object to be removed |
| callback | <code>function</code> | callback function on return |

<a name="removeBulk"></a>

## removeBulk(swisUris, callback)
Bulk remove Orion objects

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| swisUris | <code>Array.&lt;String&gt;</code> | an array of swisUris representing objects to be deleted |
| callback | <code>function</code> | callback function on return |

<a name="getOptions"></a>

## getOptions() ⇒ <code>object</code>
Get options

**Kind**: global function  
**Returns**: <code>object</code> - options - currently set options  
<a name="setOptions"></a>

## setOptions(options)
Set options

**Kind**: global function  

| Param | Type | Description |
| --- | --- | --- |
| options | <code>object</code> | JSON object of options to set |

