Universities & Colleges with Actuarial Programs (UCAP):
================

# Introduction:

In this project, web scraping was used to gather information about
universities around the world that offer bachelor’s, master’s, and PhD
programs in actuarial science. The data was collected from the Society
of Actuaries’ Listing of Universities and Colleges with Actuarial
Programs, but it should be noted that this project does not guarantee
the accuracy of the information. If you need a reliable list of
institutions, please visit the SOA’s website at
[**https://www.soa.org/institutions/**](https://www.soa.org/institutions/).

This project was completed as part of my research on master’s degree
programs in actuarial science in the United States and has been
recognized by the SOA.

## Library Used

Following are the list of package used for the purpose of this project.

- `dplyr` : For data manipulation

- `rvest` : For web scraping

- `tidyr` : For Data cleaning

- `stringr` : for manipulating string

- `janitor` : cleaning names

### Loading library

``` r
library(dplyr)
library(tidyr)
library(rvest)
library(janitor)
library(stringr)
library(gt)
```

## Web scraping

To extract table from webpage using `R`, we need `rvest` package.

First we need to install and lead the `rvest` package which i have
already done in previous section

Next, use the `read_html()` function to read the HTML content of the
webpage into R.

``` r
url <- "https://www.soa.org/institutions/"
html <- read_html(url)
```

After this , Use the `html_nodes()` function to find the table element
in the HTML.We can use `css` argument to specify a CSS selector that
matches the table elements

``` r
table <- html_nodes(html, css = "table")
```

At last , we use `html_table()` function to extract the table data from
the table element. This returns a list of data frames, one for each
table on the webpage. Since there is only one table, i have used `[[1]]`
to extract the first element of the list which is the data frame for the
table that we required

``` r
df <- html_table(table)[[1]]
```

## Data Cleaning

In r programming , we need to perform series of steps to fix or remove
any issues with the data such as errors, missing values or
inconsistencies.

Here are the problem that i obeserved and perform to clean a data frame:

### Standardize variable names and values

``` r
df <- df %>%
  janitor::clean_names()
pretty_table(df=head(df),title = "Sample 5")
```

<div id="iobrdvzgbn" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#iobrdvzgbn .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #FFFFFF;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#iobrdvzgbn .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#iobrdvzgbn .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#iobrdvzgbn .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#iobrdvzgbn .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 0;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#iobrdvzgbn .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#iobrdvzgbn .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#iobrdvzgbn .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#iobrdvzgbn .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#iobrdvzgbn .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#iobrdvzgbn .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#iobrdvzgbn .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#iobrdvzgbn .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}

#iobrdvzgbn .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #FFFFFF;
  vertical-align: middle;
}

#iobrdvzgbn .gt_from_md > :first-child {
  margin-top: 0;
}

#iobrdvzgbn .gt_from_md > :last-child {
  margin-bottom: 0;
}

#iobrdvzgbn .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#iobrdvzgbn .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: rgba(255, 255, 255, 0);
  padding-left: 5px;
  padding-right: 5px;
}

#iobrdvzgbn .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#iobrdvzgbn .gt_row_group_first td {
  border-top-width: 2px;
}

#iobrdvzgbn .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#iobrdvzgbn .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#iobrdvzgbn .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#iobrdvzgbn .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#iobrdvzgbn .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#iobrdvzgbn .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#iobrdvzgbn .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#iobrdvzgbn .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#iobrdvzgbn .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#iobrdvzgbn .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#iobrdvzgbn .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#iobrdvzgbn .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#iobrdvzgbn .gt_left {
  text-align: left;
}

#iobrdvzgbn .gt_center {
  text-align: center;
}

#iobrdvzgbn .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#iobrdvzgbn .gt_font_normal {
  font-weight: normal;
}

#iobrdvzgbn .gt_font_bold {
  font-weight: bold;
}

#iobrdvzgbn .gt_font_italic {
  font-style: italic;
}

#iobrdvzgbn .gt_super {
  font-size: 65%;
}

#iobrdvzgbn .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#iobrdvzgbn .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#iobrdvzgbn .gt_indent_1 {
  text-indent: 5px;
}

#iobrdvzgbn .gt_indent_2 {
  text-indent: 10px;
}

#iobrdvzgbn .gt_indent_3 {
  text-indent: 15px;
}

#iobrdvzgbn .gt_indent_4 {
  text-indent: 20px;
}

#iobrdvzgbn .gt_indent_5 {
  text-indent: 25px;
}
</style>
<table class="gt_table">
  <thead class="gt_header">
    <tr>
      <td colspan="5" class="gt_heading gt_title gt_font_normal gt_bottom_border" style>Sample 5</td>
    </tr>
    
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="name">name</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="level_of_actuarial_courses_offered">level_of_actuarial_courses_offered</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="soa_recognition_tier">soa_recognition_tier</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="state_province">state_province</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="country_territory">country_territory</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="name" class="gt_row gt_left">Abilene Christian University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Texas</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Acadia University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Nova Scotia</td>
<td headers="country_territory" class="gt_row gt_left">Canada</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Anahuac University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Huixquilucan</td>
<td headers="country_territory" class="gt_row gt_left">Mexico</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Anderson University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Indiana</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Appalachian State University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
<td headers="state_province" class="gt_row gt_left">North Carolina</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Arcadia University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
<td headers="state_province" class="gt_row gt_left">Pennsylvania</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="5"><em>Data from SOA website</em></td>
    </tr>
  </tfoot>
  
</table>
</div>

### Inconsistencies

``` r
df <- df %>%
  separate_rows(level_of_actuarial_courses_offered, sep = ",")
pretty_table(df = head(df),title = "Sample 5")
```

<div id="gwgobtxapg" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#gwgobtxapg .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #FFFFFF;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#gwgobtxapg .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#gwgobtxapg .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#gwgobtxapg .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#gwgobtxapg .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 0;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#gwgobtxapg .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#gwgobtxapg .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#gwgobtxapg .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#gwgobtxapg .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#gwgobtxapg .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#gwgobtxapg .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#gwgobtxapg .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#gwgobtxapg .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}

#gwgobtxapg .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #FFFFFF;
  vertical-align: middle;
}

#gwgobtxapg .gt_from_md > :first-child {
  margin-top: 0;
}

#gwgobtxapg .gt_from_md > :last-child {
  margin-bottom: 0;
}

#gwgobtxapg .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#gwgobtxapg .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: rgba(255, 255, 255, 0);
  padding-left: 5px;
  padding-right: 5px;
}

#gwgobtxapg .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#gwgobtxapg .gt_row_group_first td {
  border-top-width: 2px;
}

#gwgobtxapg .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#gwgobtxapg .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#gwgobtxapg .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#gwgobtxapg .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#gwgobtxapg .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#gwgobtxapg .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#gwgobtxapg .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#gwgobtxapg .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#gwgobtxapg .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#gwgobtxapg .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#gwgobtxapg .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#gwgobtxapg .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#gwgobtxapg .gt_left {
  text-align: left;
}

#gwgobtxapg .gt_center {
  text-align: center;
}

#gwgobtxapg .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#gwgobtxapg .gt_font_normal {
  font-weight: normal;
}

#gwgobtxapg .gt_font_bold {
  font-weight: bold;
}

#gwgobtxapg .gt_font_italic {
  font-style: italic;
}

#gwgobtxapg .gt_super {
  font-size: 65%;
}

#gwgobtxapg .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#gwgobtxapg .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#gwgobtxapg .gt_indent_1 {
  text-indent: 5px;
}

#gwgobtxapg .gt_indent_2 {
  text-indent: 10px;
}

#gwgobtxapg .gt_indent_3 {
  text-indent: 15px;
}

#gwgobtxapg .gt_indent_4 {
  text-indent: 20px;
}

#gwgobtxapg .gt_indent_5 {
  text-indent: 25px;
}
</style>
<table class="gt_table">
  <thead class="gt_header">
    <tr>
      <td colspan="5" class="gt_heading gt_title gt_font_normal gt_bottom_border" style>Sample 5</td>
    </tr>
    
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="name">name</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="level_of_actuarial_courses_offered">level_of_actuarial_courses_offered</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="soa_recognition_tier">soa_recognition_tier</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="state_province">state_province</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="country_territory">country_territory</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="name" class="gt_row gt_left">Abilene Christian University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Texas</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Acadia University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Nova Scotia</td>
<td headers="country_territory" class="gt_row gt_left">Canada</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Anahuac University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Huixquilucan</td>
<td headers="country_territory" class="gt_row gt_left">Mexico</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Anderson University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Indiana</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Appalachian State University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
<td headers="state_province" class="gt_row gt_left">North Carolina</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Arcadia University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
<td headers="state_province" class="gt_row gt_left">Pennsylvania</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="5"><em>Data from SOA website</em></td>
    </tr>
  </tfoot>
  
</table>
</div>

### Unnecessary white space

``` r
df <- df %>%
  mutate(country_territory = str_trim(country_territory),
         level_of_actuarial_courses_offered = str_trim(level_of_actuarial_courses_offered))
pretty_table(df=head(df),title = "Sample 5")
```

<div id="ctpcezkvke" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#ctpcezkvke .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #FFFFFF;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#ctpcezkvke .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ctpcezkvke .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#ctpcezkvke .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#ctpcezkvke .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 0;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#ctpcezkvke .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#ctpcezkvke .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#ctpcezkvke .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#ctpcezkvke .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#ctpcezkvke .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#ctpcezkvke .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#ctpcezkvke .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#ctpcezkvke .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}

#ctpcezkvke .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #FFFFFF;
  vertical-align: middle;
}

#ctpcezkvke .gt_from_md > :first-child {
  margin-top: 0;
}

#ctpcezkvke .gt_from_md > :last-child {
  margin-bottom: 0;
}

#ctpcezkvke .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#ctpcezkvke .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: rgba(255, 255, 255, 0);
  padding-left: 5px;
  padding-right: 5px;
}

#ctpcezkvke .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#ctpcezkvke .gt_row_group_first td {
  border-top-width: 2px;
}

#ctpcezkvke .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ctpcezkvke .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#ctpcezkvke .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#ctpcezkvke .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#ctpcezkvke .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#ctpcezkvke .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#ctpcezkvke .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#ctpcezkvke .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#ctpcezkvke .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ctpcezkvke .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#ctpcezkvke .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#ctpcezkvke .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#ctpcezkvke .gt_left {
  text-align: left;
}

#ctpcezkvke .gt_center {
  text-align: center;
}

#ctpcezkvke .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#ctpcezkvke .gt_font_normal {
  font-weight: normal;
}

#ctpcezkvke .gt_font_bold {
  font-weight: bold;
}

#ctpcezkvke .gt_font_italic {
  font-style: italic;
}

#ctpcezkvke .gt_super {
  font-size: 65%;
}

#ctpcezkvke .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#ctpcezkvke .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#ctpcezkvke .gt_indent_1 {
  text-indent: 5px;
}

#ctpcezkvke .gt_indent_2 {
  text-indent: 10px;
}

#ctpcezkvke .gt_indent_3 {
  text-indent: 15px;
}

#ctpcezkvke .gt_indent_4 {
  text-indent: 20px;
}

#ctpcezkvke .gt_indent_5 {
  text-indent: 25px;
}
</style>
<table class="gt_table">
  <thead class="gt_header">
    <tr>
      <td colspan="5" class="gt_heading gt_title gt_font_normal gt_bottom_border" style>Sample 5</td>
    </tr>
    
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="name">name</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="level_of_actuarial_courses_offered">level_of_actuarial_courses_offered</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="soa_recognition_tier">soa_recognition_tier</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="state_province">state_province</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="country_territory">country_territory</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="name" class="gt_row gt_left">Abilene Christian University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Texas</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Acadia University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Nova Scotia</td>
<td headers="country_territory" class="gt_row gt_left">Canada</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Anahuac University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Huixquilucan</td>
<td headers="country_territory" class="gt_row gt_left">Mexico</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Anderson University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Indiana</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Appalachian State University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
<td headers="state_province" class="gt_row gt_left">North Carolina</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Arcadia University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
<td headers="state_province" class="gt_row gt_left">Pennsylvania</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="5"><em>Data from SOA website</em></td>
    </tr>
  </tfoot>
  
</table>
</div>

### Data Exploration

The purpose of this project is to find list of US Universities offering
Masters program in actuarial science and are in list of recognized
university of SOA

for this we need to perform the following task in R:

``` r
df1 <- df %>%
  filter(level_of_actuarial_courses_offered == "Masters" & country_territory =="United States")

pretty_table(head(df),"sample 5")
```

<div id="nashfbxqru" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#nashfbxqru .gt_table {
  display: table;
  border-collapse: collapse;
  margin-left: auto;
  margin-right: auto;
  color: #333333;
  font-size: 16px;
  font-weight: normal;
  font-style: normal;
  background-color: #FFFFFF;
  width: auto;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #FFFFFF;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
}

#nashfbxqru .gt_heading {
  background-color: #FFFFFF;
  text-align: center;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#nashfbxqru .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#nashfbxqru .gt_title {
  color: #333333;
  font-size: 125%;
  font-weight: initial;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-color: #FFFFFF;
  border-bottom-width: 0;
}

#nashfbxqru .gt_subtitle {
  color: #333333;
  font-size: 85%;
  font-weight: initial;
  padding-top: 0;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-color: #FFFFFF;
  border-top-width: 0;
}

#nashfbxqru .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#nashfbxqru .gt_col_headings {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
}

#nashfbxqru .gt_col_heading {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 6px;
  padding-left: 5px;
  padding-right: 5px;
  overflow-x: hidden;
}

#nashfbxqru .gt_column_spanner_outer {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: normal;
  text-transform: inherit;
  padding-top: 0;
  padding-bottom: 0;
  padding-left: 4px;
  padding-right: 4px;
}

#nashfbxqru .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#nashfbxqru .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#nashfbxqru .gt_column_spanner {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
  vertical-align: bottom;
  padding-top: 5px;
  padding-bottom: 5px;
  overflow-x: hidden;
  display: inline-block;
  width: 100%;
}

#nashfbxqru .gt_group_heading {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  text-align: left;
}

#nashfbxqru .gt_empty_group_heading {
  padding: 0.5px;
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #000000;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #FFFFFF;
  vertical-align: middle;
}

#nashfbxqru .gt_from_md > :first-child {
  margin-top: 0;
}

#nashfbxqru .gt_from_md > :last-child {
  margin-bottom: 0;
}

#nashfbxqru .gt_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  margin: 10px;
  border-top-style: solid;
  border-top-width: 1px;
  border-top-color: #FFFFFF;
  border-left-style: none;
  border-left-width: 1px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 1px;
  border-right-color: #D3D3D3;
  vertical-align: middle;
  overflow-x: hidden;
}

#nashfbxqru .gt_stub {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: rgba(255, 255, 255, 0);
  padding-left: 5px;
  padding-right: 5px;
}

#nashfbxqru .gt_stub_row_group {
  color: #333333;
  background-color: #FFFFFF;
  font-size: 100%;
  font-weight: initial;
  text-transform: inherit;
  border-right-style: solid;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
  padding-left: 5px;
  padding-right: 5px;
  vertical-align: top;
}

#nashfbxqru .gt_row_group_first td {
  border-top-width: 2px;
}

#nashfbxqru .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#nashfbxqru .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#nashfbxqru .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#nashfbxqru .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#nashfbxqru .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#nashfbxqru .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#nashfbxqru .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#nashfbxqru .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#nashfbxqru .gt_footnotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#nashfbxqru .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#nashfbxqru .gt_sourcenotes {
  color: #333333;
  background-color: #FFFFFF;
  border-bottom-style: none;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
  border-left-style: none;
  border-left-width: 2px;
  border-left-color: #D3D3D3;
  border-right-style: none;
  border-right-width: 2px;
  border-right-color: #D3D3D3;
}

#nashfbxqru .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#nashfbxqru .gt_left {
  text-align: left;
}

#nashfbxqru .gt_center {
  text-align: center;
}

#nashfbxqru .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#nashfbxqru .gt_font_normal {
  font-weight: normal;
}

#nashfbxqru .gt_font_bold {
  font-weight: bold;
}

#nashfbxqru .gt_font_italic {
  font-style: italic;
}

#nashfbxqru .gt_super {
  font-size: 65%;
}

#nashfbxqru .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#nashfbxqru .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#nashfbxqru .gt_indent_1 {
  text-indent: 5px;
}

#nashfbxqru .gt_indent_2 {
  text-indent: 10px;
}

#nashfbxqru .gt_indent_3 {
  text-indent: 15px;
}

#nashfbxqru .gt_indent_4 {
  text-indent: 20px;
}

#nashfbxqru .gt_indent_5 {
  text-indent: 25px;
}
</style>
<table class="gt_table">
  <thead class="gt_header">
    <tr>
      <td colspan="5" class="gt_heading gt_title gt_font_normal gt_bottom_border" style>sample 5</td>
    </tr>
    
  </thead>
  <thead class="gt_col_headings">
    <tr>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="name">name</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="level_of_actuarial_courses_offered">level_of_actuarial_courses_offered</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="soa_recognition_tier">soa_recognition_tier</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="state_province">state_province</th>
      <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="country_territory">country_territory</th>
    </tr>
  </thead>
  <tbody class="gt_table_body">
    <tr><td headers="name" class="gt_row gt_left">Abilene Christian University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Texas</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Acadia University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Nova Scotia</td>
<td headers="country_territory" class="gt_row gt_left">Canada</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Anahuac University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Huixquilucan</td>
<td headers="country_territory" class="gt_row gt_left">Mexico</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Anderson University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
<td headers="state_province" class="gt_row gt_left">Indiana</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Appalachian State University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
<td headers="state_province" class="gt_row gt_left">North Carolina</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    <tr><td headers="name" class="gt_row gt_left">Arcadia University</td>
<td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Bachelors</td>
<td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
<td headers="state_province" class="gt_row gt_left">Pennsylvania</td>
<td headers="country_territory" class="gt_row gt_left">United States</td></tr>
  </tbody>
  <tfoot class="gt_sourcenotes">
    <tr>
      <td class="gt_sourcenote" colspan="5"><em>Data from SOA website</em></td>
    </tr>
  </tfoot>
  
</table>
</div>

### Getting University list based on SOA recognition tier

The UCAP list includes universities and colleges that have met certain
eligibility requirements for recognition as Centers of Actuarial
Excellence (CAEs), or as having Introductory Curriculum (UCAP-IC) or
Advanced Curriculum (UCAP-AC) status. To be recognized as a CAE, a
university must meet eight specific requirements related to its degree
programs, curriculum, faculty composition, graduate quality, and other
factors. Universities with UCAP-IC status must offer course coverage for
at least two SOA preliminary exams and have approved courses for at
least one Validation by Educational Experience (VEE) topic area.
Universities with UCAP-AC status must offer course coverage for at least
four SOA preliminary exams, including Exam LTAM or Exam STAM, and
approved courses for all VEE topic areas. The UCAP program also includes
a University-Earned Credit (UEC) program, which allows university
students to become eligible for SOA exam credit by attaining a
designated UEC mark on university courses at approved CAEs.

So lets get list for each tier

- `CAE with UEC` : University-Earned Credit Status:

  ``` r
  uec <- df1 %>%
    filter(soa_recognition_tier == "CAE/UEC")
  pretty_table(df=uec,title = "List of University in CAE with UEC tier")
  ```

  <div id="uwirfnoeus" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
  <style>html {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
  }

  #uwirfnoeus .gt_table {
    display: table;
    border-collapse: collapse;
    margin-left: auto;
    margin-right: auto;
    color: #333333;
    font-size: 16px;
    font-weight: normal;
    font-style: normal;
    background-color: #FFFFFF;
    width: auto;
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #FFFFFF;
    border-right-style: none;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 2px;
    border-left-color: #D3D3D3;
  }

  #uwirfnoeus .gt_heading {
    background-color: #FFFFFF;
    text-align: center;
    border-bottom-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
  }

  #uwirfnoeus .gt_caption {
    padding-top: 4px;
    padding-bottom: 4px;
  }

  #uwirfnoeus .gt_title {
    color: #333333;
    font-size: 125%;
    font-weight: initial;
    padding-top: 4px;
    padding-bottom: 4px;
    padding-left: 5px;
    padding-right: 5px;
    border-bottom-color: #FFFFFF;
    border-bottom-width: 0;
  }

  #uwirfnoeus .gt_subtitle {
    color: #333333;
    font-size: 85%;
    font-weight: initial;
    padding-top: 0;
    padding-bottom: 6px;
    padding-left: 5px;
    padding-right: 5px;
    border-top-color: #FFFFFF;
    border-top-width: 0;
  }

  #uwirfnoeus .gt_bottom_border {
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #uwirfnoeus .gt_col_headings {
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #000000;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
  }

  #uwirfnoeus .gt_col_heading {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: normal;
    text-transform: inherit;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
    vertical-align: bottom;
    padding-top: 5px;
    padding-bottom: 6px;
    padding-left: 5px;
    padding-right: 5px;
    overflow-x: hidden;
  }

  #uwirfnoeus .gt_column_spanner_outer {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: normal;
    text-transform: inherit;
    padding-top: 0;
    padding-bottom: 0;
    padding-left: 4px;
    padding-right: 4px;
  }

  #uwirfnoeus .gt_column_spanner_outer:first-child {
    padding-left: 0;
  }

  #uwirfnoeus .gt_column_spanner_outer:last-child {
    padding-right: 0;
  }

  #uwirfnoeus .gt_column_spanner {
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
    vertical-align: bottom;
    padding-top: 5px;
    padding-bottom: 5px;
    overflow-x: hidden;
    display: inline-block;
    width: 100%;
  }

  #uwirfnoeus .gt_group_heading {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    text-transform: inherit;
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #000000;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
    vertical-align: middle;
    text-align: left;
  }

  #uwirfnoeus .gt_empty_group_heading {
    padding: 0.5px;
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #000000;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #FFFFFF;
    vertical-align: middle;
  }

  #uwirfnoeus .gt_from_md > :first-child {
    margin-top: 0;
  }

  #uwirfnoeus .gt_from_md > :last-child {
    margin-bottom: 0;
  }

  #uwirfnoeus .gt_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    margin: 10px;
    border-top-style: solid;
    border-top-width: 1px;
    border-top-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
    vertical-align: middle;
    overflow-x: hidden;
  }

  #uwirfnoeus .gt_stub {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    text-transform: inherit;
    border-right-style: solid;
    border-right-width: 2px;
    border-right-color: rgba(255, 255, 255, 0);
    padding-left: 5px;
    padding-right: 5px;
  }

  #uwirfnoeus .gt_stub_row_group {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    text-transform: inherit;
    border-right-style: solid;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
    padding-left: 5px;
    padding-right: 5px;
    vertical-align: top;
  }

  #uwirfnoeus .gt_row_group_first td {
    border-top-width: 2px;
  }

  #uwirfnoeus .gt_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #uwirfnoeus .gt_first_summary_row {
    border-top-style: solid;
    border-top-color: #D3D3D3;
  }

  #uwirfnoeus .gt_first_summary_row.thick {
    border-top-width: 2px;
  }

  #uwirfnoeus .gt_last_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
  }

  #uwirfnoeus .gt_grand_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #uwirfnoeus .gt_first_grand_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-top-style: double;
    border-top-width: 6px;
    border-top-color: #D3D3D3;
  }

  #uwirfnoeus .gt_striped {
    background-color: rgba(128, 128, 128, 0.05);
  }

  #uwirfnoeus .gt_table_body {
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #D3D3D3;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #uwirfnoeus .gt_footnotes {
    color: #333333;
    background-color: #FFFFFF;
    border-bottom-style: none;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
    border-left-style: none;
    border-left-width: 2px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
  }

  #uwirfnoeus .gt_footnote {
    margin: 0px;
    font-size: 90%;
    padding-left: 4px;
    padding-right: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #uwirfnoeus .gt_sourcenotes {
    color: #333333;
    background-color: #FFFFFF;
    border-bottom-style: none;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
    border-left-style: none;
    border-left-width: 2px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
  }

  #uwirfnoeus .gt_sourcenote {
    font-size: 90%;
    padding-top: 4px;
    padding-bottom: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #uwirfnoeus .gt_left {
    text-align: left;
  }

  #uwirfnoeus .gt_center {
    text-align: center;
  }

  #uwirfnoeus .gt_right {
    text-align: right;
    font-variant-numeric: tabular-nums;
  }

  #uwirfnoeus .gt_font_normal {
    font-weight: normal;
  }

  #uwirfnoeus .gt_font_bold {
    font-weight: bold;
  }

  #uwirfnoeus .gt_font_italic {
    font-style: italic;
  }

  #uwirfnoeus .gt_super {
    font-size: 65%;
  }

  #uwirfnoeus .gt_footnote_marks {
    font-style: italic;
    font-weight: normal;
    font-size: 75%;
    vertical-align: 0.4em;
  }

  #uwirfnoeus .gt_asterisk {
    font-size: 100%;
    vertical-align: 0;
  }

  #uwirfnoeus .gt_indent_1 {
    text-indent: 5px;
  }

  #uwirfnoeus .gt_indent_2 {
    text-indent: 10px;
  }

  #uwirfnoeus .gt_indent_3 {
    text-indent: 15px;
  }

  #uwirfnoeus .gt_indent_4 {
    text-indent: 20px;
  }

  #uwirfnoeus .gt_indent_5 {
    text-indent: 25px;
  }
  </style>
  <table class="gt_table">
    <thead class="gt_header">
      <tr>
        <td colspan="5" class="gt_heading gt_title gt_font_normal gt_bottom_border" style>List of University in CAE with UEC tier</td>
      </tr>

    </thead>
    <thead class="gt_col_headings">
      <tr>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="name">name</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="level_of_actuarial_courses_offered">level_of_actuarial_courses_offered</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="soa_recognition_tier">soa_recognition_tier</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="state_province">state_province</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="country_territory">country_territory</th>
      </tr>
    </thead>
    <tbody class="gt_table_body">
      <tr><td headers="name" class="gt_row gt_left">Illinois State University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">CAE/UEC</td>
  <td headers="state_province" class="gt_row gt_left">Illinois</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">St. John's University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">CAE/UEC</td>
  <td headers="state_province" class="gt_row gt_left">New York</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Temple University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">CAE/UEC</td>
  <td headers="state_province" class="gt_row gt_left">Pennsylvania</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">The University of Iowa</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">CAE/UEC</td>
  <td headers="state_province" class="gt_row gt_left">Iowa</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of Illinois at Urbana-Champaign</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">CAE/UEC</td>
  <td headers="state_province" class="gt_row gt_left">Illinois</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of Nebraska - Lincoln</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">CAE/UEC</td>
  <td headers="state_province" class="gt_row gt_left">Nebraska</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of Wisconsin - Madison</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">CAE/UEC</td>
  <td headers="state_province" class="gt_row gt_left">Wisconsin</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of Wisconsin - Milwaukee</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">CAE/UEC</td>
  <td headers="state_province" class="gt_row gt_left">Wisconsin</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    </tbody>
    <tfoot class="gt_sourcenotes">
      <tr>
        <td class="gt_sourcenote" colspan="5"><em>Data from SOA website</em></td>
      </tr>
    </tfoot>

  </table>
  </div>

- `CAE` : Centers of Actuarial Excellence

  ``` r
  cae<- df1 %>%
    filter(soa_recognition_tier == "CAE")

  pretty_table(df=cae,title = "List of University in CAE tier")
  ```

  <div id="utnjtbreyq" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
  <style>html {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
  }

  #utnjtbreyq .gt_table {
    display: table;
    border-collapse: collapse;
    margin-left: auto;
    margin-right: auto;
    color: #333333;
    font-size: 16px;
    font-weight: normal;
    font-style: normal;
    background-color: #FFFFFF;
    width: auto;
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #FFFFFF;
    border-right-style: none;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 2px;
    border-left-color: #D3D3D3;
  }

  #utnjtbreyq .gt_heading {
    background-color: #FFFFFF;
    text-align: center;
    border-bottom-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
  }

  #utnjtbreyq .gt_caption {
    padding-top: 4px;
    padding-bottom: 4px;
  }

  #utnjtbreyq .gt_title {
    color: #333333;
    font-size: 125%;
    font-weight: initial;
    padding-top: 4px;
    padding-bottom: 4px;
    padding-left: 5px;
    padding-right: 5px;
    border-bottom-color: #FFFFFF;
    border-bottom-width: 0;
  }

  #utnjtbreyq .gt_subtitle {
    color: #333333;
    font-size: 85%;
    font-weight: initial;
    padding-top: 0;
    padding-bottom: 6px;
    padding-left: 5px;
    padding-right: 5px;
    border-top-color: #FFFFFF;
    border-top-width: 0;
  }

  #utnjtbreyq .gt_bottom_border {
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #utnjtbreyq .gt_col_headings {
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #000000;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
  }

  #utnjtbreyq .gt_col_heading {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: normal;
    text-transform: inherit;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
    vertical-align: bottom;
    padding-top: 5px;
    padding-bottom: 6px;
    padding-left: 5px;
    padding-right: 5px;
    overflow-x: hidden;
  }

  #utnjtbreyq .gt_column_spanner_outer {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: normal;
    text-transform: inherit;
    padding-top: 0;
    padding-bottom: 0;
    padding-left: 4px;
    padding-right: 4px;
  }

  #utnjtbreyq .gt_column_spanner_outer:first-child {
    padding-left: 0;
  }

  #utnjtbreyq .gt_column_spanner_outer:last-child {
    padding-right: 0;
  }

  #utnjtbreyq .gt_column_spanner {
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
    vertical-align: bottom;
    padding-top: 5px;
    padding-bottom: 5px;
    overflow-x: hidden;
    display: inline-block;
    width: 100%;
  }

  #utnjtbreyq .gt_group_heading {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    text-transform: inherit;
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #000000;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
    vertical-align: middle;
    text-align: left;
  }

  #utnjtbreyq .gt_empty_group_heading {
    padding: 0.5px;
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #000000;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #FFFFFF;
    vertical-align: middle;
  }

  #utnjtbreyq .gt_from_md > :first-child {
    margin-top: 0;
  }

  #utnjtbreyq .gt_from_md > :last-child {
    margin-bottom: 0;
  }

  #utnjtbreyq .gt_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    margin: 10px;
    border-top-style: solid;
    border-top-width: 1px;
    border-top-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
    vertical-align: middle;
    overflow-x: hidden;
  }

  #utnjtbreyq .gt_stub {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    text-transform: inherit;
    border-right-style: solid;
    border-right-width: 2px;
    border-right-color: rgba(255, 255, 255, 0);
    padding-left: 5px;
    padding-right: 5px;
  }

  #utnjtbreyq .gt_stub_row_group {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    text-transform: inherit;
    border-right-style: solid;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
    padding-left: 5px;
    padding-right: 5px;
    vertical-align: top;
  }

  #utnjtbreyq .gt_row_group_first td {
    border-top-width: 2px;
  }

  #utnjtbreyq .gt_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #utnjtbreyq .gt_first_summary_row {
    border-top-style: solid;
    border-top-color: #D3D3D3;
  }

  #utnjtbreyq .gt_first_summary_row.thick {
    border-top-width: 2px;
  }

  #utnjtbreyq .gt_last_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
  }

  #utnjtbreyq .gt_grand_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #utnjtbreyq .gt_first_grand_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-top-style: double;
    border-top-width: 6px;
    border-top-color: #D3D3D3;
  }

  #utnjtbreyq .gt_striped {
    background-color: rgba(128, 128, 128, 0.05);
  }

  #utnjtbreyq .gt_table_body {
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #D3D3D3;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #utnjtbreyq .gt_footnotes {
    color: #333333;
    background-color: #FFFFFF;
    border-bottom-style: none;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
    border-left-style: none;
    border-left-width: 2px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
  }

  #utnjtbreyq .gt_footnote {
    margin: 0px;
    font-size: 90%;
    padding-left: 4px;
    padding-right: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #utnjtbreyq .gt_sourcenotes {
    color: #333333;
    background-color: #FFFFFF;
    border-bottom-style: none;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
    border-left-style: none;
    border-left-width: 2px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
  }

  #utnjtbreyq .gt_sourcenote {
    font-size: 90%;
    padding-top: 4px;
    padding-bottom: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #utnjtbreyq .gt_left {
    text-align: left;
  }

  #utnjtbreyq .gt_center {
    text-align: center;
  }

  #utnjtbreyq .gt_right {
    text-align: right;
    font-variant-numeric: tabular-nums;
  }

  #utnjtbreyq .gt_font_normal {
    font-weight: normal;
  }

  #utnjtbreyq .gt_font_bold {
    font-weight: bold;
  }

  #utnjtbreyq .gt_font_italic {
    font-style: italic;
  }

  #utnjtbreyq .gt_super {
    font-size: 65%;
  }

  #utnjtbreyq .gt_footnote_marks {
    font-style: italic;
    font-weight: normal;
    font-size: 75%;
    vertical-align: 0.4em;
  }

  #utnjtbreyq .gt_asterisk {
    font-size: 100%;
    vertical-align: 0;
  }

  #utnjtbreyq .gt_indent_1 {
    text-indent: 5px;
  }

  #utnjtbreyq .gt_indent_2 {
    text-indent: 10px;
  }

  #utnjtbreyq .gt_indent_3 {
    text-indent: 15px;
  }

  #utnjtbreyq .gt_indent_4 {
    text-indent: 20px;
  }

  #utnjtbreyq .gt_indent_5 {
    text-indent: 25px;
  }
  </style>
  <table class="gt_table">
    <thead class="gt_header">
      <tr>
        <td colspan="5" class="gt_heading gt_title gt_font_normal gt_bottom_border" style>List of University in CAE tier</td>
      </tr>

    </thead>
    <thead class="gt_col_headings">
      <tr>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="name">name</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="level_of_actuarial_courses_offered">level_of_actuarial_courses_offered</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="soa_recognition_tier">soa_recognition_tier</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="state_province">state_province</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="country_territory">country_territory</th>
      </tr>
    </thead>
    <tbody class="gt_table_body">
      <tr><td headers="name" class="gt_row gt_left">Georgia State University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">CAE</td>
  <td headers="state_province" class="gt_row gt_left">Georgia</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Towson University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">CAE</td>
  <td headers="state_province" class="gt_row gt_left">Maryland</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of California Santa Barbara (UCSB)</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">CAE</td>
  <td headers="state_province" class="gt_row gt_left">California</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of Connecticut</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">CAE</td>
  <td headers="state_province" class="gt_row gt_left">Connecticut</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of Michigan</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">CAE</td>
  <td headers="state_province" class="gt_row gt_left">Michigan</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of Texas at Dallas</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">CAE</td>
  <td headers="state_province" class="gt_row gt_left">Texas</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    </tbody>
    <tfoot class="gt_sourcenotes">
      <tr>
        <td class="gt_sourcenote" colspan="5"><em>Data from SOA website</em></td>
      </tr>
    </tfoot>

  </table>
  </div>

- `UCAP-AC`: Advanced Curriculum

  ``` r
  ac <- df1 %>%
    filter(soa_recognition_tier == "UCAP-AC")

  pretty_table(df=ac,title = "List of University in AC tier")
  ```

  <div id="duokjluwvb" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
  <style>html {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
  }

  #duokjluwvb .gt_table {
    display: table;
    border-collapse: collapse;
    margin-left: auto;
    margin-right: auto;
    color: #333333;
    font-size: 16px;
    font-weight: normal;
    font-style: normal;
    background-color: #FFFFFF;
    width: auto;
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #FFFFFF;
    border-right-style: none;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 2px;
    border-left-color: #D3D3D3;
  }

  #duokjluwvb .gt_heading {
    background-color: #FFFFFF;
    text-align: center;
    border-bottom-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
  }

  #duokjluwvb .gt_caption {
    padding-top: 4px;
    padding-bottom: 4px;
  }

  #duokjluwvb .gt_title {
    color: #333333;
    font-size: 125%;
    font-weight: initial;
    padding-top: 4px;
    padding-bottom: 4px;
    padding-left: 5px;
    padding-right: 5px;
    border-bottom-color: #FFFFFF;
    border-bottom-width: 0;
  }

  #duokjluwvb .gt_subtitle {
    color: #333333;
    font-size: 85%;
    font-weight: initial;
    padding-top: 0;
    padding-bottom: 6px;
    padding-left: 5px;
    padding-right: 5px;
    border-top-color: #FFFFFF;
    border-top-width: 0;
  }

  #duokjluwvb .gt_bottom_border {
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #duokjluwvb .gt_col_headings {
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #000000;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
  }

  #duokjluwvb .gt_col_heading {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: normal;
    text-transform: inherit;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
    vertical-align: bottom;
    padding-top: 5px;
    padding-bottom: 6px;
    padding-left: 5px;
    padding-right: 5px;
    overflow-x: hidden;
  }

  #duokjluwvb .gt_column_spanner_outer {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: normal;
    text-transform: inherit;
    padding-top: 0;
    padding-bottom: 0;
    padding-left: 4px;
    padding-right: 4px;
  }

  #duokjluwvb .gt_column_spanner_outer:first-child {
    padding-left: 0;
  }

  #duokjluwvb .gt_column_spanner_outer:last-child {
    padding-right: 0;
  }

  #duokjluwvb .gt_column_spanner {
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
    vertical-align: bottom;
    padding-top: 5px;
    padding-bottom: 5px;
    overflow-x: hidden;
    display: inline-block;
    width: 100%;
  }

  #duokjluwvb .gt_group_heading {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    text-transform: inherit;
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #000000;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
    vertical-align: middle;
    text-align: left;
  }

  #duokjluwvb .gt_empty_group_heading {
    padding: 0.5px;
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #000000;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #FFFFFF;
    vertical-align: middle;
  }

  #duokjluwvb .gt_from_md > :first-child {
    margin-top: 0;
  }

  #duokjluwvb .gt_from_md > :last-child {
    margin-bottom: 0;
  }

  #duokjluwvb .gt_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    margin: 10px;
    border-top-style: solid;
    border-top-width: 1px;
    border-top-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
    vertical-align: middle;
    overflow-x: hidden;
  }

  #duokjluwvb .gt_stub {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    text-transform: inherit;
    border-right-style: solid;
    border-right-width: 2px;
    border-right-color: rgba(255, 255, 255, 0);
    padding-left: 5px;
    padding-right: 5px;
  }

  #duokjluwvb .gt_stub_row_group {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    text-transform: inherit;
    border-right-style: solid;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
    padding-left: 5px;
    padding-right: 5px;
    vertical-align: top;
  }

  #duokjluwvb .gt_row_group_first td {
    border-top-width: 2px;
  }

  #duokjluwvb .gt_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #duokjluwvb .gt_first_summary_row {
    border-top-style: solid;
    border-top-color: #D3D3D3;
  }

  #duokjluwvb .gt_first_summary_row.thick {
    border-top-width: 2px;
  }

  #duokjluwvb .gt_last_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
  }

  #duokjluwvb .gt_grand_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #duokjluwvb .gt_first_grand_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-top-style: double;
    border-top-width: 6px;
    border-top-color: #D3D3D3;
  }

  #duokjluwvb .gt_striped {
    background-color: rgba(128, 128, 128, 0.05);
  }

  #duokjluwvb .gt_table_body {
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #D3D3D3;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #duokjluwvb .gt_footnotes {
    color: #333333;
    background-color: #FFFFFF;
    border-bottom-style: none;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
    border-left-style: none;
    border-left-width: 2px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
  }

  #duokjluwvb .gt_footnote {
    margin: 0px;
    font-size: 90%;
    padding-left: 4px;
    padding-right: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #duokjluwvb .gt_sourcenotes {
    color: #333333;
    background-color: #FFFFFF;
    border-bottom-style: none;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
    border-left-style: none;
    border-left-width: 2px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
  }

  #duokjluwvb .gt_sourcenote {
    font-size: 90%;
    padding-top: 4px;
    padding-bottom: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #duokjluwvb .gt_left {
    text-align: left;
  }

  #duokjluwvb .gt_center {
    text-align: center;
  }

  #duokjluwvb .gt_right {
    text-align: right;
    font-variant-numeric: tabular-nums;
  }

  #duokjluwvb .gt_font_normal {
    font-weight: normal;
  }

  #duokjluwvb .gt_font_bold {
    font-weight: bold;
  }

  #duokjluwvb .gt_font_italic {
    font-style: italic;
  }

  #duokjluwvb .gt_super {
    font-size: 65%;
  }

  #duokjluwvb .gt_footnote_marks {
    font-style: italic;
    font-weight: normal;
    font-size: 75%;
    vertical-align: 0.4em;
  }

  #duokjluwvb .gt_asterisk {
    font-size: 100%;
    vertical-align: 0;
  }

  #duokjluwvb .gt_indent_1 {
    text-indent: 5px;
  }

  #duokjluwvb .gt_indent_2 {
    text-indent: 10px;
  }

  #duokjluwvb .gt_indent_3 {
    text-indent: 15px;
  }

  #duokjluwvb .gt_indent_4 {
    text-indent: 20px;
  }

  #duokjluwvb .gt_indent_5 {
    text-indent: 25px;
  }
  </style>
  <table class="gt_table">
    <thead class="gt_header">
      <tr>
        <td colspan="5" class="gt_heading gt_title gt_font_normal gt_bottom_border" style>List of University in AC tier</td>
      </tr>

    </thead>
    <thead class="gt_col_headings">
      <tr>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="name">name</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="level_of_actuarial_courses_offered">level_of_actuarial_courses_offered</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="soa_recognition_tier">soa_recognition_tier</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="state_province">state_province</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="country_territory">country_territory</th>
      </tr>
    </thead>
    <tbody class="gt_table_body">
      <tr><td headers="name" class="gt_row gt_left">Arizona State University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Arizona</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Ball State University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Indiana</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Boston University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Massachusetts</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">DePaul University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Illinois</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Florida State University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Florida</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">George Mason University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Virginia</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Kent State University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Ohio</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Maryville University of St. Louis</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Missouri</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Middle Tennessee State University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Tennessee</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Missouri University of Science and Technology</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Missouri</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Roosevelt University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Illinois</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">The Ohio State University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Ohio</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">The University of North Carolina at Charlotte</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">North Carolina</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of Central Missouri</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Missouri</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of Missouri - Columbia</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Missouri</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of Texas at Austin</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Texas</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Wharton School - University of Pennsylvania</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Pennsylvania</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Youngstown State University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-AC</td>
  <td headers="state_province" class="gt_row gt_left">Ohio</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    </tbody>
    <tfoot class="gt_sourcenotes">
      <tr>
        <td class="gt_sourcenote" colspan="5"><em>Data from SOA website</em></td>
      </tr>
    </tfoot>

  </table>
  </div>

- `UCAP-IC` : Introductory Curriculum

  ``` r
  ic <- df1 %>%
    filter(soa_recognition_tier == "UCAP-IC")

  pretty_table(df=ic,title = "List of University in IC tier")
  ```

  <div id="xgirooddbk" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
  <style>html {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
  }

  #xgirooddbk .gt_table {
    display: table;
    border-collapse: collapse;
    margin-left: auto;
    margin-right: auto;
    color: #333333;
    font-size: 16px;
    font-weight: normal;
    font-style: normal;
    background-color: #FFFFFF;
    width: auto;
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #FFFFFF;
    border-right-style: none;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 2px;
    border-left-color: #D3D3D3;
  }

  #xgirooddbk .gt_heading {
    background-color: #FFFFFF;
    text-align: center;
    border-bottom-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
  }

  #xgirooddbk .gt_caption {
    padding-top: 4px;
    padding-bottom: 4px;
  }

  #xgirooddbk .gt_title {
    color: #333333;
    font-size: 125%;
    font-weight: initial;
    padding-top: 4px;
    padding-bottom: 4px;
    padding-left: 5px;
    padding-right: 5px;
    border-bottom-color: #FFFFFF;
    border-bottom-width: 0;
  }

  #xgirooddbk .gt_subtitle {
    color: #333333;
    font-size: 85%;
    font-weight: initial;
    padding-top: 0;
    padding-bottom: 6px;
    padding-left: 5px;
    padding-right: 5px;
    border-top-color: #FFFFFF;
    border-top-width: 0;
  }

  #xgirooddbk .gt_bottom_border {
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #xgirooddbk .gt_col_headings {
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #000000;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
  }

  #xgirooddbk .gt_col_heading {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: normal;
    text-transform: inherit;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
    vertical-align: bottom;
    padding-top: 5px;
    padding-bottom: 6px;
    padding-left: 5px;
    padding-right: 5px;
    overflow-x: hidden;
  }

  #xgirooddbk .gt_column_spanner_outer {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: normal;
    text-transform: inherit;
    padding-top: 0;
    padding-bottom: 0;
    padding-left: 4px;
    padding-right: 4px;
  }

  #xgirooddbk .gt_column_spanner_outer:first-child {
    padding-left: 0;
  }

  #xgirooddbk .gt_column_spanner_outer:last-child {
    padding-right: 0;
  }

  #xgirooddbk .gt_column_spanner {
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
    vertical-align: bottom;
    padding-top: 5px;
    padding-bottom: 5px;
    overflow-x: hidden;
    display: inline-block;
    width: 100%;
  }

  #xgirooddbk .gt_group_heading {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    text-transform: inherit;
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #000000;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
    vertical-align: middle;
    text-align: left;
  }

  #xgirooddbk .gt_empty_group_heading {
    padding: 0.5px;
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #000000;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #FFFFFF;
    vertical-align: middle;
  }

  #xgirooddbk .gt_from_md > :first-child {
    margin-top: 0;
  }

  #xgirooddbk .gt_from_md > :last-child {
    margin-bottom: 0;
  }

  #xgirooddbk .gt_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    margin: 10px;
    border-top-style: solid;
    border-top-width: 1px;
    border-top-color: #FFFFFF;
    border-left-style: none;
    border-left-width: 1px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 1px;
    border-right-color: #D3D3D3;
    vertical-align: middle;
    overflow-x: hidden;
  }

  #xgirooddbk .gt_stub {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    text-transform: inherit;
    border-right-style: solid;
    border-right-width: 2px;
    border-right-color: rgba(255, 255, 255, 0);
    padding-left: 5px;
    padding-right: 5px;
  }

  #xgirooddbk .gt_stub_row_group {
    color: #333333;
    background-color: #FFFFFF;
    font-size: 100%;
    font-weight: initial;
    text-transform: inherit;
    border-right-style: solid;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
    padding-left: 5px;
    padding-right: 5px;
    vertical-align: top;
  }

  #xgirooddbk .gt_row_group_first td {
    border-top-width: 2px;
  }

  #xgirooddbk .gt_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #xgirooddbk .gt_first_summary_row {
    border-top-style: solid;
    border-top-color: #D3D3D3;
  }

  #xgirooddbk .gt_first_summary_row.thick {
    border-top-width: 2px;
  }

  #xgirooddbk .gt_last_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
  }

  #xgirooddbk .gt_grand_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #xgirooddbk .gt_first_grand_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-top-style: double;
    border-top-width: 6px;
    border-top-color: #D3D3D3;
  }

  #xgirooddbk .gt_striped {
    background-color: rgba(128, 128, 128, 0.05);
  }

  #xgirooddbk .gt_table_body {
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #D3D3D3;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #xgirooddbk .gt_footnotes {
    color: #333333;
    background-color: #FFFFFF;
    border-bottom-style: none;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
    border-left-style: none;
    border-left-width: 2px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
  }

  #xgirooddbk .gt_footnote {
    margin: 0px;
    font-size: 90%;
    padding-left: 4px;
    padding-right: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #xgirooddbk .gt_sourcenotes {
    color: #333333;
    background-color: #FFFFFF;
    border-bottom-style: none;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
    border-left-style: none;
    border-left-width: 2px;
    border-left-color: #D3D3D3;
    border-right-style: none;
    border-right-width: 2px;
    border-right-color: #D3D3D3;
  }

  #xgirooddbk .gt_sourcenote {
    font-size: 90%;
    padding-top: 4px;
    padding-bottom: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #xgirooddbk .gt_left {
    text-align: left;
  }

  #xgirooddbk .gt_center {
    text-align: center;
  }

  #xgirooddbk .gt_right {
    text-align: right;
    font-variant-numeric: tabular-nums;
  }

  #xgirooddbk .gt_font_normal {
    font-weight: normal;
  }

  #xgirooddbk .gt_font_bold {
    font-weight: bold;
  }

  #xgirooddbk .gt_font_italic {
    font-style: italic;
  }

  #xgirooddbk .gt_super {
    font-size: 65%;
  }

  #xgirooddbk .gt_footnote_marks {
    font-style: italic;
    font-weight: normal;
    font-size: 75%;
    vertical-align: 0.4em;
  }

  #xgirooddbk .gt_asterisk {
    font-size: 100%;
    vertical-align: 0;
  }

  #xgirooddbk .gt_indent_1 {
    text-indent: 5px;
  }

  #xgirooddbk .gt_indent_2 {
    text-indent: 10px;
  }

  #xgirooddbk .gt_indent_3 {
    text-indent: 15px;
  }

  #xgirooddbk .gt_indent_4 {
    text-indent: 20px;
  }

  #xgirooddbk .gt_indent_5 {
    text-indent: 25px;
  }
  </style>
  <table class="gt_table">
    <thead class="gt_header">
      <tr>
        <td colspan="5" class="gt_heading gt_title gt_font_normal gt_bottom_border" style>List of University in IC tier</td>
      </tr>

    </thead>
    <thead class="gt_col_headings">
      <tr>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="name">name</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="level_of_actuarial_courses_offered">level_of_actuarial_courses_offered</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="soa_recognition_tier">soa_recognition_tier</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="state_province">state_province</th>
        <th class="gt_col_heading gt_columns_bottom_border gt_left" rowspan="1" colspan="1" scope="col" id="country_territory">country_territory</th>
      </tr>
    </thead>
    <tbody class="gt_table_body">
      <tr><td headers="name" class="gt_row gt_left">Bowling Green State University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Ohio</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Central Connecticut State</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Connecticut</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Columbia University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">New York</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Embry-Riddle Aeronautical University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Florida</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Johns Hopkins University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Maryland</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Lock Haven University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Pennsylvania</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Minnesota State University - Mankato</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Minnesota</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Murray State University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Kentucky</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Northern Arizona University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Arizona</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Oregon State University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Oregon</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Purdue University Fort Wayne</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Indiana</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Southern Illinois University – Carbondale</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Illinois</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">Tennessee Technological University</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Tennessee</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of California Riverside</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">California</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of Massachusetts - Boston</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Massachusetts</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of Nevada - Reno</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Nevada</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
      <tr><td headers="name" class="gt_row gt_left">University of Northern Iowa</td>
  <td headers="level_of_actuarial_courses_offered" class="gt_row gt_left">Masters</td>
  <td headers="soa_recognition_tier" class="gt_row gt_left">UCAP-IC</td>
  <td headers="state_province" class="gt_row gt_left">Iowa</td>
  <td headers="country_territory" class="gt_row gt_left">United States</td></tr>
    </tbody>
    <tfoot class="gt_sourcenotes">
      <tr>
        <td class="gt_sourcenote" colspan="5"><em>Data from SOA website</em></td>
      </tr>
    </tfoot>

  </table>
  </div>

### 
