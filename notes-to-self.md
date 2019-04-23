# Discovery

[[toc]]

## Development environment & build tools

Local development environment:

* Windows 10 Pro & Windows Subsystem for Linux (WSL) Ubuntu
* Git-scm
* VS Code

Online build tools:

* Github
* Zeit now 2.0
* Circle CI

### Windows 10 Pro & Windows Subsystem for Linux (WSL)

#### Install Ubuntu (WSL)

* WIN-key search: "turn windows features on or off"
* Restart computer
* Open Windows store
* Search for and install Ubuntu
* Open Ubuntu

Update Ununtu:

* $ sudo apt-get update
* $ sudo apt-get upgrade

#### Visual Studio Code (VS Code)

Download: https://code.visualstudio.com/download
Install: VS Code

Open Ununtu terminal in VS Code:

* $ code .

Set WSL as default terminal:

* CTRL+Shift+p
* Terminal: Selecte default shell
* WSL Bash

_Source: https://dev.to/micahshute/setting-up-windows-subsytem-for-linux-3b7n_

#### NB. End of lines (EOL) in Windows vs. Linux

LF (Linux) vs. CRLF (Windows).

Add configuration of EOL in:

* Git-scm (during install).
* VSCode (File/Preferences/Settings -> Search EOL -> Setting \n) 

### Git-scm

* Download https://git-scm.com/download/win
* Install Git-scm

Follow installation instructions.

* Choose Linux line endings "\n".
* Log in to Github.

### Circle CI

* https://github.com/niccai/zeit-now-with-circleci

## Setup project boilerplate

### Navigation in Ubuntu on Windows 10.

Windows pathfinder cannot access Ubuntu root ({user}@{computer}:).
Ubunt CAN access Windows file-system.

Create project folder in windows file-system to access files from Ubuntu terminal in VS Code:

* Windows: c:\{path}\{project-folder}
* Ubuntu: {user}@{computer-name}:/mnt/c/{path}/{project-folder}

### Install Node.js, npm, express and Nodemon:

Terminal commands:
* $ mkdir "project-folder" && cd "project-folder"
* $ sudo apt-get install nodejs
* $ sudo apt-get install npm
* $ sudo npm init
* $ sudo apt install node-express-generator
* $ sudo npm install -g nodemon

Verify installation:

* $ node --version
* $ npm --version
* $ express --version
* $ nodemon --version

#### Nodemon

Nodemon reloads the http server when a file is served, avoiding numerous close serveren (CTRL+c) and start server iterations to see changes.

In package.json add

```json
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "node index",
    "dev": "nodemon"
  },
```

$ nodemon index

Sources:

* https://nodejs.org/en/docs/
* https://expressjs.com/en/starter/hello-world.html
* https://www.npmjs.com/package/nodemon

## Programming langauges and libraries

### Node.js

Simple example:
https://zeit.co/docs/v2/deployments/official-builders/node-js-now-node/
https://discovery.now.sh/?name=rolf

### Hello world node server in localhost

```javascript
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://$ {hostname}:$ {port}/`);
});

```

Start server: $ node app.js
Stop server: CTRL+c

Node.js courses:

* https://www.youtube.com/watch?v=fBNz5xF-Kx4

### Express

Netlify: https://blog.bitsrc.io/react-production-deployment-part-1-netlify-703686631dd1
Zeit now: https://blog.bitsrc.io/react-production-deployment-part-2-now-c81657c700b7

https://zeit.co/blog/serverless-express-js-lambdas-with-now-2

### React

https://zeit.co/guides/deploying-react-with-now-cra

https://medium.com/rambel/guide-to-a-simple-fullstack-semi-monolithic-stack-that-will-scale-b3c8b1aff591

### Integrating with an API backend

https://www.fullstackreact.com/articles/using-create-react-app-with-a-server/

_Kilde: https://facebook.github.io/create-react-app/docs/integrating-with-an-api-backend_

## Build tools and deploy pipeline

### Zeit now

Now 2.0 makes it possible to deploy new code that is committed to Github, by adding a now.json file to the Git repository.

* Log in to https://zeit.co/
* Open https://zeit.co/account
* Connect to Github
* Add now.js file in Github repository

Now.js example: 

```json
{
    "version": 2,
	"regions": ["bru"],
	"name": "discovery",
	"alias": "discovery",
    "public": false,
    "builds": [
        { "src": "*.js", "use": "@now/node" },
        { "src": "*.md", "use": "@now/md" }
    ],
    "routes": [
    { "src": "/(.*)", "dest": "/app.js" },
    { "src": "/about", "dest": "/readme.md" }
  	]
}
```

Commit an app to Github:
* https://github.com/{owner}/{repository}/

View project in Zeit now:

* https://{project-alias}.now.sh/

View Zeit Now project information:

* https://zeit.co/dashboard/project/{project-name}

Documentation: _https://zeit.co/docs/v2/integrations/now-for-github_

### Secret or private variables

* https://zeit.co/docs/api/v2/#endpoints/secrets
* https://zeit.co/docs/v2/deployments/environment-variables-and-secrets/
* https://zeit.co/docs/v2/deployments/environment-variables-and-secrets/#from-now.json

## Staging- and production environments

Now 2.0 handles environments in different ways.

Alias:

* https://zeit.co/docs/v2/integrations/now-for-github
* https://zeit.co/docs/v2/deployments/builds/
* https://zeit.co/docs/v2/deployments/configuration/#build.env
* https://zeit.co/docs/v2/domains-and-aliases/introduction/
* https://zeit.co/docs/v2/deployments/concepts/urls/
* https://zeit.co/docs/v2/deployments/configuration/

micro:

$  npm i micro-proxy

Sources: 

* _https://zeit.co/blog/micro-proxy_
* _https://github.com/zeit/micro_

## Online tutorials

https://github.com/rolfmadsen/opensearch/blob/gh-pages/index.html
https://discovery.now.sh/?name=readme
https://zeit.co/docs/v2/deployments/routes/
https://zeit.co/docs/v2/deployments/environment-variables-and-secrets
https://zeit.co/examples/nodejs-express/
https://zeit.co/guides/deploying-react-with-now-cra
https://blog.bitsrc.io/react-production-deployment-part-2-now-c81657c700b7

## Markdown syntax

https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet#code