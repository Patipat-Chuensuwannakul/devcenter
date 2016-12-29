DataStax DevCenter is a free visual query tool for developers and administrators 
for creating and running Cassandra Query Language (CQL) queries and commands 
against Apache Cassandra™ and DataStax Enterprise.


## Installing/Running

After unpacking the downloaded archive, you'll find a platform specific executable 
(`DevCenter.exe` or `DevCenter.app`) in the `devcenter` folder. Simply run the executable to launch DevCenter.

_Note_: even if packaged as a self-contained Eclipse RCP-based app, DevCenter requires that java be installed on your system and present in your application path.


## What is new in DataStax DevCenter 1.6.0
1. DSE Search Support
    * Automatic routing of Solr queries to Solr node on execution
        * Aware of DSE nodes and their workload
    * String and JSON query formats
    * Query parameter name and type checking
    * Separate grouping in Schema View for Search Indices
    * Validations
    * Content Assist
    * Code Snippets (Templates)
    * Solr REST to CQL conversion
2. Export Keyspace
3. Support for large result sets
    * Result Set Paging
    * LIMIT keyword no longer appended to SELECT statements (C* 2.0+)
    * Export results to File (CSV or Insert statements)
4. Misc
    * Customize format of Timestamp date and timezone in results 
        * devcenter.date.format=yyyy-MM-dd' 'HH:mm:ssZ
        * devcenter.timezone.id=GMT
    * Customize format of Numeric values in results
        * devcenter.number.format=#,##0.###
    * Support latest time conversion functions
        * toDate, toTimestamp, and toUnixTimestamp
        * deprecated use of dateOf and unixTimestampOf
        * typeAsBlob and blobAsType for smallint, tinyint, date and time data types
    * Validation support for DSE In-Memory tables
    * Additional metrics
        * Cassandra version
        * DSE version and workload
        

## What is new in DataStax DevCenter 1.5.0
1. Support for Cassandra 3.0 CQL features:
    * New, Edit, Clone, and Drop Materialized View Wizards 
    * Multiple secondary indexes
    * Syntax highlighting, code snippets and code assist support for materialized views in the CQL editor
2. Schema Navigator improvements:
    * Materialized View nodes are displayed both under their corresponding keyspace and also under their base table
    * Maintains the state of expanded nodes and also the position on a refresh
    * Displays only those schema elements supported by the version of Cassandra in the cluster
3. Drop Schema objects:
    * Added wizards for dropping User-defined Functions and Aggregates
    * The drop action checks for dependent objects (for example, dropping a table checks for materialized views, dropping a User-defined type checks for table and User-defined types, dropping a User-defined function checks for User-defined aggregates)
4. Improved timestamp formatting used in the Query Results and Detailed Results views; the new format is `yyyy-MM-dd hh:mm:ssZ`
5. Editor and Wizard support in Cassandra 3.0 for new compression options `class` and `chunk_length_in_kb`, and for `crc_check_chance` as a table-level property.
6. Ability to enable or disable the Query Trace feature
7. Improved content assist proposals for caching, compaction, compressions and clustering properties for ATLER TABLE statements
8. Authentication against DataStax Enterprise clusters configured to use LDAP has been tested with the following LDAP providers: OpenLDAP, OracleLDAP, WinAD08, or WinAD12
9. Help links in wizards use the underlying connection details to link to the version-specific documentation pages


## What is new in DataStax DevCenter 1.4.1
1. Improved content assist and validation for `DROP FUNCTION` statement
2. Improved Index name validation for Cassandra 1.2.x and 2.0.x
3. New usage data metrics: DevCenter version, Java version, and OS version

## What is new in DataStax DevCenter 1.4.0
1. Support for Cassandra 2.2.0 CQL features:
    * User Defined Function / Aggregates (CASSANDRA-7395) including complete content assist and validation
    * JSON Syntax for CQL (CASSANDRA-7970) for both INSERT and SELECT statements
    * Role-base authentication (CASSANDRA-7653)
2. New / Edit Index and User Defined Type Wizards, bringing the same experience as for Table and Keyspace creation and modification.
3. Details view for results, letting the user see all the information related to the currently selected cell.
4. Automatic update check, which trigger a popup at startup if a new version is available

## What is new in DataStax DevCenter 1.3.1
1. Support for Cassandra 2.1.3 CQL features:
    * Frozen collections (CASSANDRA-7859) including nested collections and `FULL` collection indexes.
    * Inclusion of `IF EXISTS` for `UPDATE` statements (CASSANDRA-8610)
2. Editor and wizard support for the `DateTieredCompactionStrategy`
3. Additional table options available in the Create and Edit Table wizard: `default_time_to_live`, `gc_grace_seconds`, `index_interval`, `min_index_interval`, `max_index_interval`,`memtable_flush_period_in_ms`, `populate_io_cache_on_flush`, and `speculative_retry`

## What is new in DataStax DevCenter 1.3.0

1. Execute highlighted statements, whenever the user select entirely or partially one or several CQL statements only them will be executed
2. New / Edit Table Wizards to make it easier to create or modify tables in Cassandra without having to type the whole CQL statement
3. New / Edit Keyspace Wizards that brings the same experience but for keyspaces
4. A new Feedback dialog, to allow feedbacks to be sent directly within DevCenter. 

## What is new in DataStax DevCenter 1.2.1

1. Prevent execution of erroneous/incorrect CQL scripts (DEVC-447)
2. Results tab: "Copy as INSERT" now supports collections containing User-defined Types (UDT's) and Tuples (DEVC-420)
3. Fix issue on Mac OS/X Yosemite causing first row of results and query trace table to be hidden (DEVC-442)
4. Fix NPE appearing in log file on some content assist actions (DEVC-449)

## What is new in DataStax DevCenter 1.2.0

1. Full support for Cassandra 2.1, including User-defined Types (UDT's) and Tuples, for which DevCenter now provides syntax highlighting, validation, content assist and code snippets. Also, the Schema Explorer view now displays User-defined Types (UDT's)
2. A new Query Trace tab, located next to the Results tab, that displays detailed trace event data for the last executed query to aid in understanding query execution and performance
3. An improved Connection wizard for creating and managing Cassandra connections

## What is new in DataStax DevCenter 1.1.1

1. Fixed using mixed case keyspace names with the "in keyspace:" combo box (DEVC-229 and DEVC-230)
2. Added the example CQL scripts directory that was missing from 1.1.0
3. Added a comment to the last query in examples/videodb-sample-queries.cql to clarify that this query contains and intentional error (DEVC-227)
4. Fixed the editor not recognizing clustering keys in the ORDER BY clause if the CREATE TABLE statement is not contained in the same script as the query (DEVC-226)
5. Added application icon to the Windows taskbar (DEVC-237)
6. Fixed template proposals not working if the editor is empty (DEVC-238)
7. Fixed CREATE TRIGGER and DROP TRIGGER being proposed in all contexts (DEVC-239)

## What is new in DataStax DevCenter 1.1.0

1. Support for Apache Cassandra 2.0.x and DataStax Enterprise 4.0.x (lightweight transactions syntax, `static` columns, `uuid()`, `'now'`, etc.)
2. New and improved validation and code assist rules
3. Option to use a default keyspace for running a script
4. Option to set the max number of rows to be returned by a statement
5. Copy selected or all results as CSV or CQL inserts
6. Option to enabled SSL connection
7. Fresh new look & feel

## Features in DataStax DevCenter 1.0

1. A smart CQL editor that provides syntax highlighting, code auto-completion (both keyword and snippet), 
   and real-time script validation against the current connection.
2. Schema explorer view for browsing the keyspaces, tables, and other database objects
3. Outline view for allowing quick navigating long CQL scripts
4. Configuring connections to Cassandra or DataStax Enterprise clusters requiring authorization.


## Connecting to a Cassandra or DSE cluster

To configure a connection to a Cassandra cluster, use the top left Connections panel. 
Enter a name for the connection and the IP(s) of the Cassandra node(s) to connect to. 
If the cluster requires authentication, the wizard also allows entering the username and password. The wizard also allows enabling SSL connections.

_Note_: In case DevCenter is not able to connect to the Cassandra cluster please check these 
[connection requirements](https://github.com/datastax/java-driver/wiki/Connection-requirements).
 

## Running CQL scripts
 
Enter CQL commands in a DevCenter query editor/panel, select a configured connection and press the Run button. 
DevCenter uses a tabbed interface that allows you to have multiple query editors open at the same time. 
Simply click on the New SQL Script button in the CQL Scripts pane to create additional query editors.

## Useful shortcuts

### General

*   `Cmd` + `N` (Mac) / `Ctrl` + `N` : New resource wizard
*   `Cmd` + `Shift` + `N` (Mac) / `Ctrl` + `Shift` + `N` : New CQL script
*   `Cmd` + `Shift` + `Option` + `N` (Mac) / `Ctrl` + `Shift` + `Alt` + `N` : New Connection
*   `Cmd` + `Shift` + `Option` + `K` (Mac) / `Ctrl` + `Shift` + `Alt` + `K` : New Keyspace
*   `Cmd` + `Shift` + `Option` + `T` (Mac) / `Ctrl` + `Shift` + `Alt` + `T` : New Table
*   `Cmd` + `Shift` + `Option` + `I` (Mac) / `Ctrl` + `Shift` + `Alt` + `I` : New Index
*   `Cmd` + `Shift` + `Option` + `U` (Mac) / `Ctrl` + `Shift` + `Alt` + `U` : New User Defined Type
*   `Cmd` + `Shift` + `Option` + `V` (Mac) / `Ctrl` + `Shift` + `Alt` + `V` : New Materialized View

### Editing / Running CQL scripts

*   `Alt` + `F11` : Run current CQL script/highlighted statement(s)
*   `Ctrl` + `Space` : Bring up the auto-completion popup
*   `Cmd` + `1` (Mac) / `Ctrl` + `1` : Bring up the quick fixes popup
*   `Cmd` + `.` (Mac) / `Ctrl` + `.` : Jump to next warning/error
*   `Cmd` + `Shift` + `.` (Mac) / `Ctrl` + `,` : Jump to previous warning/error
*   `Cmd` + `Shift` + `F` (Mac) / `Ctrl` + `Shift` + `F` : Format code

### Connections Panel

*   `Cmd` + `F3` (Mac) / `Ctrl` + `F3` : Open selected connection(s)
*   `Cmd` + `F4` (Mac) / `Ctrl` + `F4` : Close selected connection(s)
*   `Cmd` + `Shift` + `D` (Mac) / `Ctrl` + `Shift` + `D` : Clone selected connection(s)
*   `DEL` : Delete selected connection(s)
*   `Cmd` + `I` (Mac) / `Alt` + `Return` : Edit selected connection properties 

### CQL Scripts Panel

*   `Cmd` + `F3` (Mac) / `Ctrl` + `F3` : Open selected script(s)
*   `DEL` : Delete selected script(s)
*   `Cmd` + `I` (Mac) / `Alt` + `Return` : Edit selected script properties 
 
## Sample scripts

In the folder `examples` you can find some CQL scripts that you can use to get started with. 
They provide a complete example of setting up a new keyspace and some tables, inserting data, and 
running various queries against the data.

## Supported versions

DataStax DevCenter 1.5.0 can be used with clusters running:

- Apache Cassandra 3.0.x
- Apache Cassandra 2.2.x
- Apache Cassandra 2.1.x
- Apache Cassandra 2.0.x
- Apache Cassandra 1.2.x
- DataStax Enterprise 4.8.x
- DataStax Enterprise 4.7.x
- DataStax Enterprise 4.6.x
- DataStax Enterprise 4.5.x
- DataStax Enterprise 4.0.x
- DataStax Enterprise 3.2.x
- DataStax Enterprise 3.1.x

## FAQ

Q: **Why does DevCenter on Mac OS/X need Java 6?**

A: When launching DevCenter on Mac OS/X, you might see an error message stating: "To open 'DevCenter' you need to install the legacy Java SE 6 runtime.  Click 'More Info...' to visit the legacy Java SE 6 download website". Although DevCenter is compatible with any recent Java version, Mac OS/X might force you to use Java 6. If this happens, simply follow the link in the message and install Java 6.

Q: **Why am I seeing the “Failed to load the JNI shared library" error when starting DevCenter?**

A: It's likely to be because you're using a 32bits app on a 64bits jvm or conversely. See http://stackoverflow.com/questions/7352493/failed-to-load-the-jni-shared-library-jdk for more details.

Q: **Why aren't all my database objects showing up in the auto-completion popup?**

A: To retrieve an up to date view of the database schema, DevCenter requires an active connection to the cluster, so if you are working offline, only the database objects defined in the
current script will be available for auto-completion.

Q: **Why isn't the Detailed Results View updated when a new Results table cell is selected?**

A: This is a known issue using VNC Viewer to connect to a virtual machine running DevCenter. Connecting using the VMWare console does not have this problem.

Q: **Is there any way to disable Query Tracing?**

A: By default, DevCenter enables query tracing only for the last query executed in a script. A system property can be used to control this by adding the following like to the DevCenter `config.ini` file:
`devcenter.querytrace.enabled=false`

The `config.ini` file is located in:

- Mac: `<DevCenter_Home>/configuration`
- Linux: `<DevCenter_Home>/configuration`
- Windows: `<DevCenter_Home>/configuration`

Q: **Does DevCenter allow connection to a DSE cluster configured with LDAP authentication?**

A: Yes, DevCenter has been tested to be able to connect to a DSE cluster configured with OpenLDAP, OracleLDAP, WinAD08 and WinAD12.

Q: **I just got "an internal error occurred during Xtext validation. Java heap space" dialog. What can I do about it?**

A: Increase the JVM MaxHeapSize by adding `-Xmx512m` or `-Xmx1024m` to the `DevCenter.ini` file The `DevCenter.ini` file is located in:

- Mac: `<DevCenter_Home>/DevCenter.app/Contents/MacOS`
- Linux: `<DevCenter_Home>`
- Windows: `<DevCenter_Home>`

## Feedback

We need your help in improving DevCenter and also prioritizing the features for upcoming milestone releases. 
Please send us all your ideas, bug reports, and feature requests at <devcenter-feedback@datastax.com>.


## License

By downloading and using DevCenter, you agree that your access to and use of DevCenter is governed by the terms applicable to 
Licensed Software under a “No-Fee" or "Trial" license under the DataStax End User General Terms 
(accessible through the link or directly at <http://www.datastax.com/terms>) provided, 
however that you may use the Licensed Software in production, not just for non-production evaluation purposes. 

