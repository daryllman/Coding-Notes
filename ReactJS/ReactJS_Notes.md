# Installation & Set-Up

1. Install **create-react-app** dependency

   ```
   npm install -g create-react-app
   ```

   > -g is global flag that installs create-react-app globally, so you can use it anywhere

2. Run **create-react-app** to start your react project

   Go to the file directory where you want to start your project

   ```
   cd Desktop/
   ```

   Run **create-react-app**

   ```
   create-react-app react-sample-website-project
   ```

3. Start project

   ```
   npm start
   ```

   > this starts the local development server at localhost:3000     
   >
   > check if it is running fine    

4. You are ready to start working on your react project!





# Redux

Redux is a state management that can be used in any framework, but it works particularly well with React.     

### Why Redux?

1. Keeps States **Predictable**
2. Only serves as a **Storage** that is **Read-Only**
3. Can only use **Reducer** functions to edit the states
4. Access states anywhere in the app with **Inject**
5. 

> The way to manage states in small-scale apps are through **Component States**            
>
> However as apps become larger and more complex, it will be very complicated to manage states through components, and will introduce a lot of bugs that are difficult to debug      
>
> That is why **Redux** can be used.