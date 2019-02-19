
# Loopback Rest DataSource Example


This project contains the steps how to setup a loopback project which used Rest Datasource


## Prerequisite

  
```

node > 6

npm > 3

loopback cli

```

  

- First install Loopback CLI to create project:

```
npm install -g loopback-cli
```


- Create Project via loopback cli run the below command and answer the questions asked by cli [Documentation](https://loopback.io/doc/en/lb2/Create-a-simple-API.html)

```
lb loopback

Which version of LoopBack would you like to use?
select 3.x

What kind of application do you have in mind?
select notes

Switch to your project: cd <yourProject>

Run Project: node .
```

  

- Now create datasource via cli and answer the questions asked by cli to create datasource

  

```
create datasourc: lb datasource

? Enter the datasource name: geoDetails
? Select the connector for geoDetails: REST services (supported by StrongLoop)
? Base URL for the REST service:
? Default options for the request:
? An array of operation templates:
? Use default CRUD mapping: No
? Install loopback-connector-rest@^3.2.0 Yes

Now you datasource.json (./server/datasource.json) should look like this 

{
  "db": {
    "name": "db",
    "connector": "memory"
  },
  "geoDetails": {
    "name": "geoDetails",
    "baseURL": "",
    "crud": false,
    "connector": "rest"
  }
}

 
```

Now create your model and map it to your rest datasource

```

lb model


? Enter the model name: google-map
? Select the datasource to attach google-map to: geoDetails (rest)
? Select model's base class: Model
? Expose google-map via the REST API? Yes
? Custom plural form (used to build REST URL):
? Common model or server only? server
Let's add some google-map properties now.

Enter an empty property name when done.
? Property name:


```
  
- Map your modal to datasource (./server/model-config.json)

  

```

"google-map": {
    "dataSource": "geoDetails", // your datasource name (./server/datasources.json)
    "public": true
  }


```

- As our datasource is Google Map Rest API to use this we have to genrate a API_KEY in Google develope portal and export it as a env variable.

```
export API_KEY="<your api key>"


npm start or node .

```
