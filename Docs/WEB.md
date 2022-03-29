# Web Application Build and Firebase Deployment

<a href="#table-of-contents" style="width:100%"><img style="width:100%" src="https://gitlab.com/megabyte-labs/assets/-/raw/master/png/aqua-divider.png" /></a>

## Build and Deploy

Clone the repo:

```sh
git clone https://github.com/TelicSolutionsInc/AngularBoilerplate.git
```

Run npm install

```sh
npm install
```

### Build

Run ng build --prod

```sh
ng build --prod
```

After running the above command new directory (./dist) will be made in the root of the project.

### Firebase Setup

Create a new project on Firebase by clicking on Hosting section in Side Panel with any project name.

```sh
firebase login
```

Run ng firebase init and initialize the project after answering few questions:

```sh
firebase init
```

<ol>
  <li>Firebase CLI features…: Hosting.</li>
  <li>Public directory: Type in dist, because this is where your production-ready Angular app assets are.</li>
  <li>Configure as single-page app: Most of the time you’ll say yes (y) for this one.</li>
  <li>Overwrite index.html: No.</li>
  <li>Automatic builds: No.</li>
</ol>

Use this command to deploy your production-ready app to Firebase Hosting:

```sh
firebase deploy
```
