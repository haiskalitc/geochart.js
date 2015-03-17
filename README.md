# :chart_with_upwards_trend: geochart.js [![Built with Grunt](https://cdn.gruntjs.com/builtwith.png)](http://gruntjs.com/)

> A geo location based visualization chart application based on D3.js, TopoJSON and jQuery. It provides a simple interface for visualizing a dataset on a chloropleth world map.

## Getting Started
At the moment, it is not possible to check out this project as a bower project. Feel free to copy the files in the dist folder to your project and include it manually. The `geochart.js` library has some dependencies. It is necessary to include these dependencies before the `geochart.js` library. Take a look at the `bower.json` file to find out which libraries are necessary.

## Options
geochart.js expects a configuration object as an initial input. In the following section the mandatory and optional options are described in detail.

### options.map
Type: `String` or `Object`
Mandatory: :ballot_box_with_check:
Default value: `undefined`

The URL path to the json file containing the map data or the object itself. This option is necessary and can be provided as a link or a TopoJSON JavaScript object.

### options.data
Type: `String` or `Object`
Mandatory: :ballot_box_with_check:
Default value: `undefined`

The URL path to the data json or the object itself containing all the data which needs to be viualized on the map.

#### options.data.types
Type: `Array` of `Object`
Mandatory: :ballot_box_with_check:
Default value: `undefined`

An array of data types in which the values are grouped. Each data type holds a set of values which are displayed in separate maps. The data type can easily be switched in the slide menu or the overlayed select box. The structure of each object needs to correspond to the following structure:
```
{
  "type": "DATA_TYPE_KEY",
  "label": "Data Type"
}
```

#### options.data.selectedType
Type: `String`
Mandatory: :negative_squared_cross_mark:
Default value: the first defined data type

The key of the initially selected data type. If not specified, the first data type from the array of data types is taken.

#### options.data.countries
Type: `Object`
Mandatory: :ballot_box_with_check:
Default value: `undefined`

The object holding the data of each country, which needs to be visualized. The key of every country is the [ISO 3166-1 alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) country code, which is used to match the data with the actual map. Its structure is depicted in the following example:
```
options.data.countries = {
  "US": {
    "label": "United States",
    "continent": "North America",
    "values": {
      [...]
    }
  }
}
```
##### options.data.countries.label
Type: `String`
Mandatory: :ballot_box_with_check:
Default value: `undefined`

##### options.data.countries.continent
Type: `String`
Mandatory: :negative_squared_cross_mark:
Default value: `undefined`

##### options.data.countries.values
Type: `Object`
Mandatory: :negative_squared_cross_mark:
Default value: `undefined`

Lists all values for each data type of this specific country. If `values` is not provided, this specific country entry becomes obsolete and is not used inside the map. Not every listed country needs to provide a value for each data type. The structure of the object needs to be like in the following example:

```
options.data.countries.US.values = {
  "DATA_TYPE_KEY_1": 123,
  "DATA_TYPE_KEY_2": 456,
  [...]
}
```

#### options.data.notLocatable
Type: `Object`
Mandatory: :negative_squared_cross_mark:
Default value: `undefined`

Often there are datasets which can not be located to a single country but need to be declared anyway. This option adds the not locatable data sets to only the slide menu, not the map. The structure of the `Object` is equal to a [regular country entry](#optionsdatacountries) with exception of the continent, which can not be provided.

#### options.data.csv
Type: `String`
Mandatory: :negative_squared_cross_mark:
Default value: `undefined`

The URL path to the CSV file which holds the full dataset. If a link is provided, it will show a button in the slide menu leading to the provided link.

#### options.data.date
Type: `String` or `Object`
Mandatory: :negative_squared_cross_mark:
Default value: `undefined`

The date of the dataset, which is displayed on top of the slide menu. By default, the date needs to be given in the format YYYY-MM-DD. If the format needs to be passed too, the following schema can be used:
```
options.data.date = {
  "value": "01.01.2015",
  "format": "DD.MM.YYYY"
}
```
