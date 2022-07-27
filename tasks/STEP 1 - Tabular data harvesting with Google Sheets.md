# Step 1 - Tabular data harvesting with Google Sheets

## IMPORTHTML

In some cases, you may need to harvest only a small amount of tabular data from a web resource - this could be done using the built-in Google Sheets functionality.

As an example, let's take a look at the Demographics of the European Union Wikipedia page: https://en.wikipedia.org/wiki/Demographics_of_the_European_Union

The general formula to extract the data from the URL page to a Google Sheet is:

```
=IMPORTHTML(“URL”, “QUERY”, Index)
```

where **URL** is the URL of the page to examine, including protocol (e.g. http://), **QUERY** is either "table" or "list" depending on what type of structure contains the desired data, and **Index** is the index, starting at 1, which identifies which table or list as defined in the HTML source should be returned.

For example, to extract the data from the table on the Demographics of the European Union Wikipedia page, we can use the following formula:

```
=IMPORTHTML("https://en.wikipedia.org/wiki/Demographics_of_the_European_Union", "table", 2)
```

Which returns the following table as a result:

| Member State       | Population      | Percent of total EU-27 pop. | Total area km2 | Percent of total EU-27 area | Pop. densityPeople/km2 |
| ------------------ | --------------- | --------------------------- | -------------- | --------------------------- | ---------------------- |
| **European Union** | **447,007,596** | 100.00%                     | **4079962**    | 100.00%                     | **109.56**             |
| Austria            | 8,932,664       | 1.97%                       | 83858          | 1.98%                       | 106.52                 |
| Belgium            | 11,556,041      | 2.55%                       | 30510          | 0.72%                       | 378.76                 |
| Bulgaria           | 6,916,548       | 1.59%                       | 110912         | 2.62%                       | 62.36                  |
| Croatia            | 4,036,355       | 0.93%                       | 56594          | 1.34%                       | 71.32                  |
| Cyprus             | 854,802         | 0.19%                       | 9250           | 0.22%                       | 92.41                  |
| Czech Republic     | 10,701,777      | 2.37%                       | 78866          | 1.86%                       | 135.69                 |
| Denmark            | 5,840,045       | 1.29%                       | 43094          | 1.02%                       | 135.51                 |
| Estonia            | 1,330,068       | 0.30%                       | 45226          | 1.07%                       | 29.4                   |
| Finland            | 5,533,793       | 1.23%                       | 337030         | 7.96%                       | 16.41                  |
| France             | 67,439,599      | 15.03%                      | 643548         | 15.20%                      | 104.79                 |
| Germany            | 83,055,031      | 18.51%                      | 357021         | 8.43%                       | 232.63                 |
| Greece             | 10,682,547      | 2.42%                       | 131957         | 3.12%                       | 80.95                  |
| Hungary            | 9,730,772       | 2.20%                       | 93030          | 2.20%                       | 104.59                 |
| Ireland            | 5,006,907       | 1.10%                       | 70280          | 1.66%                       | 71.24                  |
| Italy              | 59,257,566      | 13.59%                      | 301320         | 7.12%                       | 196.65                 |
| Latvia             | 1,893,223       | 0.44%                       | 64589          | 1.53%                       | 29.31                  |
| Lithuania          | 2,795,680       | 0.64%                       | 65200          | 1.54%                       | 42.87                  |
| Luxembourg         | 634,730         | 0.13%                       | 2586           | 0.06%                       | 245.44                 |
| Malta              | 516,100         | 0.10%                       | 316            | 0.01%                       | 1633.22                |
| Netherlands        | 17,475,415      | 3.83%                       | 41526          | 0.98%                       | 420.83                 |
| Poland             | 37,840,001      | 8.52%                       | 312685         | 7.38%                       | 121.01                 |
| Portugal           | 10,298,252      | 2.31%                       | 92931          | 2.19%                       | 110.81                 |
| Romania            | 19,186,201      | 4.41%                       | 238391         | 5.63%                       | 80.48                  |
| Slovakia           | 5,459,781       | 1.22%                       | 48845          | 1.15%                       | 111.77                 |
| Slovenia           | 2,108,977       | 0.46%                       | 20253          | 0.48%                       | 104.13                 |
| Spain              | 47,394,223      | 10.44%                      | 504782         | 11.92%                      | 93.89                  |
| Sweden             | 10,379,295      | 2.24%                       | 449964         | 10.63%                      | 23.06                  |

Full **IMPORTHTML** documentation can be found [here](https://support.google.com/docs/answer/3093339?hl=en).

<br>

## Exercise

Find the table with the list of largest cities in the EU and construct a query to import it into a Google Sheet.

<br>

## Tip

If the page you are importing from has multiple tables, open your browser's Developer Tools and execute the following code:

```
var i = 1; [].forEach.call(document.getElementsByTagName("table"), function(x) { console.log(i++, x); });
```
