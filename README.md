## Getting started

1. Clone this repository

2. Install al the project dependencies

```
npm install
```

3. Copy the new index.html file with some necesary imports

```
cp base/index-01.html public/index.html
```

## Getting started with Amplify

1. Go to your AWS console and create a new Amplify Backend Application

2. Open the AdminUI for that application

## Add authentication

1. In the admin UI add authentication with the default settings and deploy it.

2. After the application finish deploying. Go to your react application and do amplify pull as the instructions mentions.

3. Add authentication in your front end

```
cp base/App-01.css src/App.css
cp base/App-01.js src/App.js
```

4. Start the react app and see what happen. Create an account.

```
npm start
```

## Add GraphQL API

1. Go back to the AdminUI and in data, create a new model.

Make sure that you choose the cognito user pool (the authentication we just created) as authentication model for this API.

Model name: Note
Attributes:

- id
- note: string!

2. Deploy the API and after it finish deploying follow the instructions on amplify pull.

3. Add the API in your client

```
cp base/App-02.js src/App.js
```

4. Check the react app and see what happened. Add a note, delete it.

## Deploy this in the cloud

1. Create a new repository in github and put the react app in there.

NOTE: if you cloned this project make sure first to remove the origin so you can commit this code to a new place.

```
git remote remove origin
```

2. Go to the AWS Console and Amplify and add a new github project for the frontend.
   Note: Pick the existing backend enviroment or if you want to have multiple environments pick a new one.

3. Open the link and test the application that is in the cloud.

## Add ML capabilities

1. In the AdminUI, modify the data model and deploy it

Model: Note
Attributes:

- id
- note
- sentiment: String ---> NEW
- spanish: String ---> NEW

2. In the client pull the changes as the instructions mention

3. Add predictions Interpret --> TEXT

```
$ amplify add predictions
? Please select from one of the categories below Interpret
? What would you like to interpret? Interpret Text
? Provide a friendly name for your resource interpretTextXXX
? What kind of interpretation would you like? All
? Who should have access? Auth users only
Successfully added resource interpretTextXXX locally
```

4. Add predictions Convert --> Translate

```
$ amplify add predictions
? Please select from one of the categories below Convert
? What would you like to convert? Translate text into a different language
? Provide a friendly name for your resource translateTextfaXXX
? What is the source language? English
? What is the target language? Spanish
? Who should have access? Auth users only
Successfully added resource translateTextfaXXX locally
```

5. When that is complete do amplify push

```
amplify push
```

6. Then modify the client to see the new features in action:

```
cp base/App-03.js src/App.js
```

7. Commit all the new changes in github and see how the CICD pipeline in the Amplify app triggers.

8. Test it in the cloud.
