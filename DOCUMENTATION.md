# Structure ( Website all through JS) 
* It has two parts **client** and **server**. 
* Client is developed in **reactJS** and server is developed in **nodeJS** 
* All the files in root directory is of server. 
* To setup this far 
  1. Do "npm init " in root directory.
  1. Then make server in it.
  1. Do "create-react-app client" in it.
  
# Server

* Make following folder in it.
  * **models** (for storing mongoose entity structure | write model name in class notation 
    Ex: User , Video) 
  * **middleware** ( for storing custom middleware ) 
  * **router** (for storing files coresponding to each model , having all the routes realted to     that | wirte router name in small letters Ex: user , video)
  * **config** (for storing the configuration ) It contains following files
    * prod.js (config file for production environment)
    * dev.js (config file for development environment) 
    * key.js (file to decide which file to take MACROS from wheter prod.js or dev.js)
* Then make "index.js" in it.
* Some Prominent Modules used
  * **body-parser** : A middleware
    * body-parser.json() : It JSONify all the request coming from client.
    * body-parser.urlencoded() : It JSONify querystring data syntax.
  * **cookie-parser** : A middleware | cookie is present as a header in all request that is passed to         the server. | I used it to put token in user database as the user will log in and 
      then saving that token as cookie. Now whenever we shift to any page wheter login o       register etc we would first check whether any user is there it the database             having same same token as that saved in cookie. At the time of logout the token         field is made empty. 
   * **cors** : A mddleware | It stands for (CrOss-platform Resourse Sharing). \
      while sharing resourses bw client and server , automatically a flag in the header        in turned to false , donating resourse sharing is not allowed for security 
       purposes. To turn it on include it as a middleware. 
   * **jsonwebtoken** : JSON web token is used to give hash of JSON object or data which        can be accessed if you have the hash. (In project , used to generate token from           userid | not best usecase);
   * **bcrypt** : To encrypt the password before storing it in database and decrypt it          while accessing it again.
   * **nodemailer** : To send mails to specified email-address. 
   * **mongoose** : For mongodb database.
   * **express** : For making the server.
   
# Client
* It has following folders in it by default
  * **public** : It contain some basic html stuff | index.html | favicon.ico | manifest.json
  * **src** : It contains all the client side css and js stuffs.
* Make following folders in **src**.
  * **actions** : have file containing all the action that are being perfomed. ( We can say particular stuff action if it deals with communicating with server or something whose result is required by other components (redux)
  * **reducers** : have file containing all the stuff that need to be performed when particular action would be perfomed. ( It adds result of the action to the centralised redux-state store).
  * **components** : To put all your component. | It will also contain **App.js** (the root component) 
  * **assests** : To store all the assets
  * **hoc** : contains all the higher order components. | hoc components is a component that takes a component and returns a new component by adding some logic in that . Sometimes it may happen that same code is repeating in every component code so its better to include that in an hoc component and pass that earlier component from this hoc component every time your are using it. \ 
In this case we need to check with various components that is the user already signed in . If yes then dashboard need to be started, that's why we need auth hoc component.
  * Then **index.css** and **index.js** with other stuff is already present here.

* Some prominent modules used are 
  * **react** : For front-end
  * **react-dom** : For displaying App.js to index.html.
  * **react-redux** and **redux** : To implement centralized state structure.
  * **react-alert** : To give alerts (custom) rather than using window alert.
  * **react-router-dom** : To switch bw various components.
  * **react-google-login** , **react-facebook-login** : For google and facebook login.
  * **bootstrap** : To get bootstrap.css file (All the .css file should be included in index.js in client folder so that it gets reflected to all the components).
  * **react-bootstrap** : It offers custom made jsx component for react.
  * **antd** : It offers varing styling jsx components..
  * **formik** : Used for form validation.
  * **axios** : module offering easy way to communicate with the server . (of doing ajax);.
  * **react-icons** : for displaying icons. 

# Development phase
* "npm start" when done inside client folder run the front-end by automatically making a general server listening of "localhost:3000" 
* To asscociate client to your server we add **setupProxy.js** file in src in client directory add forward all the request to desired server.
* So Firstly we need to run client using "npm start" in client directory and then server using "nodemon index.js" in root directory. | Or we can use **concurrently** dev-tool to 
run them concurrently.

# Production phase
* Before deploying the web app firstly run "npm build" in client. It will convert all client materials into build folder inside client folder containing every stuffs in minimized format.
* now in index.js in root directory add some code to send "index.html" file in build folder when at first browser send the server get request. 
* before deploing you need to add some scripts in package.json under root folder, to send server the instruction of which file to run first and using which engine.

  
   
    
    
