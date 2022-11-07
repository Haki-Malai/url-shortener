# Url-shortener

## May not be working atm as the heroku free trial puts the server on idle mode

## [Try it out!](https://sleepy-bardeen-e624dd.netlify.app/)

### Powered By

#### Netlify, Heroku, Firebase, React & Node JavaScript and React-Bootstrap

# Code overview:
## Server
  - **[index.js](https://github.com/Haki-Malai/url-shortener/blob/main/server/index.js)** : routes the requests, uses the express library and listens to the heroku port.
  - **[routes](https://github.com/Haki-Malai/url-shortener/blob/main/server/routes)** : here lies the routing code provided to index.js
    - [urlRoutes.js](https://github.com/Haki-Malai/url-shortener/blob/main/server/routes/urlRoutes.js) : as the name suggests, routes the requests. A simple get on '/' returns {homepage : true} and it's basically useful only for testing/validation. Other get requests on '/:url' use the url to find the requested url for the redirection. In the **firebase** database there are ids with the urls. Basically the :url value is the id of the requested/shorted url encoded with the base62 encoding scheme. So all that is happening here is that the :url value is decoded and used as the id. A post request to /new with a given parameter adds a new url to the database and returns the "shorted" url. There is no regex to check for the url in the backend and it is advised to not test the security of the app yet! **(Please)**
    - [handler.js](https://github.com/Haki-Malai/url-shortener/blob/main/server/routes/handler.js) : handles the database fetching/writing.
    - [2***99.json](https://github.com/Haki-Malai/url-shortener/blob/main/server/routes/231299.json) : credentials and keys to use on firebase. As noted above, this is not a good practice and nor it is supposed to be one. Do **NOT** test for vulnerabilities!
 
## Frontend - React JS
  - **[/src/App.js](https://github.com/Haki-Malai/url-shortener/blob/main/reactjs/src/App.js)** : main renderer. Uses 2 state values. First one is 'status' which chooses what to display, either the input form, the error page or the success page. The other one is 'last' which is an object that has the values needed to display to the user. The App also renders a static label and footer.
  - **[/src/Components/input.js](https://github.com/Haki-Malai/url-shortener/blob/main/reactjs/src/Components/input.js)** : the input form used in the '../App.js'
  - **[/src/Components/error.js](https://github.com/Haki-Malai/url-shortener/blob/main/reactjs/src/Components/error.js)** : respectfully
  - **[/src/Components/success.js](https://github.com/Haki-Malai/url-shortener/blob/main/reactjs/src/Components/success.js)** : respectfully
