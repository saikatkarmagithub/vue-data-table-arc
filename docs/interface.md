# Data Table

## Data

### Array Form

```html
<data-table :data="{ header, body }">
```

```js
header = ['name', 'age', 'job']
body = [
  ['debdut', 21, 'NA'],
  ['saikat', 20, 'NA'],
]
```
```ts
header: Array<String>
header: Array<Array>
data: { Array<String>, Array<String> }
```

| name   | age | job |
|--------|-----|-----|
| debdut | 21  | NA  |
| saikat | 20  | NA  |


### Object Form

```html
<data-table :data="data" :options="{ form: 'object' }">
```
```js
data = [
  {name: 'debdut', age: 21, job: 'NA'}
  {name: 'saikat', age: 20, job: 'NA'}
]
```


```ts
data: Array<Object>
```


| name   | age | job |
|--------|-----|-----|
| debdut | 21  | NA  |
| saikat | 20  | NA  |

## Options

```ts
options: {
  form: String
  edit: Boolean
  
  sort: Boolean
  compare: <T>(a : T, b : T) => T

  removeRow: Boolean
  removeColumn: Boolean
  addRow: Boolean
  addColumn: Boolean

  filter: Boolean
  filterStrategy: <T>(search: String, a : T, list: <T>) => Boolean

  tableStyle: String | Object
  tableClass: String
  headerStyle: String | Object
  headerClass: String

  column: Array<{
    edit: Boolean
  
    sort: Boolean
    compare: <T>(a: T, b: T) => T

    remove: Boolean
    textSize: Number
    type: String

    filter: Boolean
    filterStrategy: <T>(search: String, a : T, list: <T>) => Boolean

    colStyle: String | Object
    colClass: String
  }>

  row: Array<{
    edit: Boolean
    sort: Boolean
    remove: Boolean

    rowStyle: String | Object
    rowClass: String
  }>
}
```

### Table Options

| Option         | Type                | Default | Choices           | Description                                                                                                                                                                                                                                                           |
|----------------|---------------------|---------|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| form           | String              | 'array' | 'array'  'object' | Type of **data** prop passed in                                                                                                                                                                                                                                       |
| edit           | Boolean             | false   | false  true       | If True, the table cells are editable, on click turns the cell into a input with present value                                                                                                                                                                        |
| sort           | Boolean             | false   | false  true       | If True,all the table columns are sortable according to their values                                                                                                                                                                                                  |
| compare        | function            |         |                   | The columns are sortable according to their values using the provided compare algorithm                                                                                                                                                                               |
| removeRow      | Boolean             | false   | false   true      | If True,specific rows can be removed,and will not be shown anymore                                                                                                                                                                                                    |
| removeColumn   | Boolean             | false   | false  true       | If True,specific columns can be removed,and will not be shown anymore                                                                                                                                                                                                 |
| addRow         | Boolean             | false   | false  true       | If True,rows can be added,and will be shown along with the previous rows                                                                                                                                                                                              |
| addColumn      | Boolean             | false   | false  true       | If True,columns can be added,and will be shown along with the previous columns                                                                                                                                                                                        |
| filter         | Boolean             | false   | false  true       | If true, a row will be added in the top with input feilds of the same numbers as of the number of  cells in header.Each input feilds will take a value and will match it with all the values in the  column and will finally show the values or value that matches it |
| filterStrategy | function            |         |                   | Each input feilds will take a value and will be matched with the values in the column using the  specific strategy and will finally show the values or value that matches it                                                                                          |
| tableStyle     | String  Object(JSS) |         |                   | The passed css will be binded to the whole table itself                                                                                                                                                                                                               |
| tableClass     | String              |         |                   | The passed class will get binded to the whole table itself                                                                                                                                                                                                            |
| headerStyle    | String  Object(JSS) |         |                   | The passed css will be binded to the whole header itself                                                                                                                                                                                                              |
| headerClass    | String              |         |                   | The passed class will get binded to the whole header itself                                                                                                                                                                                                           |
### Column Options
