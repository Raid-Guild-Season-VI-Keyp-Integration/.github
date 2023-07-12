# Project Overview

## Description

The goal of this project is to integrate keyp web3 authentication with Minetest, an open-source game, in order to enable web3 transactions within the game environment.

The project consists of four repositories that collectively facilitate this integration:

1. **Game Mod**: The game mod allows users to log in to keyp from within the game. Upon successful login, the user's public address is displayed in the top right corner of the game screen.

2. **UI**: The UI provides a user interface for choosing a login method (e.g., Twitter, Discord, Google). Once the user selects a login method, they are redirected to keyp for authentication. After successful authentication, a session token is generated and sent to the server for storage. The server responds with a secure 6-character authentication code that can be used to retrieve the session token.

3. **Express Server**: This server hosts the necessary endpoints for handling the authentication process. It provides two main endpoints:
   - Endpoint 1: Accepts a session token, stores it securely, and returns an authentication code.
   - Endpoint 2: Accepts an authentication code, verifies it, and returns the corresponding session token along with the user's public address.

## Testing the Integration

To test the end-to-end functionality, follow these steps:

1. Download Minetest from the official website (https://www.minetest.net/downloads/).
2. Open the Minetest client and click on "Join Game."
3. In the provided fields, enter the following details:
   - Address: minetest.saltyhash.xyz
   - Port: 30000
   - Choose any username.
4. Click on "Register" and create a password.

## Areas for Improvement

There are several areas that can be improved in this integration:

1. **Enhancing Security**: Implement additional security measures to ensure that only authorized individuals can access sensitive information. This may involve encryption, stronger authentication protocols, and secure storage of session tokens and authentication codes.

```
security for auth server:
1) add API key ( we only want the next front end and minetest server calling the auth-server. right now anyone could do that and spam 6 digit codes to get someones access token). we could just use the standard "Authorization" header for an api
2) time gate the codes (add a time stamp on creating the store and check if it's >10 mins old on the get api call)
3) make sure they're only used once (would be as simple as deleting the code and token from the store once redeemed)

```

2. **Server Optimization**: Test and improve the server's performance to handle increased traffic and scalability. This includes load testing, code optimization, and potentially utilizing caching mechanisms or distributed architectures.

3. **Expanded Transaction Support**: Extend the server's functionality to support additional types of transactions within the game. This could involve integrating with various web3 protocols and expanding the available transaction options for users.

4. **Deployment**: Create a docker compose yml that would spin up all 3 apps on a single VM so that someone could easily deploy their own version. but also there are many ways to deploy (terraform etc. ) so leaving it up to the admin makes sense too.

## Team Members

The following individuals contributed to the development of this project:

1. **Sero (Monk)**: Project Manager who oversaw the overall progress, managed communications between team members, created Github issues, wrote documentation, and ensured the project's direction and objectives were maintained.

2. **Luxumbra (Warrior) - Frontend**: Responsible for hosting the server, building the frontend UI, assisting with server development, and providing design expertise.

3. **SaltyHash (Paladin)**: Developed the game mod integration, contributed to server development, provided support to the team, and played a key role in defining the initial specifications and vision.

4. **XXavier_Dev (Paladin)**: Assisted with server development, coordinated efforts within the team, and integrated the keyp SDK.

Please note that the above information is based on the given details, and any additional specifics can be added to provide a more comprehensive overview of the project.
