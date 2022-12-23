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

<div id="wqvddbawgw" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#wqvddbawgw .gt_table {
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

#wqvddbawgw .gt_heading {
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

#wqvddbawgw .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#wqvddbawgw .gt_title {
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

#wqvddbawgw .gt_subtitle {
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

#wqvddbawgw .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#wqvddbawgw .gt_col_headings {
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

#wqvddbawgw .gt_col_heading {
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

#wqvddbawgw .gt_column_spanner_outer {
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

#wqvddbawgw .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#wqvddbawgw .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#wqvddbawgw .gt_column_spanner {
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

#wqvddbawgw .gt_group_heading {
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

#wqvddbawgw .gt_empty_group_heading {
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

#wqvddbawgw .gt_from_md > :first-child {
  margin-top: 0;
}

#wqvddbawgw .gt_from_md > :last-child {
  margin-bottom: 0;
}

#wqvddbawgw .gt_row {
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

#wqvddbawgw .gt_stub {
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

#wqvddbawgw .gt_stub_row_group {
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

#wqvddbawgw .gt_row_group_first td {
  border-top-width: 2px;
}

#wqvddbawgw .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#wqvddbawgw .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#wqvddbawgw .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#wqvddbawgw .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#wqvddbawgw .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#wqvddbawgw .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#wqvddbawgw .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#wqvddbawgw .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#wqvddbawgw .gt_footnotes {
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

#wqvddbawgw .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#wqvddbawgw .gt_sourcenotes {
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

#wqvddbawgw .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#wqvddbawgw .gt_left {
  text-align: left;
}

#wqvddbawgw .gt_center {
  text-align: center;
}

#wqvddbawgw .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#wqvddbawgw .gt_font_normal {
  font-weight: normal;
}

#wqvddbawgw .gt_font_bold {
  font-weight: bold;
}

#wqvddbawgw .gt_font_italic {
  font-style: italic;
}

#wqvddbawgw .gt_super {
  font-size: 65%;
}

#wqvddbawgw .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#wqvddbawgw .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#wqvddbawgw .gt_indent_1 {
  text-indent: 5px;
}

#wqvddbawgw .gt_indent_2 {
  text-indent: 10px;
}

#wqvddbawgw .gt_indent_3 {
  text-indent: 15px;
}

#wqvddbawgw .gt_indent_4 {
  text-indent: 20px;
}

#wqvddbawgw .gt_indent_5 {
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

<div id="xtzvaddlnu" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#xtzvaddlnu .gt_table {
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

#xtzvaddlnu .gt_heading {
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

#xtzvaddlnu .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#xtzvaddlnu .gt_title {
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

#xtzvaddlnu .gt_subtitle {
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

#xtzvaddlnu .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#xtzvaddlnu .gt_col_headings {
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

#xtzvaddlnu .gt_col_heading {
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

#xtzvaddlnu .gt_column_spanner_outer {
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

#xtzvaddlnu .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#xtzvaddlnu .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#xtzvaddlnu .gt_column_spanner {
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

#xtzvaddlnu .gt_group_heading {
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

#xtzvaddlnu .gt_empty_group_heading {
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

#xtzvaddlnu .gt_from_md > :first-child {
  margin-top: 0;
}

#xtzvaddlnu .gt_from_md > :last-child {
  margin-bottom: 0;
}

#xtzvaddlnu .gt_row {
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

#xtzvaddlnu .gt_stub {
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

#xtzvaddlnu .gt_stub_row_group {
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

#xtzvaddlnu .gt_row_group_first td {
  border-top-width: 2px;
}

#xtzvaddlnu .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#xtzvaddlnu .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#xtzvaddlnu .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#xtzvaddlnu .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#xtzvaddlnu .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#xtzvaddlnu .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#xtzvaddlnu .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#xtzvaddlnu .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#xtzvaddlnu .gt_footnotes {
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

#xtzvaddlnu .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#xtzvaddlnu .gt_sourcenotes {
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

#xtzvaddlnu .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#xtzvaddlnu .gt_left {
  text-align: left;
}

#xtzvaddlnu .gt_center {
  text-align: center;
}

#xtzvaddlnu .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#xtzvaddlnu .gt_font_normal {
  font-weight: normal;
}

#xtzvaddlnu .gt_font_bold {
  font-weight: bold;
}

#xtzvaddlnu .gt_font_italic {
  font-style: italic;
}

#xtzvaddlnu .gt_super {
  font-size: 65%;
}

#xtzvaddlnu .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#xtzvaddlnu .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#xtzvaddlnu .gt_indent_1 {
  text-indent: 5px;
}

#xtzvaddlnu .gt_indent_2 {
  text-indent: 10px;
}

#xtzvaddlnu .gt_indent_3 {
  text-indent: 15px;
}

#xtzvaddlnu .gt_indent_4 {
  text-indent: 20px;
}

#xtzvaddlnu .gt_indent_5 {
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

<div id="mhlntvhpfj" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#mhlntvhpfj .gt_table {
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

#mhlntvhpfj .gt_heading {
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

#mhlntvhpfj .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#mhlntvhpfj .gt_title {
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

#mhlntvhpfj .gt_subtitle {
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

#mhlntvhpfj .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#mhlntvhpfj .gt_col_headings {
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

#mhlntvhpfj .gt_col_heading {
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

#mhlntvhpfj .gt_column_spanner_outer {
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

#mhlntvhpfj .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#mhlntvhpfj .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#mhlntvhpfj .gt_column_spanner {
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

#mhlntvhpfj .gt_group_heading {
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

#mhlntvhpfj .gt_empty_group_heading {
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

#mhlntvhpfj .gt_from_md > :first-child {
  margin-top: 0;
}

#mhlntvhpfj .gt_from_md > :last-child {
  margin-bottom: 0;
}

#mhlntvhpfj .gt_row {
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

#mhlntvhpfj .gt_stub {
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

#mhlntvhpfj .gt_stub_row_group {
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

#mhlntvhpfj .gt_row_group_first td {
  border-top-width: 2px;
}

#mhlntvhpfj .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#mhlntvhpfj .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#mhlntvhpfj .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#mhlntvhpfj .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#mhlntvhpfj .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#mhlntvhpfj .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#mhlntvhpfj .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#mhlntvhpfj .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#mhlntvhpfj .gt_footnotes {
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

#mhlntvhpfj .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#mhlntvhpfj .gt_sourcenotes {
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

#mhlntvhpfj .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#mhlntvhpfj .gt_left {
  text-align: left;
}

#mhlntvhpfj .gt_center {
  text-align: center;
}

#mhlntvhpfj .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#mhlntvhpfj .gt_font_normal {
  font-weight: normal;
}

#mhlntvhpfj .gt_font_bold {
  font-weight: bold;
}

#mhlntvhpfj .gt_font_italic {
  font-style: italic;
}

#mhlntvhpfj .gt_super {
  font-size: 65%;
}

#mhlntvhpfj .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#mhlntvhpfj .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#mhlntvhpfj .gt_indent_1 {
  text-indent: 5px;
}

#mhlntvhpfj .gt_indent_2 {
  text-indent: 10px;
}

#mhlntvhpfj .gt_indent_3 {
  text-indent: 15px;
}

#mhlntvhpfj .gt_indent_4 {
  text-indent: 20px;
}

#mhlntvhpfj .gt_indent_5 {
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

<div id="hnxaunwfaz" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
<style>html {
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
}

#hnxaunwfaz .gt_table {
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

#hnxaunwfaz .gt_heading {
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

#hnxaunwfaz .gt_caption {
  padding-top: 4px;
  padding-bottom: 4px;
}

#hnxaunwfaz .gt_title {
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

#hnxaunwfaz .gt_subtitle {
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

#hnxaunwfaz .gt_bottom_border {
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#hnxaunwfaz .gt_col_headings {
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

#hnxaunwfaz .gt_col_heading {
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

#hnxaunwfaz .gt_column_spanner_outer {
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

#hnxaunwfaz .gt_column_spanner_outer:first-child {
  padding-left: 0;
}

#hnxaunwfaz .gt_column_spanner_outer:last-child {
  padding-right: 0;
}

#hnxaunwfaz .gt_column_spanner {
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

#hnxaunwfaz .gt_group_heading {
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

#hnxaunwfaz .gt_empty_group_heading {
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

#hnxaunwfaz .gt_from_md > :first-child {
  margin-top: 0;
}

#hnxaunwfaz .gt_from_md > :last-child {
  margin-bottom: 0;
}

#hnxaunwfaz .gt_row {
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

#hnxaunwfaz .gt_stub {
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

#hnxaunwfaz .gt_stub_row_group {
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

#hnxaunwfaz .gt_row_group_first td {
  border-top-width: 2px;
}

#hnxaunwfaz .gt_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#hnxaunwfaz .gt_first_summary_row {
  border-top-style: solid;
  border-top-color: #D3D3D3;
}

#hnxaunwfaz .gt_first_summary_row.thick {
  border-top-width: 2px;
}

#hnxaunwfaz .gt_last_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #D3D3D3;
}

#hnxaunwfaz .gt_grand_summary_row {
  color: #333333;
  background-color: #FFFFFF;
  text-transform: inherit;
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
}

#hnxaunwfaz .gt_first_grand_summary_row {
  padding-top: 8px;
  padding-bottom: 8px;
  padding-left: 5px;
  padding-right: 5px;
  border-top-style: double;
  border-top-width: 6px;
  border-top-color: #D3D3D3;
}

#hnxaunwfaz .gt_striped {
  background-color: rgba(128, 128, 128, 0.05);
}

#hnxaunwfaz .gt_table_body {
  border-top-style: solid;
  border-top-width: 2px;
  border-top-color: #D3D3D3;
  border-bottom-style: solid;
  border-bottom-width: 2px;
  border-bottom-color: #000000;
}

#hnxaunwfaz .gt_footnotes {
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

#hnxaunwfaz .gt_footnote {
  margin: 0px;
  font-size: 90%;
  padding-left: 4px;
  padding-right: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#hnxaunwfaz .gt_sourcenotes {
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

#hnxaunwfaz .gt_sourcenote {
  font-size: 90%;
  padding-top: 4px;
  padding-bottom: 4px;
  padding-left: 5px;
  padding-right: 5px;
}

#hnxaunwfaz .gt_left {
  text-align: left;
}

#hnxaunwfaz .gt_center {
  text-align: center;
}

#hnxaunwfaz .gt_right {
  text-align: right;
  font-variant-numeric: tabular-nums;
}

#hnxaunwfaz .gt_font_normal {
  font-weight: normal;
}

#hnxaunwfaz .gt_font_bold {
  font-weight: bold;
}

#hnxaunwfaz .gt_font_italic {
  font-style: italic;
}

#hnxaunwfaz .gt_super {
  font-size: 65%;
}

#hnxaunwfaz .gt_footnote_marks {
  font-style: italic;
  font-weight: normal;
  font-size: 75%;
  vertical-align: 0.4em;
}

#hnxaunwfaz .gt_asterisk {
  font-size: 100%;
  vertical-align: 0;
}

#hnxaunwfaz .gt_indent_1 {
  text-indent: 5px;
}

#hnxaunwfaz .gt_indent_2 {
  text-indent: 10px;
}

#hnxaunwfaz .gt_indent_3 {
  text-indent: 15px;
}

#hnxaunwfaz .gt_indent_4 {
  text-indent: 20px;
}

#hnxaunwfaz .gt_indent_5 {
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

  <div id="tqnfdaqbcy" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
  <style>html {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
  }

  #tqnfdaqbcy .gt_table {
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

  #tqnfdaqbcy .gt_heading {
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

  #tqnfdaqbcy .gt_caption {
    padding-top: 4px;
    padding-bottom: 4px;
  }

  #tqnfdaqbcy .gt_title {
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

  #tqnfdaqbcy .gt_subtitle {
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

  #tqnfdaqbcy .gt_bottom_border {
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #tqnfdaqbcy .gt_col_headings {
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

  #tqnfdaqbcy .gt_col_heading {
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

  #tqnfdaqbcy .gt_column_spanner_outer {
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

  #tqnfdaqbcy .gt_column_spanner_outer:first-child {
    padding-left: 0;
  }

  #tqnfdaqbcy .gt_column_spanner_outer:last-child {
    padding-right: 0;
  }

  #tqnfdaqbcy .gt_column_spanner {
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

  #tqnfdaqbcy .gt_group_heading {
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

  #tqnfdaqbcy .gt_empty_group_heading {
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

  #tqnfdaqbcy .gt_from_md > :first-child {
    margin-top: 0;
  }

  #tqnfdaqbcy .gt_from_md > :last-child {
    margin-bottom: 0;
  }

  #tqnfdaqbcy .gt_row {
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

  #tqnfdaqbcy .gt_stub {
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

  #tqnfdaqbcy .gt_stub_row_group {
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

  #tqnfdaqbcy .gt_row_group_first td {
    border-top-width: 2px;
  }

  #tqnfdaqbcy .gt_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #tqnfdaqbcy .gt_first_summary_row {
    border-top-style: solid;
    border-top-color: #D3D3D3;
  }

  #tqnfdaqbcy .gt_first_summary_row.thick {
    border-top-width: 2px;
  }

  #tqnfdaqbcy .gt_last_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
  }

  #tqnfdaqbcy .gt_grand_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #tqnfdaqbcy .gt_first_grand_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-top-style: double;
    border-top-width: 6px;
    border-top-color: #D3D3D3;
  }

  #tqnfdaqbcy .gt_striped {
    background-color: rgba(128, 128, 128, 0.05);
  }

  #tqnfdaqbcy .gt_table_body {
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #D3D3D3;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #tqnfdaqbcy .gt_footnotes {
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

  #tqnfdaqbcy .gt_footnote {
    margin: 0px;
    font-size: 90%;
    padding-left: 4px;
    padding-right: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #tqnfdaqbcy .gt_sourcenotes {
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

  #tqnfdaqbcy .gt_sourcenote {
    font-size: 90%;
    padding-top: 4px;
    padding-bottom: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #tqnfdaqbcy .gt_left {
    text-align: left;
  }

  #tqnfdaqbcy .gt_center {
    text-align: center;
  }

  #tqnfdaqbcy .gt_right {
    text-align: right;
    font-variant-numeric: tabular-nums;
  }

  #tqnfdaqbcy .gt_font_normal {
    font-weight: normal;
  }

  #tqnfdaqbcy .gt_font_bold {
    font-weight: bold;
  }

  #tqnfdaqbcy .gt_font_italic {
    font-style: italic;
  }

  #tqnfdaqbcy .gt_super {
    font-size: 65%;
  }

  #tqnfdaqbcy .gt_footnote_marks {
    font-style: italic;
    font-weight: normal;
    font-size: 75%;
    vertical-align: 0.4em;
  }

  #tqnfdaqbcy .gt_asterisk {
    font-size: 100%;
    vertical-align: 0;
  }

  #tqnfdaqbcy .gt_indent_1 {
    text-indent: 5px;
  }

  #tqnfdaqbcy .gt_indent_2 {
    text-indent: 10px;
  }

  #tqnfdaqbcy .gt_indent_3 {
    text-indent: 15px;
  }

  #tqnfdaqbcy .gt_indent_4 {
    text-indent: 20px;
  }

  #tqnfdaqbcy .gt_indent_5 {
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

  <div id="mwbptkywzw" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
  <style>html {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
  }

  #mwbptkywzw .gt_table {
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

  #mwbptkywzw .gt_heading {
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

  #mwbptkywzw .gt_caption {
    padding-top: 4px;
    padding-bottom: 4px;
  }

  #mwbptkywzw .gt_title {
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

  #mwbptkywzw .gt_subtitle {
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

  #mwbptkywzw .gt_bottom_border {
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #mwbptkywzw .gt_col_headings {
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

  #mwbptkywzw .gt_col_heading {
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

  #mwbptkywzw .gt_column_spanner_outer {
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

  #mwbptkywzw .gt_column_spanner_outer:first-child {
    padding-left: 0;
  }

  #mwbptkywzw .gt_column_spanner_outer:last-child {
    padding-right: 0;
  }

  #mwbptkywzw .gt_column_spanner {
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

  #mwbptkywzw .gt_group_heading {
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

  #mwbptkywzw .gt_empty_group_heading {
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

  #mwbptkywzw .gt_from_md > :first-child {
    margin-top: 0;
  }

  #mwbptkywzw .gt_from_md > :last-child {
    margin-bottom: 0;
  }

  #mwbptkywzw .gt_row {
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

  #mwbptkywzw .gt_stub {
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

  #mwbptkywzw .gt_stub_row_group {
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

  #mwbptkywzw .gt_row_group_first td {
    border-top-width: 2px;
  }

  #mwbptkywzw .gt_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #mwbptkywzw .gt_first_summary_row {
    border-top-style: solid;
    border-top-color: #D3D3D3;
  }

  #mwbptkywzw .gt_first_summary_row.thick {
    border-top-width: 2px;
  }

  #mwbptkywzw .gt_last_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
  }

  #mwbptkywzw .gt_grand_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #mwbptkywzw .gt_first_grand_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-top-style: double;
    border-top-width: 6px;
    border-top-color: #D3D3D3;
  }

  #mwbptkywzw .gt_striped {
    background-color: rgba(128, 128, 128, 0.05);
  }

  #mwbptkywzw .gt_table_body {
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #D3D3D3;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #mwbptkywzw .gt_footnotes {
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

  #mwbptkywzw .gt_footnote {
    margin: 0px;
    font-size: 90%;
    padding-left: 4px;
    padding-right: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #mwbptkywzw .gt_sourcenotes {
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

  #mwbptkywzw .gt_sourcenote {
    font-size: 90%;
    padding-top: 4px;
    padding-bottom: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #mwbptkywzw .gt_left {
    text-align: left;
  }

  #mwbptkywzw .gt_center {
    text-align: center;
  }

  #mwbptkywzw .gt_right {
    text-align: right;
    font-variant-numeric: tabular-nums;
  }

  #mwbptkywzw .gt_font_normal {
    font-weight: normal;
  }

  #mwbptkywzw .gt_font_bold {
    font-weight: bold;
  }

  #mwbptkywzw .gt_font_italic {
    font-style: italic;
  }

  #mwbptkywzw .gt_super {
    font-size: 65%;
  }

  #mwbptkywzw .gt_footnote_marks {
    font-style: italic;
    font-weight: normal;
    font-size: 75%;
    vertical-align: 0.4em;
  }

  #mwbptkywzw .gt_asterisk {
    font-size: 100%;
    vertical-align: 0;
  }

  #mwbptkywzw .gt_indent_1 {
    text-indent: 5px;
  }

  #mwbptkywzw .gt_indent_2 {
    text-indent: 10px;
  }

  #mwbptkywzw .gt_indent_3 {
    text-indent: 15px;
  }

  #mwbptkywzw .gt_indent_4 {
    text-indent: 20px;
  }

  #mwbptkywzw .gt_indent_5 {
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

  <div id="jetkbwbfbf" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
  <style>html {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
  }

  #jetkbwbfbf .gt_table {
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

  #jetkbwbfbf .gt_heading {
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

  #jetkbwbfbf .gt_caption {
    padding-top: 4px;
    padding-bottom: 4px;
  }

  #jetkbwbfbf .gt_title {
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

  #jetkbwbfbf .gt_subtitle {
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

  #jetkbwbfbf .gt_bottom_border {
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #jetkbwbfbf .gt_col_headings {
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

  #jetkbwbfbf .gt_col_heading {
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

  #jetkbwbfbf .gt_column_spanner_outer {
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

  #jetkbwbfbf .gt_column_spanner_outer:first-child {
    padding-left: 0;
  }

  #jetkbwbfbf .gt_column_spanner_outer:last-child {
    padding-right: 0;
  }

  #jetkbwbfbf .gt_column_spanner {
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

  #jetkbwbfbf .gt_group_heading {
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

  #jetkbwbfbf .gt_empty_group_heading {
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

  #jetkbwbfbf .gt_from_md > :first-child {
    margin-top: 0;
  }

  #jetkbwbfbf .gt_from_md > :last-child {
    margin-bottom: 0;
  }

  #jetkbwbfbf .gt_row {
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

  #jetkbwbfbf .gt_stub {
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

  #jetkbwbfbf .gt_stub_row_group {
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

  #jetkbwbfbf .gt_row_group_first td {
    border-top-width: 2px;
  }

  #jetkbwbfbf .gt_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #jetkbwbfbf .gt_first_summary_row {
    border-top-style: solid;
    border-top-color: #D3D3D3;
  }

  #jetkbwbfbf .gt_first_summary_row.thick {
    border-top-width: 2px;
  }

  #jetkbwbfbf .gt_last_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
  }

  #jetkbwbfbf .gt_grand_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #jetkbwbfbf .gt_first_grand_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-top-style: double;
    border-top-width: 6px;
    border-top-color: #D3D3D3;
  }

  #jetkbwbfbf .gt_striped {
    background-color: rgba(128, 128, 128, 0.05);
  }

  #jetkbwbfbf .gt_table_body {
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #D3D3D3;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #jetkbwbfbf .gt_footnotes {
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

  #jetkbwbfbf .gt_footnote {
    margin: 0px;
    font-size: 90%;
    padding-left: 4px;
    padding-right: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #jetkbwbfbf .gt_sourcenotes {
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

  #jetkbwbfbf .gt_sourcenote {
    font-size: 90%;
    padding-top: 4px;
    padding-bottom: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #jetkbwbfbf .gt_left {
    text-align: left;
  }

  #jetkbwbfbf .gt_center {
    text-align: center;
  }

  #jetkbwbfbf .gt_right {
    text-align: right;
    font-variant-numeric: tabular-nums;
  }

  #jetkbwbfbf .gt_font_normal {
    font-weight: normal;
  }

  #jetkbwbfbf .gt_font_bold {
    font-weight: bold;
  }

  #jetkbwbfbf .gt_font_italic {
    font-style: italic;
  }

  #jetkbwbfbf .gt_super {
    font-size: 65%;
  }

  #jetkbwbfbf .gt_footnote_marks {
    font-style: italic;
    font-weight: normal;
    font-size: 75%;
    vertical-align: 0.4em;
  }

  #jetkbwbfbf .gt_asterisk {
    font-size: 100%;
    vertical-align: 0;
  }

  #jetkbwbfbf .gt_indent_1 {
    text-indent: 5px;
  }

  #jetkbwbfbf .gt_indent_2 {
    text-indent: 10px;
  }

  #jetkbwbfbf .gt_indent_3 {
    text-indent: 15px;
  }

  #jetkbwbfbf .gt_indent_4 {
    text-indent: 20px;
  }

  #jetkbwbfbf .gt_indent_5 {
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

  <div id="xjtrxxfouy" style="padding-left:0px;padding-right:0px;padding-top:10px;padding-bottom:10px;overflow-x:auto;overflow-y:auto;width:auto;height:auto;">
  <style>html {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, 'Helvetica Neue', 'Fira Sans', 'Droid Sans', Arial, sans-serif;
  }

  #xjtrxxfouy .gt_table {
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

  #xjtrxxfouy .gt_heading {
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

  #xjtrxxfouy .gt_caption {
    padding-top: 4px;
    padding-bottom: 4px;
  }

  #xjtrxxfouy .gt_title {
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

  #xjtrxxfouy .gt_subtitle {
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

  #xjtrxxfouy .gt_bottom_border {
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #xjtrxxfouy .gt_col_headings {
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

  #xjtrxxfouy .gt_col_heading {
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

  #xjtrxxfouy .gt_column_spanner_outer {
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

  #xjtrxxfouy .gt_column_spanner_outer:first-child {
    padding-left: 0;
  }

  #xjtrxxfouy .gt_column_spanner_outer:last-child {
    padding-right: 0;
  }

  #xjtrxxfouy .gt_column_spanner {
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

  #xjtrxxfouy .gt_group_heading {
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

  #xjtrxxfouy .gt_empty_group_heading {
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

  #xjtrxxfouy .gt_from_md > :first-child {
    margin-top: 0;
  }

  #xjtrxxfouy .gt_from_md > :last-child {
    margin-bottom: 0;
  }

  #xjtrxxfouy .gt_row {
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

  #xjtrxxfouy .gt_stub {
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

  #xjtrxxfouy .gt_stub_row_group {
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

  #xjtrxxfouy .gt_row_group_first td {
    border-top-width: 2px;
  }

  #xjtrxxfouy .gt_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #xjtrxxfouy .gt_first_summary_row {
    border-top-style: solid;
    border-top-color: #D3D3D3;
  }

  #xjtrxxfouy .gt_first_summary_row.thick {
    border-top-width: 2px;
  }

  #xjtrxxfouy .gt_last_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #D3D3D3;
  }

  #xjtrxxfouy .gt_grand_summary_row {
    color: #333333;
    background-color: #FFFFFF;
    text-transform: inherit;
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #xjtrxxfouy .gt_first_grand_summary_row {
    padding-top: 8px;
    padding-bottom: 8px;
    padding-left: 5px;
    padding-right: 5px;
    border-top-style: double;
    border-top-width: 6px;
    border-top-color: #D3D3D3;
  }

  #xjtrxxfouy .gt_striped {
    background-color: rgba(128, 128, 128, 0.05);
  }

  #xjtrxxfouy .gt_table_body {
    border-top-style: solid;
    border-top-width: 2px;
    border-top-color: #D3D3D3;
    border-bottom-style: solid;
    border-bottom-width: 2px;
    border-bottom-color: #000000;
  }

  #xjtrxxfouy .gt_footnotes {
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

  #xjtrxxfouy .gt_footnote {
    margin: 0px;
    font-size: 90%;
    padding-left: 4px;
    padding-right: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #xjtrxxfouy .gt_sourcenotes {
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

  #xjtrxxfouy .gt_sourcenote {
    font-size: 90%;
    padding-top: 4px;
    padding-bottom: 4px;
    padding-left: 5px;
    padding-right: 5px;
  }

  #xjtrxxfouy .gt_left {
    text-align: left;
  }

  #xjtrxxfouy .gt_center {
    text-align: center;
  }

  #xjtrxxfouy .gt_right {
    text-align: right;
    font-variant-numeric: tabular-nums;
  }

  #xjtrxxfouy .gt_font_normal {
    font-weight: normal;
  }

  #xjtrxxfouy .gt_font_bold {
    font-weight: bold;
  }

  #xjtrxxfouy .gt_font_italic {
    font-style: italic;
  }

  #xjtrxxfouy .gt_super {
    font-size: 65%;
  }

  #xjtrxxfouy .gt_footnote_marks {
    font-style: italic;
    font-weight: normal;
    font-size: 75%;
    vertical-align: 0.4em;
  }

  #xjtrxxfouy .gt_asterisk {
    font-size: 100%;
    vertical-align: 0;
  }

  #xjtrxxfouy .gt_indent_1 {
    text-indent: 5px;
  }

  #xjtrxxfouy .gt_indent_2 {
    text-indent: 10px;
  }

  #xjtrxxfouy .gt_indent_3 {
    text-indent: 15px;
  }

  #xjtrxxfouy .gt_indent_4 {
    text-indent: 20px;
  }

  #xjtrxxfouy .gt_indent_5 {
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
