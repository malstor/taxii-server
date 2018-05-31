# node-taxii

This server implementation is a Node.js application based on the TAXII 2.0 RESTful API specification. TAXII is a protocol for the communication of cyber threat information. This server is read-only, with no user authentication, and is designed to allow access to the public collection of ATT&CK data. Unit tests are provided in the `test` directory, along with configuration files specific to the test environment. Further information on the TAXII 2.0 specification can be found [here](https://docs.google.com/document/d/1Jv9ICjUNZrOnwUXtenB1QcnBLO35RnjQcJLsa1mGSkI/edit#heading=h.4do73o99e2l7).

Collections may be defined per API root in `collections.json`. This serves as an access control mechanism, allowing users to request STIX data from enumerated collections only. API roots and the discovery endpoint may be defined in `config.json`, along with various other customizable options such as listening port, backend connection string, and bind address. API root metadata may be autogenerated or explicitly defined in `config.json`.

Clients may interact with the server like any other RESTful API, with exact HTTP verbiage and required header information described in the above specification.

## Installation

Clone the repository to your directory of choice, install dependencies using ``npm install``.

## Usage

`npm start`

## Testing

Testing requires the `mocha`, `chai` and `chai-http` npm packages.

- `npm test` - Runs tests inside of docker environment
- `npm test:local` - Runs tests on local host, assuming MongoDB is accessible


# Configuration

Configuration is done through a combination of the default configuration file, environmental variables, and command line arguments.

The configuration file should be the *last* place to change a configuration.  Command line arguments take precendence over environmental variables, which take precendence over the configuration file.

## Command Line Arguments

Warning: The following list may be out of date.  To see current command line arguments, run `npm run help`.

```
Options:
  --version                    Show version number                     [boolean]
  -h, --host                   Host name and/or IP address for MongoDB
  -p, --port                   Port for MongoDB
  -c, --certificate            Absolute path to certificate file for Mutual TLS
                               authentication (cert, key, and ca required for
                               mutual TLS)
  -k, --key                    Absolute path to key file for Mutual TLS
                               authentication (cert, key, and ca required for
                               mutual TLS)
  -a, --certificate-authority  Absolute path to certificate authority file for
                               Mutual TLS authentication (cert, key, and ca
                               required for mutual TLS)
  --help                       Show help                               [boolean]
  ```

## Environmental Variables

- `SERVER_CERTIFICATE` - Path to certificate file for mutual SSL authentication (key, cert, and ca is required for mutual SSL authentication)
- `SERVER_KEY` - Path to key file for mutual SSL authentication (key, cert, and ca is required for mutual SSL authentication)
- `SERVER_CA` - Path to ca file for mutual SSL authentication (key, cert, and ca is required for mutual SSL authentication)
- `MONGO_REPOSITORY` - Domain/IP for MongoDB
- `MONGO_PORT` - Port for MongoDB
