---
title: "tables"
---
##### Input

~~~text
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |
~~~

##### Output

~~~html

<table>
  <thead>
    <tr>
      <th>Tables</th>
      <th style="text-align: center">Are</th>
      <th style="text-align: right">Cool</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>col 3 is</td>
      <td style="text-align: center">right-aligned</td>
      <td style="text-align: right">$1600</td>
    </tr>
    <tr>
      <td>col 2 is</td>
      <td style="text-align: center">centered</td>
      <td style="text-align: right">$12</td>
    </tr>
    <tr>
      <td>zebra stripes</td>
      <td style="text-align: center">are neat</td>
      <td style="text-align: right">$1</td>
    </tr>
  </tbody>
</table>
~~~
