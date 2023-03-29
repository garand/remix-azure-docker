# Welcome to Remix!

This is a template for deploying a Remix app on Azure App Service using Docker with Azure Container Registry.

Required GitHub Secrets 

| Name                         | Sample Value                                                                                                        |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------- |
| REGISTRY_SERVER              | yourregistry.azurecr.io                                                                                             |
| REGISTRY_USERNAME            | yourregistry                                                                                                        |
| REGISTRY_PASSWORD            | REGISTRY_PASSWORD                                                                                                   |
| AZURE_WEBAPP_PUBLISH_PROFILE | https://learn.microsoft.com/en-us/visualstudio/azure/how-to-get-publish-profile-from-azure-app-service?view=vs-2022 |

(Note: These secrets should also be added into the application settings of app services using different key name as:DOCKER_REGISTRY_SERVER_URL, DOCKER_REGISTRY_SERVER_USERNAME & DOCKER_REGISTRY_SERVER_PASSWORD)

Things to update:

- [ ] Build image name (build-deploy.yml line 28)
- [ ] Publish image name (build-deploy.yml line 32)
- [ ] App name (build-deploy.yml line 37)

On any push to master, GitHub actions will build the Docker image, deploy it to Azure Container Registry, tagged with the short commit SHA, and publish that image to your Azure Web App.

- [Remix Docs](https://remix.run/docs)

## Development

From your terminal:

```sh
npm run dev
```

This starts your app in development mode, rebuilding assets on file changes.

## Deployment

First, build your app for production:

```sh
npm run build
```

Then run the app in production mode:

```sh
npm start
```

Now you'll need to pick a host to deploy it to.

### DIY

If you're familiar with deploying node applications, the built-in Remix app server is production-ready.

Make sure to deploy the output of `remix build`

- `build/`
- `public/build/`

### Using a Template

When you ran `npx create-remix@latest` there were a few choices for hosting. You can run that again to create a new project, then copy over your `app/` folder to the new project that's pre-configured for your target server.

```sh
cd ..
# create a new project, and pick a pre-configured host
npx create-remix@latest
cd my-new-remix-app
# remove the new project's app (not the old one!)
rm -rf app
# copy your app over
cp -R ../my-old-remix-app/app app
```
