##React.js Instructions

HTML templates will only ever read from `/static/js`. `/static/jsx` should only be used for developing the React files. [JSX](http://facebook.github.io/react/docs/jsx-in-depth.html) allows you to define views with HTML syntax right in your Javascript. They are not strings, but rather actual markup. After writing your .jsx file in the `/jsx`, you must compile it to Javascript.

###Compiling JSX to Javascript

`npm install -g react-tools` 
Note: React does not have any node dependencies of any kind. The compiler is just distributed via npm.

Then, `cd` into the `/static` directory and run:

`jsx -x jsx jsx js --no-cache-dir`

Explanation of command in order:

`-x jsx` specifies that the files to be compiled will have a `.jsx` extension

`jsx` the directory of all the JSX files (input) 

`js`  the directory of all the Js files (output)

`--no-cache-dir` the program uses some sort of cache optimization without this flag, but it also creates unnecessary files. 


## Instructions for getting set up (from scratch):

** Notes:**
 This is the CycleSafe_deploy project, found here: https://github.com/zemadi/CycleSafe_deploy (python/django)
 It is a reimplementation of this project: https://github.com/zemadi/CycleSafe (groovy/rails)

**Installing into a virtual evironment is highly recommended!**
NOTE: You will need to install MySQL for running in production mode.

1. install python 2.7
2. install pip (to get django)
3. > python get-pip.py
 
4. Install requirements.
 For development mode only: 
   > -pip install -r local_requirements.txt

 For production mode:
   > pip install -r prod_requirements.txt
  
  NOTE: If you have a problem with MySQl-Python in production, follow instructions here: http://stackoverflow.com/questions/25459386/mac-os-x-environmenterror-mysql-config-not-found

5. Get the secret key from someone already on the project. Add it as an environment variable. 
6. If you are using virtualenv, add the secret key to YOURENVIRONMENTNAME/bin/activate:
7. 
   > export SECRET_KEY='ADD_YOUR_SECRET_KEY_STRING_HERE'
7. Run Django's DB management tools: syncdb, schemamigration, and migrate. Read up on these if you don't know what they already are, THEN:
   > python manage.py syncdb

   > python manage.py schemamigration app --initial
   
   > python manage.py migrate app
   
   > python manage.py migrate tastypie
   
8. Run your local server
  > python manage.py runserver 0.0.0.0:8000 (or leave the IP address and port run on your localhost default)
 
To get your own DB set up, do the following:

For sqlite3:
 1. Create a new instance of sqlite3 in the project root, /CycleSafe_deploy
 2. Edit local_settings.py with your new DB info.
 3. Redo schemamigration and migrate in step 7.


For mysql:
 1. Create a new DB in MySQL.
 2. Add that info to local_settings.py or settings.py **(change settings.py only for production)** 
 3. Redo schemamigration and migrate in step 7.
  
Other links:

 Installers for various platforms (including Windows):
     http://www.enterprisedb.com/products-services-training/pgdownload#windows

 Windows: install Visual Studio 2008:
   http://download.microsoft.com/download/A/5/4/A54BADB6-9C3F-478D-8657-93B3FC9FE62D/vcsetup.exe
