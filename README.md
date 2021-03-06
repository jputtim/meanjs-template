# meanjs-template #

Template project for a [MEAN.JS](http://meanjs.org/) application

## Running the Project ##

To run the application, some initial setup required:

### Install Node ###

Since this is a [Node.js](http://nodejs.org/) project, please make sure
Node is installed on the machine. A recommended install method is to use
[nvm](https://github.com/creationix/nvm) which installs Node into your
home directory.

### Install Dependencies ###

Once Node is installed, from this project's root directory run the following
command to install the project dependencies:

`$ npm install`

This will install both the server side dependencies
(via [npm](https://www.npmjs.org/)) and client side dependencies
(via [bower](http://bower.io/)).

### Sass ###

This project uses [Sass](http://sass-lang.com/) as a CSS preprocessor. To
install Sass, you need Ruby installed. From there, to install Sass, run:

`$ gem install sass`

We also use a [Sass linter](https://github.com/causes/scss-lint). To
install `scss-lint` run the command:

`$ gem install scss-lint`

### MongoDB ###

This application requires a running instance of MongoDB. By default, the
application is configured to look for this running instance on the local
machine, but can be configured to point to a remote instance (see the
[configuration section](#configuration) for more information.)

If you need to install MongoDB, you can do so from the
[MongoDB downloads page](https://www.mongodb.org/downloads). For help
on the installation process and starting up MongoDB, please consult
the [installation instructions](http://docs.mongodb.org/manual/installation/).

### Start the App ###

This project is configured to load separate configuration based on the
environment where it is run (for example, `development` vs `production`).
The environment is specified via the `NODE_ENV` environment variable.
If no environment is specified, it will default to `development`.

To start the application (in development mode), execute the following command:

`$ NODE_ENV=development npm start`

The current available environments include:

*   `development`
*   `test`
*   `production`

#### Production ####

In production mode the application is setup to use minified assets
on the client side (along with template caching via Angular).
[Grunt](http://gruntjs.com/) is used to do this via the grunt `build`
task. To execute this task, run the following command:

`$ npm run build`

To start the server in the `production` environment, execute the following
command:

`$ npm run production`

### Configuration ###

Most all of the app's configuration is held within the `cofig/env/all.js` file.
Some of these values can be specified via environment variables. Below is a
list of those variables:

* Node Server
    * `PORT` : The port for the node application server, defaults to `3000` in all environments, except `test`, which defaults the port to `3001`
* Mongo
    * `MONGO_PROTOCOL` : The protocol for the mongodb connection, defaults to `mongodb://`
    * `MONGO_HOST` : Hostname for mongodb, defaults to `localhost`
    * `MONGO_PORT` : Port for mongodb, defaults to `27017`
    * `MONGO_DATABASE` : The database to use for mongodb, defaults to `meanjs-template`

## Tests ##

There are tests for both the server side code and the client side code.
The server side and client side unit tests are written using
[Jasmine](https://jasmine.github.io/), but the client side unit tests
run using [Karma](https://karma-runner.github.io). There are also
end to end tests for the client which use
[Protractor](http://angular.github.io/protractor).

### Setup ###

Project dependencies are required for tests as well, so please make
sure the [dependencies are installed](#install-dependencies).

### Run All Tests ###

To run all the tests, execute the following command:

`$ npm test`

[Grunt](http://gruntjs.com/) is used to bundle all the test execution
into one command. For more information on how this is done, please
see the `Gruntfile.js` file -- specifically the `test` task.

### Run Tests for Continuous Integration ###

In a continuous integration environment (such as Jenkins), the tests have been
configured to use only Firefox for a browser, and generate test reports in an
XML format that resembles JUnit. To run the tests in continuous integration mode,
execute the following:

`$ npm run ci`

For more information on running Firefox without a GUI, see: http://stackoverflow.com/a/16311264.

### Additional Test Run Actions ###

To run the server side tests in a "watch" mode (re-runs the tests after each change):

`$ npm run test-server-watch`

To run the client side karma unit tests in a "watch" mode:

`$ npm run test-client-watch`

To run the protractor tests:

`$ npm run protractor`
