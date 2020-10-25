# Common Terms & Definitions

<table>
  <thead>
    <tr>
      <th style="text-align:left">Term</th>
      <th style="text-align:left">Definition</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <p></p>
        <p>Slug</p>
      </td>
      <td style="text-align:left">a slug is a human readable identifier that is used to reference a specific
        object in a system. Slugs must be unique and can never change once they
        are created. Panoramic makes use of slugs in many areas of the system in
        order to reference certain tables in your data warehouse or certain columns
        in your tables.</td>
    </tr>
    <tr>
      <td style="text-align:left">Tables</td>
      <td style="text-align:left">will be used to refer to any reference-able storage of data in your database
        or data warehouse. This could include tables, views or materialized views
        depending on the warehouse</td>
    </tr>
    <tr>
      <td style="text-align:left">Model</td>
      <td style="text-align:left">A Pano-specific metadata file that points to a single data table and is
        used to describe what data is in the table and how it should be used.</td>
    </tr>
    <tr>
      <td style="text-align:left">Transformation</td>
      <td style="text-align:left">The process of applying business logic to a set of data to convert the
        data into a more useful output for the user or company</td>
    </tr>
    <tr>
      <td style="text-align:left">Dataframe</td>
      <td style="text-align:left">The output of a transformation process, this is a single table of data
        that can be visualized or shared</td>
    </tr>
    <tr>
      <td style="text-align:left">CLI</td>
      <td style="text-align:left">Command line interface - a package that can be installed on your local
        computer to streamline connection to and interaction with the panoramic
        system, this CLI provides common and useful functions that can be used
        to automate the data mapping and transformation process</td>
    </tr>
    <tr>
      <td style="text-align:left">IDB</td>
      <td style="text-align:left">Insight-Driven Business</td>
    </tr>
    <tr>
      <td style="text-align:left">Field</td>
      <td style="text-align:left">Any term defined in your business glossary, this could include dimensions
        or metrics, mapped to dataset or derived from a custom calculation</td>
    </tr>
    <tr>
      <td style="text-align:left">Dataset</td>
      <td style="text-align:left">A grouping of one or more tables that an implicit relationship between
        them, usually all from the same API or data provider. All entity IDs within
        a dataset should be unique.</td>
    </tr>
    <tr>
      <td style="text-align:left">ERD</td>
      <td style="text-align:left">Entity Relationship Diagram - essentially a technical &quot;map&quot;
        of your data showing what information is stored in each table and how you
        can form relations between multiple tables for more complex analysis</td>
    </tr>
    <tr>
      <td style="text-align:left">Cache</td>
      <td style="text-align:left">A pre-assembled dataframe that could be created manually or by the system,
        caches are used to help speed up analytical query times by doing the heavy
        processing in advance</td>
    </tr>
  </tbody>
</table>

