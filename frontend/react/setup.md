# Setting up for React development

## 1. Install node.js

```
curl -sL https://deb.nodesource.com/setup_11.x | sudo -E bash -
sudo apt-get install -y nodejs
```

```
davis@davis-mint  /tmp  node -v
v11.3.0
```

```
davis@davis-mint  /tmp  npm -v
6.4.1
```

## 2. Create new React app

```
npx create-react-app react-app
```

```
✘ davis@davis-mint  ~/Sites  npx create-react-app react-app
npx: installed 63 in 1.511s

Creating a new React app in /home/davis/Sites/react-app.

Installing packages. This might take a couple of minutes.
Installing react, react-dom, and react-scripts...

+ react-scripts@2.1.1
+ react@16.6.3
+ react-dom@16.6.3
added 1701 packages from 661 contributors and audited 35639 packages in 95.539s
found 0 vulnerabilities


Initialized a git repository.

Success! Created react-app at /home/davis/Sites/react-app
Inside that directory, you can run several commands:

  npm start
    Starts the development server.

  npm run build
    Bundles the app into static files for production.

  npm test
    Starts the test runner.

  npm run eject
    Removes this tool and copies build dependencies, configuration files
    and scripts into the app directory. If you do this, you can’t go back!

We suggest that you begin by typing:

  cd react-app
  npm start

Happy hacking!

```

```
cd react-app
npm start
```