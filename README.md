Udemy Nuxt course

#setup

1. to scaffold the app - npx nuxi create <appName>

2. open the app in vs code - code .

3. install the dependencies - npm i

4. run the app with - npm run dev

#course

1. File Based routing
   a. the starting point of the app is app.vue file
   b. to add route in the app create a folder in the base route names "pages"
   c. add a file called index.vue which is the base route
   d. now add <NuxtPage/> in the app.vue to render the pages based on the route
   e. we can also do dynamic routing using [] to take parameter
   f. we can also add optional route using [[]] to take optional parameter
   d. we can have multiple parameter in a single segment of the route using []and separated by special characters

2. components
   a. nuxt by default supports auto imports and based on the folder it will import the corresponding files
   b. you can add components to the app by adding a components folder in the route folder
   c. you can also use CLI to add component npx nuxi add component <componentName>
   d. if we a have a similar components in our app we can put those components in the same folder

3. NuxtLink
   a. we can navigate through pages using <NuxtLink to=""> instead of <a href=""> will not refresh the page
   b. we can also use <NuxtLink to="externalLink"> to navigate to a specific page
   c. Nuxt will load the link in nuxtLink when it is in viewport so the page will load even faster

4. NavigateTo() - will take you to the specified route

5. implementing nested pages
   a. we can have nested pages by adding nested folder in the corresponding folder and keeping a .vue file with the same name in the root
   b. we need to add <NuxtPage/> in the file where the route will be rendered nested inside the page

6. composables
   a. composables are places where we can store states or functionalities
   b. composables also supports auto import
   c. we can also use CLI to add composables npx nuxi add composable <composableName>

7. Default Composables
   a. useHead() - composable to set the name for the page and whatever we'll do in the header part of the HTML
   b. useRouter() - to access the url of the page
   c. useRoute() - to access the parameter from the route

8. Layouts
   a. when we want to render the same component in many places we can define it as a layout
   b. to add a layout we need to add a folder called layouts
   b. to define a default layout we need to name it as default.vue
   c. we need to define a slot component which will house all of the HTML
   d. we can also add custom layouts
   e. to override the default layout and to use the custom layout use definePageMeta()
   d. we can also use CLI to define layouts using npx nuxi add layout <layout name>

9. error handling
   a. there are two types of error handling - client side error handling - server side error handing
   b. client side error handling - we can define a page called error.vue in the route folder - so now whatever the error we might encounter from the client side it will land in this page
   c. useError() composable to get details about the error
   d. createError() to throw custom error
   e. clearError() - to clear the error and redirect the route
   c. client side error

   - error happening once all the hydrating and rendering are completed are client side error
   - client side error can be handled by <NuxtErrorBoundary>
   - whatever error happens this <nuxtErrorBoundary/> catches it and it doesn't renders the part where the error occurred
   - instead it will render the HTML error we have specified init
   - to specify the error message we can use <template #error="{error}"/> to read error - handling the error - resetting the same component to allow user to enter the correct input - strategic retreat - fatal error

10. Universal Rendering
    a. browser will get All the necessary HTML + CSS + JS from the server
    b. there are two types of rendering

    - server side rendering
      - client (browser) will request to server and server gives you everything needed to render the page
      - for every route there will be a request to server
      - initial page load will be faster since all the data are provided from the server but it will take time for other pages since there a individual call for every pages
      - good for SEO since the HTML template will be there
      - more expensive since data is processed in server and different req will be sent
    - client side rendering

      - here when the client request the server the server will provide you empty HTML and a Js bundle which can be parsed and rendered as a webpage
      - there will be no more request to server for different pages
      - initial page will take some time since the data need to be parsed in the browser but remaining pages will be loaded faster
      - bad SEO since we are getting only empty HTML
      - cheaper since there is no separate api calls every route

    - combined together we get universal rendering
      - will get the initial page first and the Js bundle will be send the in the background
      - Hydration - is the process of background parsing the webpage

11. passing dynamic values between components
    a. we can pass dynamic values between components using :key="value"
    b. to read the value passed use defineProps()
    and assign in to the variable in order to use the value inside the script tag we need to use variable.value to access the value but in side the HTML we can use it directly

12. modules in NUXT

    - nuxt provides some additional modules and can we used to enhance he performance fo the webpage
    - HTML img tag can be replaced by nuxtImg
    - once we install the package we need to update it in the nuxtConfig file

13. useState()

    - to maintain the state NUXT provides useState() composable
    - it is NUXT recommended way of creating a state
    - it is server side friendly
    - useState() takes two values uniqueKey , function returns the current state
    - but when the page is refreshed the state get reset

14. vueUse

- nuxt provides vueUse module which provides bunch of composables
- use access to browser things
- once we install the package we need to update it in the nuxtConfig file
- useLocalStorage takes a unique name and the initial state of the variable

15 emitting an event

- in order to communicate between the child to the parent we need to trigger an event
- we can make our app to only render in client side - wrapping with <clientOnly/> - or by suffixing with \*.client.vue
