# React application using authentication with Keycloak

This project was bootstrapped with [Create React App](https://github.com/facebook/create-react-app).

## Installation

- run `npm install` to install dependecies

## Run

The application has just 2 URLs:

- public accessed page
- secured pages protected witjh Keycloak

### Keycloak setup

- Install Keycloak on Docker as described at [Keycloak installation](https://www.keycloak.org/getting-started/getting-started-docker) docs page.
- From a terminal start Keycloak with the following command:

```shell
docker run -p 8080:8080 -e KEYCLOAK_USER=admin -e KEYCLOAK_PASSWORD=admin quay.io/keycloak/keycloak:11.0.2
```

- go to the Keycloak Admin Console and login with the username and password you passed in earlier when starting the Keycloak as a Docker container (`admin/admin`).
- create `MyDemo` realm
- create a User `John` with password `john123`.
- create a Client `my-react-client`, choose `openid-connect` as Client Protocol and set the Root URL to `http://localhost:3000`
- select `Installation` tab in the client settings, select `Keycloak OIDC JSON` value as the Format Option. Copy the JSON content
- save the Client settings
- open `keycloak.json` file in the app and paste the JSON content copied previously from the Keycloak server Client's serttings.
- start the app with `npm start`
- you browser should open automatically at `localhost:3000` at the public accessed page
- click on the `secured` link of the page, - you should be redirected to the Keycloak login page
- log in ias `John` with the password you specified earlier (`john123`)
- you should see the content pf the secured page
- clicking the logout button forces you to have to log in again, the next time you try to access the Secured component.
