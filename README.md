# vue-editable-grid

## How to install

```
npm install vue-editable-grid
```

Then import in you main file

```js
import Vue from 'vue'

// Vue editable grid component and styles
import VueEditableGrid from 'vue-editable-grid'
import 'vue-editable-grid/dist/VueEditableGrid.css'

// register component in the Vue app
Vue.component('vue-editable-grid', VueEditableGrid)
```

Now you can use it
```html
<vue-editable-grid
  class="grid"
  :column-defs="columnDefs"
  :row-data="shipmentsFiltered"
  :displays='gridDisplays'
  @cell-updated="cellUpdated"
  @row-selected="rowSelected"
></vue-editable-grid>
```
Column definition format:
```js
const columnDefs = [
  { sortable: true, filter: true, field: 'shipmentId', headerName: 'Id' },
  { sortable: true, filter: true, field: 'datePublication', headerName: 'Date Publication', type: 'datetime', format: 'MMM dd, yyyy' },
  { sortable: true, filter: true, field: 'typeTruckDescription', headerName: 'Truck' },
  { sortable: true, filter: true, field: 'countryName', headerName: 'Cuty' },
  { sortable: true, filter: true, field: 'ammount', headerName: 'Ammount', type: 'currency' }
]
```

## Properties

```js
{
  columnDefs: { type: Array },
  rowData: { type: Array },
  pageCount: { type: Number, default: 0 },
  displays: { type: Array },
  itemHeight: { type: Number, default: 30 },
  virtualScrollOffset: { type: Number, default: 3 }
}
```

### columnDefs `(array)`
Define the column definition

### rowData `(array)`
Define the grid content data

### pageCount `(number)`
Define how many elements per page are showed. If pageCount is `0`, grid pagination is disabled.

Default value: `0`

### displays `(srray of string)`
Array of elements to show in grid top section like informative values.

### itemHeight `(number)`
Height of rows in pixels.

default value: `30`

### virtualScrollOffset `(number)`
How many elements (rows) are rendered outside grid visible scroll.

default value: `3`

## Column definition reference

### sortable
If column can be sort

Default: `false`

### filter
If column can be filter

Default: `false`

### field
Key name for column in `row-data` items

### headerName
Name for column header

### type
Data type, possible vales: `datetime`, `date`, `text`, `numeric`, `currency`, `boolean`.

Default: `text`

### format
Data column format, only apply for `date` and `datetime` column types.

Refer to [date-fns format table](https://date-fns.org/v2.14.0/docs/format) for more details.

### editable
Allow to edit column values.

Default: `false`

## Events

### cell-updated
Emited when cell value is changed.
TODO: ...

### row-selected
Emited when row selection is changed.

## Methods

You can access to VueEditableGrid instance using `ref` property.
```html
<vue-editable-grid
  ref="grid"
  ...
></vue-editable-grid>
```

In your component script
```js
export default {
  mounted () {
    const data = this.$refs.grid.getFormattedRows()
  },
  ...
}
```

### getFormattedRows()
Allow to get a complete row data passed in `row-data` property but with all format applied. This is very useful for example when you want to export the data.

## How to colaborate
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
