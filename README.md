# Auth0 Scripts

## Development

To get started run `npm install`

## Usage
In order to deploy all settings, themes and templates in 1 click, a short-lived authentication token must be requested in Auth0:

1. Request authentication token here: https://auth0.com/docs/secure/tokens/access-tokens/management-api-access-tokens  

2. Navigate to `environment` directory.  
   For a given environment, replace `auth0AuthToken` property value `<PASTE TOKEN HERE>` with a valid and not expired Auth0 authentication token.    
   To build templates run the npm build script for the appropriate env:

`npm run build:dev`  
`npm run build:qa`  
`npm run build:prod`

This will create output in the `dist/{env}` directory.

To deploy all generated settings, themes and templates run npm deploy script for the appropriate env:

`npm run deploy:dev`  
`npm run deploy:qa`  
`npm run deploy:prod`

More details on Auth0 APIs:

Update branding settings: https://auth0.com/docs/api/management/v2/branding/patch-branding  
Update branding theme: https://auth0.com/docs/api/management/v2/branding/patch-branding-theme  
Set template for new universal login experience: https://auth0.com/docs/api/management/v2/branding/put-universal-login  
Update prompts settings: https://auth0.com/docs/api/management/v2/prompts/patch-prompts  
Set custom text for a specific prompt: https://auth0.com/docs/api/management/v2/prompts/put-custom-text-by-language

Notes:  
All the changes that could be applied using this tool are mostly related to the look of the app.
Functional Auth0 tenant settings are not included in order to minimize potential override of manual changes made via Auth0 UI in the future.
Latter part of file names for prompts match Auth0's prompt names. For example: `prompt_login-id.json` corresponds to `login-id` prompt.  
Generated JSON files are used by shell script files which make curl requests to Auth0 API.  
Shebang is omitted from `.sh` files as the `deploy` script runs bash shell.  
URL query params for displaying a message above the widget cannot include some symbols, like "!" or ",": https://community.auth0.com/t/limit-of-ext-parameters-on-universal-login-page/111792/2  
Some custom messages are replaced within the script in the ul-template.
