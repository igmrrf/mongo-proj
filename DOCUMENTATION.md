Thank you for using Turbo! Full documentation:
https://docs.turbo360.co

Think of this file as quick-guide when you need to look something up or get stuck. Reading the entire page from top-to-bottom (though not a bad thing) is probably not necessary - just know that this file is here whenever you have questions.


- - - - - - - - - - - - - - - - - - SCAFFOLDING PROJECTS - - - - - - - - - - - - - - - - - - 

Turbo scaffolds projects in three ways:

VERTEX PROJECTS | $ turbo new <MY_PROJECT_NAME>
- After creating, cd into the project directory and run $ npm install
- Vertex projects are full stack apps that closely follow Node/Express architecture.

REACT/REDUX PROJECTS | $ turbo new <MY_PROJECT_NAME> --react
- After creating, cd into the project directory and run $ npm install
- This scaffolds a project with REACT/REDUX configured
- The REACT/REDUX source code is in the 'src' directory
- A webpack.config.js file is included with some basic webpack configuration. Feel free to adjust as needed.

- - - - - - - - - - - - - - - - - - GENERAL COMMANDS - - - - - - - - - - - - - - - - - - 

RUN DEV SERVER | $ turbo devserver
- This runs a simple Express server and renders the main index.html from http://localhost:3000
- We recommend running the dev server throughout development because it accurately reflects the behavior of your site in deployment.
- We also recommend running "gulp" in a separate tab. This invokes the build process whenever you make changes to JS or CSS files.
- The dev server supports relative links for anchor tags. For example, <a href="/blog">Blog</a> works fine with the dev server running.

BUILD THE PROJECT - ALL PROJECTS | $ npm run build
- This packages the project assets and concatenates/minifies the imports into the 'dist' directory.
** This command should be executed before every deployment because the 'dist' directory gets deployed, NOT the assets
- The gulpfile.js is where the configuration for the build process is defined. Register your custom assets here to include them in the build sequence.

LINK TO TURBO PROJECT - ALL PROJECTS | $ turbo app <APP_ID>
- This links your local project to the Turbo platform which is necessary for deployment
- To create a Turbo project, see here: https://docs.turbo360.co
- You can get the <APP_ID> from your app dashboard on turbo360.co

DEPLOY TO STAGING - ALL PROJECTS | $ turbo deploy
-- Deploys your site to the Turbo staging environment. The staging URL is accessible on the internet and can be viewed by anyone.
-- When deploying updates, it may take a minute or two for the changes to take effect as we propagate your site to multiple servers
** To deploy, your app must be linked to a  Turbo project. To create a Turbo project, see here: https://docs.turbo360.co
** It is best practice to run "$ npm run build" before deploying in order to package assets and minify imports.


- - - - - - - - - - - - - - - - FILE STORAGE - - - - - - - - - - - - - 

CDN: import <script src="https://cdn.turbo360-dev.com/dist/turbo.min.js" type="text/javascript"></script>
- Turbo({site_id:<MY_APP_ID>}).uploadFile(params)
	-> The 'params' argument requires 2 keys: 'apiKey' and 'completion'
	-> 'apiKey' is the API key for the current project on Turbo 360
	-> 'completion' is a function which takes 'err' and 'data' arguments. 'data' is returned from Turbo 360 upon successful file upload. 'err' is returned in error cases.
	-> The 'params' argument can take 2 more optional keys: 'onUploadStart' and 'onProgressUpdate'
	-> 'onUploadStart' is a function that is called when file begins uploading
	-> 'onProgressUpdate' is a function that is called continously as file uploads and takes a number argument between 0-100, e.g. "37.67389454804663"

- Turbo({site_id:<MY_APP_ID>}).getFiles(params, function(err, data){})
