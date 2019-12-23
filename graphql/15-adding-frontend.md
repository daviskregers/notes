# Adding frontend

Currently we have made a server with a GraphQL endpoint. We are going to make a new React app that will use `Apollo` to query the graphql data.

```
➜  ~ cd projects/learning/graphql                                        
➜  graphql git:(master) sudo npm i create-react-app -g                                                                             
[sudo] password for davis:                                                                                                         
/usr/bin/create-react-app -> /usr/lib/node_modules/create-react-app/index.js                                                       
+ create-react-app@3.3.0                                                                                                           
added 91 packages from 45 contributors in 9.11s                                                                                    
➜  graphql git:(master) create-react-app client                                                                                    
                                                                                                                                   
Creating a new React app in /home/davis/projects/learning/graphql/client.                                                          
                                                                                                                                   
Installing packages. This might take a couple of minutes.                                                                          
Installing react, react-dom, and react-scripts with cra-template...                                                                
                                                                                                                                   
                                                                                                                                                                               
> core-js@2.6.11 postinstall /home/davis/projects/learning/graphql/client/node_modules/babel-runtime/node_modules/core-js          
> node -e "try{require('./postinstall')}catch(e){}"                                                                                
                                                                                                                                                                               
                                                                                                                                   
> core-js@3.6.0 postinstall /home/davis/projects/learning/graphql/client/node_modules/core-js                                                                                  
> node -e "try{require('./postinstall')}catch(e){}"                                                                                
                                                                                                                                                                               
                                
> core-js-pure@3.6.0 postinstall /home/davis/projects/learning/graphql/client/node_modules/core-js-pure                            
> node -e "try{require('./postinstall')}catch(e){}"              
                                                                                       
+ cra-template@1.0.0                                                                                                               
+ react-dom@16.12.0                                                                                                                
+ react@16.12.0                                                                                                                    
+ react-scripts@3.3.0                                                                                                              
added 1535 packages from 745 contributors and audited 906206 packages in 68.619s                                                   
                                                                                                                                   
32 packages are looking for funding                                                                                                
  run `npm fund` for details                                                           
                                                                                                                                   
found 0 vulnerabilities                                                                                                                                                                                                                                                
                                                                                                                                   
                                                                                                                                                                               
Installing template dependencies using npm...                                                                                                                                  
npm WARN tsutils@3.17.1 requires a peer of typescript@>=2.8.0 || >= 3.2.0-dev || >= 3.3.0-dev || >= 3.4.0-dev || >= 3.5.0-dev || >= 3.6.0-dev || >= 3.6.0-beta || >= 3.7.0-dev || >= 3.7.0-beta but none is installed. You must install peer dependencies yourself.
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.11 (node_modules/jest-haste-map/node_modules/fsevents):                                                           
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.11: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})             
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.11 (node_modules/chokidar/node_modules/fsevents):                                                                 
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.11: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})                                                                                                     
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.1.2 (node_modules/fsevents): 
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.2: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})                                                                                                      
                                                                                                                                   
+ @testing-library/react@9.4.0                                   
+ @testing-library/jest-dom@4.2.4  
+ @testing-library/user-event@7.2.1         
added 17 packages from 40 contributors and audited 906378 packages in 16.231s
                                                                 
32 packages are looking for funding                                                                                                                                            
  run `npm fund` for details                                                           

found 0 vulnerabilities                                                                                                                                                                                                                                                
                                                                                                                                   
Removing template package using npm...                                                                                                                                                                                                                                 
                                                                                                                                   
npm WARN tsutils@3.17.1 requires a peer of typescript@>=2.8.0 || >= 3.2.0-dev || >= 3.3.0-dev || >= 3.4.0-dev || >= 3.5.0-dev || >= 3.6.0-dev || >= 3.6.0-beta || >= 3.7.0-dev || >= 3.7.0-beta but none is installed. You must install peer dependencies yourself.    
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.11 (node_modules/jest-haste-map/node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.11: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})                                                                                                     
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@1.2.11 (node_modules/chokidar/node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@1.2.11: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})                                                                                                     
npm WARN optional SKIPPING OPTIONAL DEPENDENCY: fsevents@2.1.2 (node_modules/fsevents):
npm WARN notsup SKIPPING OPTIONAL DEPENDENCY: Unsupported platform for fsevents@2.1.2: wanted {"os":"darwin","arch":"any"} (current: {"os":"linux","arch":"x64"})                                                                                                      
                                                                 
removed 1 package and audited 906377 packages in 8.443s
                                                                 
32 packages are looking for funding
  run `npm fund` for details                                     
                                                                                                                                   
found 0 vulnerabilities                                          


Success! Created client at /home/davis/projects/learning/graphql/client
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

  cd client                                                      
  npm start                                                      

Happy hacking!                                                   
➜  graphql git:(master) ✗                                        
```

Now we can start the app

```
➜  graphql git:(master) ✗ cd client
➜  client git:(master) ✗ npm start
Compiled successfully!

You can now view client in the browser.

  Local:            http://localhost:3000/
  On Your Network:  http://192.168.1.171:3000/

Note that the development build is not optimized.
To create a production build, use npm run build.
```

Now we are going to clean up the project - delete the logo, test related files, app.css and modify the index.js:

```js
import React from 'react';
import ReactDOM from 'react-dom';
import './index.css';
import App from './App';

ReactDOM.render(<App />, document.getElementById('root'));
```

As well as app.js

```js
import React from 'react';
import BookList from './components/BookList'

function App() {
  return (
          <div id="main">
                <h1>Reading List</h1>
                <BookList />
          </div>
  );
}

export default App;
```

Now we are going to create a new file `src/components/BookList.js`.

```js
import React, { Component } from 'react';

class BookList extends Component {

        render() {
                return (
                        <div>
                                <ul id="book-list">
                                        <li>Item</li>
                                </ul>
                        </div>
                )
        }

}

export default BookList;
```