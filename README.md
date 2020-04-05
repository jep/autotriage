# AutoTriage - connect to critical patients faster

## About
During the initial spread of COVID-19 there was a substantial demand for testing. However, due to limited testing capacity the CDC advised only patients that had travel history involving specific countries, or presented a particular combination of symptoms, could receive a 'referral' to be tested. Patients who did not meet those parameters were considered 'stable' and told to self-isolate, get rest, and contact the doctor if symptoms progress or worsen. 

'AutoTriage' is web application that leverages the [Twilio Autopilot](https://www.twilio.com/docs/autopilot) API to screen human callers, using a list of doctor-configurable rules to determine which patients need to be connected to a medical professional and which patients are stable enough to exercise self-care.

This type of system is perfect for small medical practices who may not have the resources to field multiple calls from patients, or whose staff is required to work from home. During the current pandemic, many local governments set up telephone helplines where citizens could call and be connected to a qualified nurse to have their COVID-related questions answered. There were still large hold times on some of these lines, something that would be less likely to occur with an app like AutoTriage.

### How it works
The front-end is a simple web-app that allows

The application also provides a couple of endpoints to handle webhooks and return dynamic tasks for the IVR.

## Features

- Node.js web server using [Express.js](https://npm.im/express)
- User interface to setup IVR responses using [Twilio Helper Library](https://www.twilio.com/docs/libraries/node).
- Small JSON database using lowdb.
- ~~Unit tests using [`mocha`](https://npm.im/mocha) and [`chai`](https://npm.im/chai)
- ~~[Automated CI testing using GitHub Actions](/.github/workflows/nodejs.yml)
- ~~One click deploy buttons for Heroku, Glitch and now.sh

## Set up

### Requirements

- [Node.js](https://nodejs.org/)
- A Twilio account - [sign up](https://www.twilio.com/try-twilio)

### Twilio Account Settings

This application should give you a ready-made starting point for writing your
own IVR application using Autopilot. Before we begin, we need to collect
all the config values we need to run the application:

| Config&nbsp;Value | Description                                                                                                                                                  |
| :---------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Account&nbsp;Sid  | Your primary Twilio account identifier - find this [in the Console](https://www.twilio.com/console).                                                         |
| Auth&nbsp;Token   | Used to authenticate - [just like the above, you'll find this here](https://www.twilio.com/console).                                                         |
| Phone&nbsp;number | A Twilio phone number in [E.164 format](https://en.wikipedia.org/wiki/E.164) - you can [get one here](https://www.twilio.com/console/phone-numbers/incoming) |

### Local development

After the above requirements have been met:

1. Clone this repository and `cd` into it
    
    ```bash
    git clone git@github.com:twilio-labs/sample-autopilot-voice-ivr.git
    cd sample-autopilot-voice-ivr
    ```

1. Install dependencies
    
    ```bash
    npm install
    ```

1. Set your environment variables
    
    ```bash
    npm run setup
    ```
    
    See [Twilio Account Settings](#twilio-account-settings) to locate the necessary environment variables.

1. Run the application

    ```bash
    npm start
    ```
    
    Alternatively, you can use this command to start the server in development mode. It will reload whenever you change any files.
    
    ```bash
    npm run dev
    ```
    
    Your application is now accessible at [http://localhost:3000](http://localhost:3000/)

1. Make the application visible from the outside world.

    Your application needs to be accessible in a public internet address for Twilio to be able to connect with it. You can do that in different ways, [deploying the app to a public provider](#cloud-deployment) or using [ngrok](https://ngrok.com/) to create a tunnel to your local server.
    
    If you have ngrok installed to open a tunnel to you local server run the following command
    ```
    ngrok http 3000
    ```
    
    Now your application should be available in a url like:
    ```
    https://<unique_id>.ngrok.io/
    ```

1. Run the autopilot assistant setup

    The application provides a setup form that when submitted it will create or update the assistant and its tasks.
    Go to `/setup` in your application, update the configurable fields accordingly, and submit the form to set up the autopilot assistant.
  
    That's it! Now you can try the IVR calling your Twilio phone number.

### Tests

You can run the tests locally by typing:

```bash
npm test
```

### Cloud deployment

Additionally to trying out this application locally, you can deploy it to a variety of host services. Here is a small selection of them.

Please be aware that some of these might charge you for the usage or might make the source code for this application visible to the public. When in doubt research the respective hosting service first.

| Service                           |                                                                                                                                                                                                                           |
| :-------------------------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| [Heroku](https://www.heroku.com/) | [![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/twilio-labs/sample-autopilot-voice-ivr/tree/master)                                                                                                                                       |
| [Glitch](https://glitch.com)      | [![Remix on Glitch](https://cdn.glitch.com/2703baf2-b643-4da7-ab91-7ee2a2d00b5b%2Fremix-button.svg)](https://glitch.com/edit/#!/remix/clone-from-repo?REPO_URL=https://github.com/twilio-labs/sample-autopilot-voice-ivr.git) |
| [Zeit](https://zeit.co/)          | [![Deploy with ZEIT Now](https://zeit.co/button)](https://zeit.co/new/project?template=https://github.com/twilio-labs/sample-autopilot-voice-ivr/tree/master)                                                                 |


## Resources

- [Getting started with Twilio Autopilot (Video)](https://www.youtube.com/watch?v=edViFb-A0zw)
- [Autopilot Quickstart](https://www.twilio.com/docs/autopilot/quickstart)

## Contributing

This tutorial is open source and welcomes contributions. All contributions are subject to our [Code of Conduct](https://github.com/twilio-labs/.github/blob/master/CODE_OF_CONDUCT.md).

[Visit the project on GitHub](https://github.com/twilio-labs/sample-autopilot-voice-ivr)

## License

[MIT](http://www.opensource.org/licenses/mit-license.html)

## Disclaimer

No warranty expressed or implied. Software is as is.

[twilio]: https://www.twilio.com
