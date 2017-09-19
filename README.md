# Simple Data Pipe connector for Stack Overflow

:no_entry_sign: This project is no longer maintained

This connector uses the [Stack Exchange API](https://api.stackexchange.com/) to fetch the newest Stack Overflow questions for a selected tag.

The [Simple Data Pipe SDK](https://github.com/ibm-cds-labs/simple-data-pipe-sdk) is used to store the data in Cloudant. One JSON record is created for each question:
                                                                                          
##### Question record structure:
```json
{
  "..." : "<cloudant document properties such as _id and _rev>",
  "tags": [
    "javascript",
    "android",
    "indexeddb",
    "web-sql"
  ],
  "owner": {
    "reputation": 1,
    "user_id": 1234567,
    "user_type": "registered",
    "profile_image": "https://www.gravatar.com/avatar/1234567",
    "display_name": "user",
    "link": "http://stackoverflow.com/users/1234567/user"
  },
  "is_answered": false,
  "view_count": 10,
  "answer_count": 2,
  "score": 0,
  "last_activity_date": 1460144445,
  "creation_date": 1460138138,
  "question_id": 87653421,
  "link": "http://stackoverflow.com/questions/87653421/is-it-possible-to-perform-database-operation-on-locally-stored-db-through-javasc",
  "title": "Is it possible to perform database operation on locally stored DB through javascript (WebSQL or Indexeddb)",
  "body": "<p>i am developing offline web app for android platform and i want to use offline database for it. Is there any way to connect to locally stored database through javascript...",
  "pt_type": "android"
}
```

Need to load data from other sources? Check out the [connector repository](https://developer.ibm.com/clouddataservices/simple-data-pipe-connectors/).

### Pre-requisites

##### General 
 A valid Stack Exchange account is required to use this connector.

##### Deploy the Simple Data Pipe

 [Deploy the Simple Data Pipe in Bluemix](https://github.com/ibm-cds-labs/simple-data-pipe) using the Deploy to Bluemix button or manually. Take note of the application route (e.g. simple-data-pipe-stackoverflow.mybluemix.net)

##### Services

This connector does not require any additional Bluemix services.


##### Install the Simple Data Pipe connector for Stack Overflow

  When you [follow these steps to install this connector](https://github.com/ibm-cds-labs/simple-data-pipe/wiki/Installing-a-Simple-Data-Pipe-Connector), add the following line to the dependencies list in the `package.json` file: 

```
"simple-data-pipe-connector-stackoverflow": "git://github.com/ibm-cds-labs/simple-data-pipe-connector-stackoverflow.git",
```

##### Enable OAuth support and collect connectivity information

 You need to register the Simple Data Pipe application before you can use this connector to load data.
 
 * Go to the <a href="http://stackapps.com" target="_blank">Stack Apps home page</a> and log in.
  > If prompted, confirm that you want to create a new Stack Apps account. 

 * Find and click the **Register an application** link. 
 * In the form, set the _Application Name_ (ex. **Simple Data Pipe**).
 * Set the _Description_ (ex. **Simple Data Pipe Connector for Stack Overflow**).
 * Set the _OAuth Domain_ to **mybluemix.net** if running on Bluemix, or **127.0.0.1:8082** if running locally (change port if necessary).
 * Set the _Application Website_ to the Bluemix route for your Simple Data Pipe app (ex. **ht<span>tps://</span>simple-data-pipe-stackoverflow.mybluemix.net/**), or if running locally to **ht<span>tps://</span>127.0.0.1:8082/**. (change port and protocol if necessary):  
 * Click the **Register Your Application** button.
 * After you have registered your application take note of the _Client Id_, _Client Secret_, and _Key_ as you will use this information to configure your Stack Overflow data pipes.

### Using the Simple Data Pipe connector for Stack Overflow

To configure and run a pipe

1. Open the Simple Data Pipe web console.
2. Select __Create A New Pipe__.
3. Select __Stack Overflow__ for the __Type__ when creating a new pipe.
4. In the _Connect_ page, enter the _Client Id_, _Client Secret_, and _Key_ from your application on Stack Apps.
5. Select the data set to be loaded. Choose one of the most actively used tags or enter one or more comma separated custom tags.
6. Schedule or run the data pipe now.

#### License 

Copyright [2016] IBM Cloud Data Services

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
