# SarabandaLatina

Web application to manage video courses of a cuban latin dance school.
It is written mostly in italian, is completely responsive and it uses:

- Front end: AngularJS, HTML, CSS
- Back end: PHP
- Database: MySQL

## File structure

- _root_
  HTML pages
- **ajax**
  PHP files, used as back end, these are the files called by JS to connect with the DB
- **config**
  Here are the files to configure the application
- **css**
  Only css files
- **file**
  In this folder there are files created by the application, uploaded by the administrator
- **img**
  All images, icons and logos of the site
- **js**
  Only javascript files
- **lib**
  All libraries used by the application

## Libraries

- **AngularJS**
  It is a JavaScript-based web framework for developing single-page applications.
- **AngularJS Material**
  It provides a set of reusable and accessible UI components for AngularJS
- **ngStorage**
  An AngularJS module that makes Web Storage working in the Angular Way

## Database

The database was designed for MySQL, it has these tables:

- **tabella_file**
  Table contains files uploaded by the administrator. It cointains only information, the real files are saved in the filesystem, into the folder _file_
- **utenti**
  All users registered on the web application

## Configuration

In the _config_ folder there are 2 files that are used to configure the application to connect correctly with the frontend, backend and DB

- **config.js**
  It is used to connect Javascript with PHP throw ajax calls. <br>
  It consider if the current url starts with http or https protocol, and if contains www or not, then add the backend address

  ```javascript
  var url_location = window.location;
  var http_https = "https://";
  var www = "";

  if (url_location.protocol) {
    http_https = url_location.protocol + "//";
  }

  if (url_location.host.startsWith("www.")) {
    www = "www.";
  }

  var url = http_https + www + "sarabandalatina.it/"; // edit this line: address url of the application
  ```

- **config.php**
  This file is inluded at the start of each php file. <br>
  It is used to configure general PHP settings and the connection with DB:

  - variables to connect to DB
  - connection to DB
  - start session

  ```php
  // connection data
  $server = "localhost";            // edit this line: server address
  $username = "sarabandalatina";    // edit this line: username
  $password = "sarabandalatina";    // edit this line: password
  $db = "sarabandalatina";          // edit this line: name of the database

  // start connection to DB
  try {
      $dbh = new PDO("mysql:host=$server;dbname=$db", $username, $password);
      $dbh->exec("set names utf8");
  }
  catch (PDOException $e) {
      echo "Connessione database fallita: " . $e->getMessage() . "\n";
      exit;
  }
  $dbh->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);

  // start session
  if (session_status() == PHP_SESSION_NONE) {
      session_start();
  }
  ```

## Screenshots

![sarabandalatina altervista org_](https://github.com/DavideMurro/SarabandaLatina/assets/118051417/fc6b408f-67af-45be-aded-ad61d354d073)
![sarabandalatina altervista org_home html](https://github.com/DavideMurro/SarabandaLatina/assets/118051417/6285ad6e-de5a-43bc-8c4a-a96f94ce1b1e)
![sarabandalatina altervista org_home(mobile) html](https://github.com/DavideMurro/SarabandaLatina/assets/118051417/c2a835a0-308b-446f-986e-79a4ced7b7ea)
