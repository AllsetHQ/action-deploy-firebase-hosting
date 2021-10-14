# Allset deploy action for firebase hosted apps

## Prerequisites
1. Your project needs to define a `build:{environment}` script for each environment supported. Example: `build:edge`
2. A Firebase project alias should be present for each environment.
3. The Firebase hosting project should already be created.

## Usage
Adding the following to your workflow will build and deploy your web app to a given Firebase project.

```yaml
- uses: actions/checkout@v2
- name: Build and deploy
  uses: AllsetHQ/action-deploy-firebase-hosting@master
  with:
    environment: edge
    release_version: ${{ github.sha }}
    firebase_token: ${{ secrets.FIREBASE_CI_TOKEN }}
    firebase_project: allset-web-tipping-edge
```

### Inputs
#### Parameters
|name|description|required|default|
|---|---|---|---|
|`environment`| Set the environment for this release. E.g. "edge", "staging", or "production". |true|-|
|`release_version`| The version string to associate with this release. Useful for connecting instrumentation. |true|-|
|`firebase_project`| The name of the Firebase hosting project being deployed to. |true|-|
|`firebase_token`| The CI Token used to interact with Firebase. |true|-|
|`node_version`| The version of node to use for the build. |false|16.5.0|
