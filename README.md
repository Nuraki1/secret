                               OmishtuJoy Agetech Engineering MERN Stack class
                                             2024 GC
         

          REACT JS
          --------
 
ES6 Module:   (Before the React class)
----------



    some History Background:
    -----------------------
       Inline scripting: had a lot of problems in complex js code
       Script tags: 
       IIFA      (modular way)   
       common Js + Browserify 
       Webpack + ES6 : export and import
         
                    Material Links for Detail info : https://javascript.info/modules-intro









   Due to :- 
  - Slow development
  - hard to scale while in complex projects (hard to manage with team of developers), 
     Frameworks and libraries were invented by high tech companies

   React: 
        - Built by Facebook (FB, Instagram & Netflix)
        - can be used in mobile devices (native) and VR
     

     N.B
         - Components                : to write reusable, modular,and better organized code
         - one way Data flow
         - Virtual Dom
         - Eco-System (many tools works with React)

    

 
   prerequisites: Set Up development Environment

           - Node.js and npm:               - https://nodejs.org
           - Text Editor or IDE:            - vscode, atom, webstorm
           - Command Line Interface (CLI)   - terminal
           - Creating A React App           - Vite and CRA
                   

             1- Vite :
                  npm create vite@latest
                  npm i npm
                  npm run dev

             2- Create-React-App(CRA) - package contain webpack,babel(bablejs.io/repl) and others ready made config installed

                1. CRA 
               - npm install -g create-react-app (add 'sudo' at begining if there is an error)
               - create-react-app my-project     ( to create a project named my-project)
                N.B this above is outdated CRA

                2. CRA 2        upgraded version of CRA 
                  - just update the version in package.json file and run 'npm install' in the terminal   

                3. Latest version of CRA
                 - npx create-react-app my-project              (npx: package runner tool comes with npm 5.2+)
                 - cd my-project
                 - npm start
               
               


               folder structure  (CRA)
               ----------------

                  my-app/
                     README.md
                     node_modules/
                     package.json
                     public/
                        index.html         ...page template
                        favicon.ico
                     src/                  .. place for sub directories + CSS + Js files (Only Place where files R processed by WEBPACK)
                        App.css
                        App.js             ... App component
                        App.test.js
                        index.css
                        index.js          ... js entry point
                        logo.svg





               How Does React works
               --------------------


                index.html (page template)      index.js (javascript entry pt)                                     App.jsx (main component)
                ----------                      --------                                                            -------
                                                                                                                         |     <Other/>
                <div id="root"> </div>           ReactDOM.createRoot(document.getElementById('root')).render(            |         |
                           |                       <React.StrictMode>                            |                       |         |       
                           |                          <App />  _ _ _ _ _ _ _ _ _ _ _ _ _ _  _ _ _| _ _ _ _ _ _ _ _ _ _ _ |         |
                           |                       </React.StrictMode>,                          |                                 |
                           |                     )                                               |                                 | 
                           |_ _ _ _ _ _ _ _ _ _ _ _ _ _  _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ _ |                                 |
                                                                                                                                   |
    
                                                                                                                             Other components (Other.jsx)
                                                                                                                             ----------------

             * Class and Function Based Components
               -----------------------------------


                                       ----------- return tree of Elements (html)
             * JSX  (javascript XML)  |
               -------------------    |
                                       ----------- inject dynamic js (inside curly braces)
                                                  _ _ _ _ _ _ _|_ _ _ _ _ _ _                                                            
                                                 |                           |
                                   conditional render elements        render element from dynamic collection
                                                                              eg. an Array


              * Styling (CSS + Frameworks)
               ------------------------     
                  - style object    eg. <div style={{color:red}}><div/>   //the inner curly braces indicate it's an object
                  - className      // in JSX "class" is one of js reserved words
         

              * Images  (internal and external)
               -------------------------------       
                   2 ways -  import renamed path and use the renamed var as src value
                          -  direct write the path location of the src value

              


            
               Props : 
               -----  
                      - Properites of a components, which are used to pass a data from parent to child component
                      - Deterministic, unchangeable, results in pure components (dumb fun)
                      - props are never changing, inputs not modified

                   Check out: install React Developer Tool extension for your browser


         Example: practice this on some project
                   


               Click Events
               ------------
                   - use 'onClick' attribute

                   Example:

                     const someFunction = () => console.log('clicked by Akrem')
                       
                     <button onClick= {someFunction}> click Here <button/>
                                            |  
                                             -- must be referenced not invoked like 'someFunction()' X
                                            v
                       # if it has an argument, eg. name , inorder to get rid of invoking the function 
                         we will wrap the function inside onother anonymous funcion 

                         eg. const someFunction = (name) => console.log('clicked by' + name);

                         <button onClick = {()=>{
                           someFunction('Akrem');
                         }}> Click Me <button/>  


                State:
                -----
                      - An object Describing an app, 
                      - Reactive Variable 
                      - Able to change  
                      - React Can't re-render components with out the state

                   key words
                   ---------
                      # Components lifecycle
                      # Rerendering The component
                      # Side effects

                 We use Hooks to make things reactive in react     

      
      Hooks:  Special type of function
             - start with a name 'use' 
             - Hooks were introduced in React 16.8 as a way to use state and other React features in functional components.
               
            UseState: 
                   syntax -   
                      import {UseState} from 'react'
                       ... inside the component
                       const [var, setVar] = UseState('initial value');


               N.B. reactive variable + method to update it => Component that defined the reactive variable Re-rendered
                                                              ... every thing inside that component get re-rendered
                                       Virtual DOM's Efficiency:-       re-rendering != Updating of browser



          lifecycle: 

          # A component gets RENDERED by React in Memory can be: 

             - *MOUNTED     : into the DOM      created + 
             - *UPDATED     : inside the DOM
             - *UNMOUNTED   : (removed) from the DOM             


             UseEffect: to introduce side effects to the components beside Rendering of components
                          
                           -  for integration any thing outside of react
                                     eg. fetch data, 
                                         call an API, 
                                         collect info for analytics tools,
                                         start a timer

                   syntax: 
                   
                              UseEffect (
                                          ()=>{
                                          //f1             //side effect function eg. setInterval()
                                          return ()=>{
                                             //f2         //side effect clean up eg. clearInterval()
                                          }               // NOt usually, jsut for Async calls that run in the background
                                     })                       after removing from the DOM (Unmounting)


                                eg. UseEffect(()=>
                                      console.log('...') 
                                      ,[] )                 // Dependency Array empty: it will run the console log fun only once
                         

          lifecycle Hooks Example
          --------------------------

      Example: 

      import React, { useState, useEffect } from 'react';

      const MyComponent = () => {
      const [count, setCount] = useState(0);

      useEffect(() => {
            // This will run after the component is *mounted
            console.log('Component mounted');

            // This will run after every *update to the count state
            console.log('Count updated');
         }, [count]);

      useEffect(() => {
            return () => {
               // This will run when the component is *unmounted
               console.log('Component unmounted');
            };
         }, []);

         return (
            <div>
               <p>Count: {count}</p>
               <button onClick={() => setCount(count + 1)}>Increment</button>
            </div>
         );
         };

         export default MyComponent;


         Reference: https://www.linkedin.com/pulse/react-functional-component-lifecycle-manikandan-b
                    https://medium.com/@stheodorejohn/functional-components-vs-class-components-comparing-lifecycle-methods-in-react-218b59525414



   Folder structure
   ----------------
    


   Error Boundary
   -------------


  Deployment (for static website)
  ----------
    Github pages: 
    netlify
    firbase


  State management tools libraries
  ---------------------------------

    Redux ,reducers                 ... refer to the video lecture
  





                           -----------------------
                           ... To the Backend
                           -----------------------