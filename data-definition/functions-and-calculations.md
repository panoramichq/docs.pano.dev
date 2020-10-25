# Functions & Calculations

## Row-Level Transformation Functions

Transformation functions only affect a single row of data and do not require data from multiple rows in order to execute correctly. Any functions added as transformation functions are fundamentally “safe” to the system and can be applied either in the model transformation layer or the field calculation layer. Since the application of transformation functions can create new dimensions or groupings of values, all transformation functions are applied prior to aggregation in the Pano query service.

A Field must be created before it can be referenced in a calculation. Currently, calculations referencing other fields can only go six layers deep, meaning there cannot be more than five degrees of abstraction between the final Field and the original mapped fields it references.

#### Text Functions

<table>
  <thead>
    <tr>
      <th style="text-align:left">Function</th>
      <th style="text-align:left">Input</th>
      <th style="text-align:left">Output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">PARSE( {DIMENSION}, DELIMITER_CHARACTER, INDEX )</td>
      <td style="text-align:left">
        <p>Single dimension field</p>
        <p>Delimiter Character that will be used to split the text into chunks</p>
        <p>Integer Index referencing which chunk to output from the function</p>
      </td>
      <td style="text-align:left">
        <p>Output will be one dimension value, not an array or multiple</p>
        <p>NULL value if list of items is too short</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">TRIM( {DIMENSION} )</td>
      <td style="text-align:left">Single text dimension field</td>
      <td style="text-align:left">Single text dimension field stripped of leading and trailing whitespace
        (spaces, tabs and newlines)</td>
    </tr>
    <tr>
      <td style="text-align:left">UPPER( {DIMENSION} )</td>
      <td style="text-align:left">Single text dimension field</td>
      <td style="text-align:left">Single text dimension field with case of the entire string converted from
        existing to upper case</td>
    </tr>
    <tr>
      <td style="text-align:left">LOWER( {DIMENSION} )</td>
      <td style="text-align:left">Single text dimension field</td>
      <td style="text-align:left">Single text dimension field with case of the entire string converted from
        existing to lower case</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>CONCAT( {FIELD}, [{FIELD | CONSTANT, ETC]</p>
        <p>)</p>
      </td>
      <td style="text-align:left">A list of one or more fields and/or user-defined constants, separated
        by commas</td>
      <td style="text-align:left">Single text dimension field with all values appended together in order</td>
    </tr>
  </tbody>
</table>

#### Conditional Functions

Conditional functions can be added into transformations in either the field “calculation” or the model “sql\_ref”.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Function</th>
      <th style="text-align:left">Input</th>
      <th style="text-align:left">Output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p>IFF( LOGIC_STATEMENT, {FIELD},</p>
        <p>[{FIELD}]</p>
        <p>)</p>
      </td>
      <td style="text-align:left">
        <p>Logical Statement that evaluates to TRUE or FALSE</p>
        <p>Desired output if TRUE</p>
        <p>Desired output if FALSE (Default NULL)</p>
      </td>
      <td style="text-align:left">Single field that matches the outcome of the logical statement. The data
        type of the output will match the field</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>IFS( LOGIC_STATEMENT,</p>
        <p>{FIELD},</p>
        <p>LOGIC_STATEMENT,</p>
        <p>{FIELD}, ...</p>
        <p>[{FIELD}]</p>
        <p>)</p>
      </td>
      <td style="text-align:left">
        <p>Multiple Logic statements listed together and evaluated in order.</p>
        <p>Each Statement is followed by the desired field output if TRUE.</p>
        <p>Last field is the output if all are FALSE (default NULL)</p>
      </td>
      <td style="text-align:left">Single field that matches the outcome of the logical statement. The data
        type of the output will match the field</td>
    </tr>
    <tr>
      <td style="text-align:left">(<em>PARENTHESES</em>)</td>
      <td style="text-align:left">Add parentheses into any calculation to dictate order of operations</td>
      <td
      style="text-align:left">-NA</td>
    </tr>
    <tr>
      <td style="text-align:left">
        <p>CONTAINS(</p>
        <p>{FIELD}, MATCH_VALUE, [MATCH_VALUE, ...]</p>
        <p>)</p>
      </td>
      <td style="text-align:left">Single field to search User-defined values to search the string for</td>
      <td
      style="text-align:left">Boolean TRUE or FALSE if any of the match_values exist in the field</td>
    </tr>
  </tbody>
</table>

#### Logic Statement Operators

| Operator | Name |
| :--- | :--- |
| IS NULL | IS NULL |
| IS NOT NULL | IS NOT NULL |
| && | AND |
| \|\| | OR |
| NOT | NOT |
| = | EQUAL TO |
| != | NOT EQUAL TO |
| &lt;&gt; | NOT EQUAL TO |
| &gt; | GREATER THAN |
| &gt;= | GREATER THAN OR EQUAL |
| &lt; | LESS THAN |
| &lt;= | LESS THAN OR EQUAL |

#### Algebraic Functions

| Function | Name |
| :--- | :--- |
| + | ADDITION |
| - | SUBTRACTION |
| \* | MULTIPLICATION |
| / | DIVISION |

#### Casting Functions

<table>
  <thead>
    <tr>
      <th style="text-align:left">Function</th>
      <th style="text-align:left">Input</th>
      <th style="text-align:left">Output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">TO_BOOL({FIELD}, [NULLIFY_ERRORS])</td>
      <td style="text-align:left">Single dimension or metric, Boolean flag to define whether to return error
        message or convert errors to NULL values</td>
      <td style="text-align:left">
        <p>Dimension</p>
        <p>&#x201C;True&#x201D; or &#x201C;False&#x201D; values or NULL for errors/unknown</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">TO_DATE({FIELD}, FORMAT_STRING, [NULLIFY_ERRORS])</td>
      <td style="text-align:left">Timestamp or datetime, Boolean flag to define whether to return error
        message or convert errors to NULL values</td>
      <td style="text-align:left">
        <p>Dimension</p>
        <p>A date (without 00:00:00)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">TO_TEXT({field}, [NULLIFY_ERRORS])</td>
      <td style="text-align:left">Any field, Boolean flag to define whether to return error message or convert
        errors to NULL values</td>
      <td style="text-align:left">
        <p>Dimension</p>
        <p>Same value as a string</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">TO_URL({field}, [NULLIFY_ERRORS])</td>
      <td style="text-align:left">Text dimension, Boolean flag to define whether to return error message
        or convert errors to NULL values</td>
      <td style="text-align:left">
        <p>Dimension</p>
        <p>Validated URL string that can be rendered accordingly by a UI client</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">TO_NUMBER({field}, [precision - integer, optional, default 0], [NULLIFY_ERRORS])</td>
      <td
      style="text-align:left">dimension or metric, integer for decimal places</td>
        <td style="text-align:left">
          <p>Metric</p>
          <p>formatted with decimal places</p>
        </td>
    </tr>
  </tbody>
</table>

#### Date / Time Functions

<table>
  <thead>
    <tr>
      <th style="text-align:left">Function</th>
      <th style="text-align:left">Input</th>
      <th style="text-align:left">Output</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">CONVERT_TIMEZONE({time_taxon}, {from_timezone}, {to_timezone})</td>
      <td
      style="text-align:left">
        <p>Date_time taxon (2020-05-01 02:00:00) that is aggregated at the hourly
          level or below, this field does not need to include timezone info</p>
        <p>From_timezone:</p>
        <ul>
          <li>A timezone taxon that points to data in the DB that specifies the time
            zone</li>
          <li>Input value matching available, supported timezones</li>
        </ul>
        <p>To_timezone:</p>
        <p>Input value matching available, supported timezones to specify the time
          zone to convert to</p>
        </td>
        <td style="text-align:left">Date/time field shifted to the desired timezone</td>
    </tr>
    <tr>
      <td style="text-align:left">DATE_DIFF( {interval}, {start_time}, {end_time} )</td>
      <td style="text-align:left">
        <p>Start_time - can be a date field or the input &#x201C;current_time&#x201D;</p>
        <ul>
          <li>&#x201C;current_time&#x201D; is a reserved word that resolves to SQL &#x201C;now()&#x201D;</li>
          <li>end_time - can be a date field or the input &#x201C;current_time&#x201D;</li>
          <li>Interval - the units that the user wants the diff to be calculated in,
            one of &#x2018;second&#x2019;, &#x2018;minute&#x2019;, &#x2018;hour&#x2019;,
            &#x2018;day&#x2019;, &#x2018;week&#x2019;, &#x2018;month&#x2019;, &#x2018;year&#x2019;.</li>
        </ul>
      </td>
      <td style="text-align:left">Metric number indicating number of defined intervals between start_time
        and end_time</td>
    </tr>
    <tr>
      <td style="text-align:left">DATE({time_taxon})</td>
      <td style="text-align:left">Reduces granularity of a time field to daily granularity.</td>
      <td style="text-align:left">
        <p>new date/date_time taxon with all values rolled up to the granularity
          defined</p>
        <p>Examples:</p>
        <ul>
          <li>Input: &#x2018;2020/05/22 09:54:23&#x2019;</li>
          <li>&#x2018;day&#x2019; = &#x2018;2020/05/22&#x2019;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">DATE_HOUR({time_taxon})</td>
      <td style="text-align:left">Reduces granularity of a time field to hourly granularity.</td>
      <td style="text-align:left">
        <p>New date/date_time taxon with all values rolled up to the granularity
          defined</p>
        <p>Examples:</p>
        <ul>
          <li>Input: &#x2018;2020/05/22 09:54:23&#x2019;</li>
          <li>&#x2018;hour&#x2019; = &#x2018;2020/05/22 09:00:00&#x2019;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">DATE_WEEK({time_taxon})</td>
      <td style="text-align:left">Reduces granularity of a time field to weekly granularity.</td>
      <td style="text-align:left">
        <p>New date/date_time taxon with all values rolled up to the granularity
          defined</p>
        <p>Examples:</p>
        <ul>
          <li>Input: &#x2018;2020/05/22 09:54:23&#x2019;</li>
          <li>&#x2018;week&#x2019; = &#x2018;2020/05/17&#x2019;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">DATE_MONTH({time_taxon})</td>
      <td style="text-align:left">Reduces granularity of a time taxon to monthly granularity.</td>
      <td style="text-align:left">
        <p>New date/date_time taxon with all values rolled up to the granularity
          defined</p>
        <p>Examples:</p>
        <ul>
          <li>Input: &#x2018;2020/05/22 09:54:23&#x2019;</li>
          <li>&#x2018;month&#x2019; = &#x2018;2020/05/01&#x2019;</li>
        </ul>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">YEAR({time_taxon})</td>
      <td style="text-align:left">Extracts the integer year from a date/time taxon</td>
      <td style="text-align:left">Integer output reflecting the year, ex: 2020</td>
    </tr>
    <tr>
      <td style="text-align:left">MONTH_OF_YEAR({time_taxon})</td>
      <td style="text-align:left">Truncates days, hours, minutes and seconds of a timestamp and returns
        data at a monthly granularity</td>
      <td style="text-align:left">Integer output reflecting the month number of the year (1-12)</td>
    </tr>
    <tr>
      <td style="text-align:left">WEEK_OF_YEAR({time_taxon})</td>
      <td style="text-align:left">Combines all timestamps within a given week into one record that is snapped
        to the first Sunday of each week</td>
      <td style="text-align:left">Integer output reflecting the ISO week of the year (1-53)</td>
    </tr>
    <tr>
      <td style="text-align:left">DAY_OF_WEEK({time_taxon})</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Returns the named day of week associated with the date_time value (Mon,
        Tues, Wed, etc)</td>
    </tr>
    <tr>
      <td style="text-align:left">HOUR_OF_DAY({time_taxon})</td>
      <td style="text-align:left"></td>
      <td style="text-align:left">Returns the hour of day associated with the date_time value (0-23)</td>
    </tr>
  </tbody>
</table>

## Aggregation Functions

**The following functions are only available in aggregation type and are not allowed in field calculations or model transformations**

Aggregation functions are necessary for all mapped metric fields. For example, if I have a column in my database table for "impressions" and I set the aggregation on that field to be SUM\(\), I am telling Pano that any time I ask for "impressions", no matter what dimensions I group by, I will get the SUM\(impressions\) returned in the query results.

An aggregation type is applied only on the first mapped field pointing directly to the data table, all references to that field will inherit the same aggregation type.

#### Standard Metrics

<table>
  <thead>
    <tr>
      <th style="text-align:left">Aggregation</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">SUM( {METRIC} )</td>
      <td style="text-align:left">Single dataset SQL: SUM( {a} )</td>
    </tr>
    <tr>
      <td style="text-align:left">COUNT( {FIELD} )</td>
      <td style="text-align:left">
        <p>Input: 1 dimension or metric</p>
        <p>Output: a count (integer) of the total number of values (including duplicates)
          that appear for that field within the query parameters</p>
        <p>Single dataset SQL: COUNT(DISTINCT {a}, {b}, etc )</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">AVERAGE( {METRIC} )</td>
      <td style="text-align:left">
        <p>The exact metric used for SUM() should also be used in COUNT()</p>
        <p>Single dataset SQL: SUM( {a} ) / COUNT( {a} )</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">AVERAGE_WEIGHTED( {METRIC}, {WEIGHTING_METRIC} )</td>
      <td style="text-align:left">Single dataset SQL: SUM( {a} * {a&#x2019;} ) / SUM( {a&#x2019;}</td>
    </tr>
  </tbody>
</table>

#### Lifetime & Unique

<table>
  <thead>
    <tr>
      <th style="text-align:left">Aggregation</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">COUNT_DISTINCT( {FIELD}, {FIELD}, ETC )</td>
      <td style="text-align:left">
        <p>Input: a list of dimensions and/or metrics from a single dataset</p>
        <p>Output: a count (integer) of the distinct values that appear for the set
          of fields within the query parameters</p>
        <p>Single dataset SQL: COUNT( {a} )</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">FIRST_BY( {FIELD}, {TIME_DIMENSION} )</td>
      <td style="text-align:left">
        <p>All dimensions from data request for the relevant dataset must be passed
          into the PARTITION BY () clause of the function</p>
        <p>Single dataset SQL: FIRST_VALUE( {a} ) OVER (PARTITION BY ( {request_dimensions}
          ) ORDER BY {time_dimension} ASC)</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">LAST_BY( {FIELD}, {TIME_DIMENSION} )</td>
      <td style="text-align:left">
        <p>All dimensions from data request for the relevant dataset must be passed
          into the PARTITION BY () clause of the function</p>
        <p>Single dataset SQL: LAST_VALUE( {a} ) OVER (PARTITION BY ( {request_dimensions}
          ) ORDER BY {time_dimension} ASC)</p>
      </td>
    </tr>
  </tbody>
</table>

#### Date / Time

<table>
  <thead>
    <tr>
      <th style="text-align:left">Aggregation</th>
      <th style="text-align:left">Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">MIN( {TIME_DIMENSION} )</td>
      <td style="text-align:left">
        <p>Description: Function will take one date/datetime value as input and return
          a metric value for the lowest/first date/time for the range within the
          query parameters</p>
        <p>Input: any date or time taxon</p>
        <p>Output: the earliest date in the set, at the same granularity as the input</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">MAX( {TIME_DIMENSION} )</td>
      <td style="text-align:left">
        <p>Description: Function will take one date/datetime value as input and return
          a metric value for the highest/last date/time for the range within the
          query parameters</p>
        <p>Input: any date or time taxon</p>
        <p>Output: the latest date in the set, at the same granularity as the input</p>
      </td>
    </tr>
  </tbody>
</table>

## Special Functions

Special functions are functions created by Pano that do not correlate to any standard SQL functions. These functions have special behaviors that provide useful functionality when querying your data. Special functions are not available in model level “sql\_ref”.

#### Conditional

* ? _Optional_
  * Similar to the NULLIF\(\) and ZEROIFNULL\(\) functions in SQL. This operator is available to add in front of any field in a transformation and signifies to the pano system that the calculation should still execute successfully if the field is not available.
  * A common use case is when you want to create some cross-dataset blended metric, but you want that metric to be available when looking at single-dataset Dataframes as well.
    * E.g. CPC = \(facebook\|spend + ?twitter\|spend\) / \(facebook\|clicks + ?twitter\|clicks\)
    * In this example CPC would be available if you are building a blended Dataframe with both facebook and twitter Datasets, it would also be available if you are building a facebook only Dataframe, since twitter metrics are marked optional. Conversely, CPC would not be available if you build a twitter only dataframe since the formula requires facebook

#### Dimensions

* MERGE\( {DIMENSION}, {DIMENSION}, ETC \)
  * **Merge function allows for Dimension Blending** - the ability to "blend" different dimensions from multiple datasets.
  * Merge function can take multiple dimension fields as inputs
  * You can not include more than one dimension from each dataset
  * The dimensions included can point directly to data or they can be derived but they cannot already include merged dimensions
* OVERRIDE\( {DIMENSION}, LOOKUP\_PATH, FILTER\_UNKNOWNS\)
  * This function allows you to clean your data by overriding existing values with new values that you would like to use. This is very common when labeling technical API enums with presentable names, or standardizing values across datasets so they can be blended reports
  * Input
    * A single dimension field that they would like to use as input values for the override function
    * A path/link/reference to a predefined lookup dataset
    * FILTER\_UNKNOWNS - Boolean flag to strip unmatched values from the response or include the data grouped as “Unknown”



