# Valentines App

## Description
Valentine's Day Application is a simple web application developed in Svelte language using Vite. The application allows user interaction by clicking "Yes" or "No" buttons in the context of a Valentine's Day request. If the user clicks "Yes", they will be redirected to the /ok page, while if the user clicks "No", the text of the "No" caption will be changed and the "Yes" caption will be enlarged.



## Startup Instructions

1. **Installation of dependency**
    ```bash
    npm install
    ```
2. **Running the application**
    ```bash
    npm run dev
    ```
3. **Access to app**
    Open a browser and go to  `http://localhost:8000`



## Settings.json file

The settings.json file contains settings for the application, such as url addresses and messages for each page 



## Configuration
To customize your application, configure the `.env` file based on `.env.sample`.

Example of `.env` configuration

```dotenv
VITE_SECRET_KEY=YOUR_VITE_SECRET_KEY
VITE_TELEGRAM_BOT_TOKKEN=YOUR_VITE_TELEGRAM_BOT_TOKKEN
VITE_TELEGRAM_USER_ID=YOUR_VITE_TELEGRAM_USER_ID
VITE_ADMIN_TOKEN=YOUR_VITE_ADMIN_TOKEN
```


## Routing

1. **Homepage**
    'http://localhost:3000/'
2. **Admin Panel**
    'http://localhost:3000/admin'
3. **OK Page**
    'http://localhost:3000/ok'


## Telegram integration

The application integrates with Telegram to report the number of clicks on the "No" buttons. In the .env file, specify the Telegram bot token.



## Security

Links generated on the /admin site are encrypted using the AES symmetric encryption cryptographic function.

## Netlify APP
To show admin button add this phrase to url on main page
'?admin_token=ssVEAHG78Z58DC3Xwp0rfDHt3CV8jbzO'

Link:
https://valentines-app-svelte.netlify.app/?admin_token=ssVEAHG78Z58DC3Xwp0rfDHt3CV8jbzO