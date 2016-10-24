# react-intl-aggregate-flat-webpack-plugin

Small webpack plugin designed to take the output from `babel-plugin-react-intl` and aggregate it into one file.
An error will be thrown if there are messages in different components that use the same `id`.

It will output code that looks like:

```json
{
  "hello_world": "Bonjour Monde"
}
```

## Installation

```sh
$ npm install react-intl-aggregate-flat-webpack-plugin
```

## Usage

In your webpack config file:

```javascript
var ReactIntlAggregateFlatPlugin = require('react-intl-aggregate-flat-webpack-plugin');
var I18N_DIR                 = '../../i18n/';
...
var config = {
  ...
  plugins: [
    ...
    new ReactIntlAggregateFlatPlugin({
      messagesPattern: I18N_DIR + 'messages/**/*.json',
      aggregateOutputDir: I18N_DIR + 'aggregate/',
      aggregateFilename: 'en-US'
    })
  ]
}
...
module.exports = config;
```

## options

- **`aggregatePattern`**: The glob pattern used to retrieve the aggregate files for processing. Defaults to: `../../i18n/messages/**/*.json`.

- **`aggregateOutputDir`**: The target location where the plugin will output a `.json` file of the same basename corresponding to each aggregate file processed. Defaults to: `../../i18n/aggregate/`.

- **`aggregateFilename`**: The name of the file to be output that will get `.json` appended to it. Defaults to: `en-US`.

