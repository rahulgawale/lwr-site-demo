# LWC Boilerplate Example

The **LWC Boilerplate** example contains the minimum code needed to get a simple Single Page Application (SPA) on LWR running.

## Project Setup

The directory structure looks like this:

```
src/
  ├── assets/           // static assets
  │   └── recipes-logo.png
  |   └── favicon.ico
  └── modules/          // lwc modules
      └── example/
          └── app/
              ├── app.css
              ├── app.html
              └── app.js
lwr.config.json         // lwr configuration
package.json            // npm packaging configuration
```

## Configuration

The LWR server is configured in `lwr.config.json`, at the root of the project. The **LWC Boilerplate** example has one LWC module and one server-side route.

```json
// lwr.config.json
{
    "lwc": { "modules": [{ "dir": "$rootDir/src/modules" }, { "npm": "lightning-base-components" }] },
    "assets": [
        {
            "alias": "assetsDir",
            "dir": "$rootDir/src/assets",
            "urlPath": "/assets"
        },
        {
            "dir": "$rootDir/src/assets/fonts",
            "urlPath": "/fonts"
        },
        {
            "file": "$rootDir/src/assets/utilitySprite.svg",
            "urlPath": "/lightning.utilitySprite"
        },
        {
            "file": "$rootDir/src/assets/utilitySprite.svg",
            "urlPath": "/lightning.standardSprite"
        },
        {
            "alias": "favicon",
            "file": "$rootDir/src/assets/favicon.ico",
            "urlPath": "/favicon.ico"
        }
    ],
    "routes": [
        {
            "id": "my-app",
            "path": "/",
            "rootComponent": "example/app",
            "layoutTemplate": "$layoutsDir/main.html",
            "bootstrap": {
                "syntheticShadow": true
            }
        }
    ]
}

```

## Running the Project in dev Mode

```bash
yarn install
yarn build-slds # copy slds assets from node_modules to ./src/assets/
yarn dev # dev:compat for AMD format
```

Open the site at [http://localhost:3000](http://localhost:3000)

## Statically Generate and Preview the Site

```bash
yarn build # dev:prod-compat for AMD format
yarn start
```

Open the site at [http://localhost:3000](http://localhost:3000)
