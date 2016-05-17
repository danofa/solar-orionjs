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

orion.invoke();
orion.remove();
orion.removeBulk();
orion.update();
orion.create();

orion.getSettings();
orion.setSettings();
```