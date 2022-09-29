# iPear (fivem-resource)

This is an example made with **oxmysql** (**1.9.2**) and **ESX 1.2**.
If your server doesn't work with **oxmysql** and **ESX** then you need to adapt the resource.

## Dependencies
- OxMySQL (1.9.2) [[github]](https://github.com/overextended/oxmysql)
- ESX (1.2) [[github]](https://github.com/esx-framework)

## Project setup
```shell
npm install
```

### Compiles and minifies for production (nodejs v16)
```shell
npm run build
```

## Production (part 1 : prepare the files)
#### Build the current project:
```shell
npm run build
```
This will create a "**dist**" folder where all client and server files are generated and compiled.

#### Build the ingame-interface project with (after install):
```shell
npm run build
```
In this project also a "**dist**" folder will be created with _index.html_ and few _js/img/css files_.

We will use both folders in the next step.

## Production (part 2 : upload on your server)
* Create a resource "**ipear**" in your "**resources**" folder.
* Add **fxmanifest.lua** to the "**ipear**" folder.
* Create a folder "**html**" in the "**ipear**" folder.
* Drag and drop all **ingame-interface/dist** files built previously **inside the html** folder.
* Drag and drop all **fivem-resource/dist** files built previously **inside the ipear** folder.
* Open your **server.cfg** file:
  * Add both following lines at the top of file:
    * set ipear_secretkey "YOUR_SECRET_KEY"
    * set ipear_endpoint "YOUR_ENDPOINT"
  * Add the following line at the end of the file:
    * ensure **ipear**

## Production (part 3 : edit your mobile phone script)
Adapt your mobile phone to fit with iPear.
You can find an example in **gcphone/server.lua** (the changes are summarised in [this commit](https://github.com/iPearApp/Re-Ignited-Phone-with-iPear/commit/bebc5ab3871e1337970b405ba70a35e802b33578)).

* Every call of addContact function will trigger **ipear:contacts:add** event.
* Every call of updateContact function will trigger **ipear:contacts:update** event.
* Every call of deleteContact function will trigger **ipear:contacts:delete** event.
* Every call of addMessage function will trigger **ipear:messages:send** event.

If you use a vanilla version of Re-Ignited Phone (gcphone), you can replace your server.lua by the **gcphone/server.lua**.

## Production (part 4 : start your server)
Enjoy!
