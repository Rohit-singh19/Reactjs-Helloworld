# react.js hello world
first, you should install node and npm.

create directory
mkdir helloworld && cd helloworld

init npm
npm init

install webpack and webpack-dev-server
npm install webpack webpack-dev-server --save

install react and react-dom
npm install react react-dom --save

install babel etc.
npm install babel-core babel-loader babel-preset-react babel-preset-es2015 --save

add start scripts to package.json

    "scripts": {
      "test": "echo \"Error: no test specified\" && exit 1",
      "start": "webpack-dev-server --hot"
    }
touch webpack.config.js
    var config = {
      entry: './main.js',

      output: {
        path: './',
        filename: 'index.js'
      },

      devServer: {
        inline: true,
        port: 7777
      },

      module: {
        loaders: [
          {
            test: /\.jsx?$/,
            exclude: /node_modules/,
            loader: 'babel',
            query: {
              presets: ['es2015', 'react']
            }
          }
        ]
      }
    }

    module.exports = config;
touch index.html
    <!DOCTYPE html>
    <html>
      <head>
        <meta charset="utf-8">
        <title>react helloworld</title>
      </head>
      <body>
        <div id="app"></div>
        <script src="index.js" charset="utf-8"></script>
      </body>
    </html>
touch App.jsx
    import React from 'react';

    class App extends React.Component {
      render() {
        return (
          <div>simon, helloworld!!!</div>
        );
      }
    }

    export default App;
touch main.js
    import React from 'react';
    import ReactDOM from 'react-dom';

    import App from './App.jsx';

    ReactDOM.render(<App />, document.getElementById('app'));
start server
npm start

open browser: http://localhost:7777

if you clone this repository to local, just npm install and npm start.

