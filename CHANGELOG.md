# DevCenter Changelog

## 1.6.0

### New Features / Improvements

- DSE Search Support
    * Automatic routing of Solr queries to Solr node on execution
        * Aware of DSE nodes and their workload
    * String and JSON query formats
    * Query parameter name and type checking
    * Separate grouping in Schema View for Search Indices
    * Validations
    * Content Assist
    * Code Snippets (Templates)
    * Solr REST to CQL conversion
- Export Keyspace
- Support for large result sets
    * Result Set Paging
    * LIMIT keyword no longer appended to SELECT statements (C* 2.0+)
    * Export results to File (CSV or Insert statements)
- Misc
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

### Bugs
- Scrolling a very long query trace result might freeze DevCenter
- Special characters should be filtered out from query trace events
- No horizontal scroll bar for query trace table.
- Query trace on linux is not viewable
- No validation error for missing keyspace in 'DROP INDEX' statement.
- No validation error for renaming non primary key column.
- Create Index content assist should not suggest static column.
- Content assist should not propose existing keyspaces in the CREATE KEYSPACE statement.
- Drop dialogs: Unable to drop multiple schema elements from different keyspaces.
- Create Aggregate Content Assist (keyword && with final function): Stype is not suggested.
- Support inequality expressions in UPDATE IF statement
- Drop UDA: Wrong uda dropped in mixed case keyspace/uda scenario.
- No validation error for Create Materialized View without clustering key statement.
- Details View on Win7 and Ubuntu: Timestamp is not split into 2 lines.
- Incorrect timestamp format (12 hour without AM/PM indicator) in Results view
- SELECT COUNT query fails when using solr_query
- Missing duplicate index validation error on CREATE INDEX statement.
- Table element in "Query Trace" view has fixed horizontal size

## 1.5.0

### New Features / Improvements

- Support for Cassandra 3.0 CQL features:
    * New, Edit, Clone, and Drop Materialized View Wizards 
    * Multiple secondary indexes
    * Syntax highlighting, code snippets and code assist support for materialized views in the CQL editor
- Schema Navigator improvements:
    * Materialized View nodes are displayed both under their corresponding keyspace and also under their base table
    * Maintains the state of expanded nodes and also the position on a refresh
    * Displays only those schema elements supported by the version of Cassandra in the cluster
- Drop Schema objects:
    * Added wizards for dropping User-defined Functions and Aggregates
    * The drop action checks for dependent objects (for example, dropping a table checks for materialized views, dropping a User-defined type checks for table and User-defined types, dropping a User-defined function checks for User-defined aggregates)
- Improved timestamp formatting used in the Query Results and Detailed Results views; the new format is `yyyy-MM-dd hh:mm:ssZ`
- Editor and Wizard support in Cassandra 3.0 for new compression options `class` and `chunk_length_in_kb`, and for `crc_check_chance` as a table-level property.
- Ability to enable or disable the Query Trace feature
- Improved content assist proposals for caching, compaction, compressions and clustering properties for ATLER TABLE statements
- Authentication against DataStax Enterprise clusters configured to use LDAP has been tested with the following LDAP providers: OpenLDAP, OracleLDAP, WinAD08, or WinAD12
- Help links in wizards use the underlying connection details to link to the version-specific documentation pages

### Bugs

- Validation error and no content assist proposal for columns that are not part of the primary key or a secondary index when ALLOW FILTERING is used in a SELECT statement
- Clustering order not included when cloning a Table with the Clone Table wizard
- Missing validation check for usage of functions in a Solr query
- Unable to fetch query results larger than 5000 rows
- Missing validation for attempt to index a static column
- Keyword INPUT not allowed as a function parameter name
- Uppercase user-defined type field name caused initialization error and empty Schema View 
- Validation error on State or Final functions without a keyspace name prefix in CREATE AGGREGATE statements. Only Cassandra 2.2.0 allowed a keyspace prefix to State and Final functions.
- Missing validation for `cold_reads_to_omit` compaction option for Cassandra versions 2.2 and higher
- DROP INDEX missing validation for non-existing index if an index of the same name exists in another keyspace with the same name but different case.

## 1.4.1

### New Features / Improvements

- Improved Index name validation for Cassandra 1.2 and 2.0
- Improved content assist and validation for `DROP FUNCTION` statement
- New usage data metrics: DevCenter version, Java version, and OS version

### Bugs

- Error retrieving trace event data prevents display of query results 
- Execution of Solr queries caused error dialog
- Timing issue caused no proposals to display when content assist invoked within 500 milliseconds of the last editor modification

## 1.4.0

### New Features / Improvements

- Support for Cassandra 2.2 CQL features: UDF/UDA, JSON Syntax, Role-based Authentication and new data types
- New Index Wizard
- Edit Index Wizard
- New User Defined Type Wizard
- Edit User Defined Type Wizard
- Automatic Check for Updates
- Detailed view for Results

### Bugs

- TTL/Writetime metadata queries preventing script execution
- Error on execution of some SELECT statements with a UDT literal
- Execution error when running SELECT statement with closed connection
- Improve support for workspace external CQL files
- Saving CQL code from the scratch space to the file can results in errors
- No validation errors when wrong value is specified for columns of type decimal, float and double
- Unable to use 'Allow Filtering'
- Clone table wizard complains about existing FROZEN keyword
- Error for SELECT COUNT and no results for this statement
- Create/Clone Table Wizard: Unable to add a column of type UDT
- Alter table Add column validation marks entire statement with error
- Validate multiple indices on the same column if Cassandra version < 2.2
- Support 'ENTRIES' secondary index on Map column
- New keyspaces aren't always recognized
- 'Drop Keyspace' dialog and 'Drop Table' dialog cannot handle keyspace name with capital letters
- 'Drop' dialogs should be disabled when no keyspace/table/UDT is selected
- UDT field name in double quotes results in schema view being blank
- No suggestion that unquoted udt field name is case insensitive
- No error reported in CQL editor for adding a duplicate column
- Wrong suggestion in quick fix when there is a typo in "IF NOT EXISTS" expression
- Validation should not require all Tuple fields for INSERT or UPDATE statements
- Allow "tuple literal" syntax for INSERT and UPDATE of UDT's

## 1.3.1

### New Features / Improvements

- Support for frozen collections (CASSANDRA-7859) including nested collections and `FULL` collection indexes.
- Inclusion of `IF EXISTS` for `UPDATE` statements (CASSANDRA-8610)
- Editor and wizard support for the `DateTieredCompactionStrategy`
- Additional table options available in the Create and Edit Table wizard: `default_time_to_live`, `gc_grace_seconds`, `index_interval`, `min_index_interval`, `max_index_interval`,`memtable_flush_period_in_ms`, `populate_io_cache_on_flush`, and `speculative_retry`
- Filter white space from username and password fields in the Connection wizard dialog.
- Feedback link in the editor status bar when results are not displayed
- Sets Cassandra 2.1.3 as the default version used for editor validation when there is no open connection.
 
### Bugs
- The "Back" button is now disabled (just like the "Next" button) whenever there's an error in the current page of the Wizard.

## 1.3.0

### New Features / Improvements

- New Table Wizard
- Edit Table Wizard
- New Keyspace Wizard
- Edit Keyspace Wizard
- Feedback Dialog
- Add execution of highlighted statements
- Allow UDT types to be qualified with a Keyspace in CQL grammar

### Bugs

- Schema view now always updated
- Typo in error message "Frozen<> cannot be nested"
- Unknown option values prevents loading of database schema
- Error in SchemaView when no editor active
- Illegal state exception in .metadata/.log upon opening a new script in cql editor
- Schema view pane is not refreshed upon connection change
- Java driver exportAsString missing ';' at end of CREATE TYPE statements
- Additional checks to improve stability when Cassandra version is newer than java driver
- Validation should not require all UDT fields for INSERT or UPDATE statements

## 1.2.1

1. Prevent execution of erroneous/incorrect CQL scripts (DEVC-447)
2. Results tab: "Copy as INSERT" now supports collections containing User-defined Types (UDT's) and Tuples (DEVC-420)
3. Fix issue on Mac OS/X Yosemite causing first row of results and query trace table to be hidden (DEVC-442)
4. Fix NPE appearing in log file on some content assist actions (DEVC-449)

## 1.2.0

### New Features / Improvements
 
- Query tracing view
- Cassandra 2.1 support
- Upgrade to Java Driver 2.1
- Add support for Tuples
- Add support for UDTs
- Add UDTs to the Schema view
- Add content assist for UDTs
- Add scoping and validation for UDTs
- Support new FROZEN CQL keyword for UDT/Tuples
- Add support for secondary indexes on collection column
- Add support for conditional CREATE/DROP USER
- Add optional keyspace to DROP INDEX statement
- View data from UDTs and Tuples in the Results table view
- Add support for task markers in the editor
 
### UX Improvements
 
- New connection wizard
- New property dialog for connections
- Multiple selection for connections and CQL scripts
- New keyboard shortcuts for connections and CQL scripts
- New menu items for connections and CQL scripts
- Double clicking a connection should initiate the connection (not edit it)
- Add clone connection option
 
### Bugs
 
- Cannot connect to cluster using Snappy
- Connection dialog UI issues on Debian 7.5
- Connection name should be required
- Connection dialog does not resize when using Windows scale
- Devcenter not validate CQL script file name
- Should give warning before overwriting CQL script with the same name
- Invalid error "conditional updates are not allowed in batches"
- Invalid error "Missing primary key part xxx"
- Invalid error "mismatched input ..." when using conditional delete
- Quoted strings should skip trailing quote
- The CQL editor loses focus when executing
- Incorrect validation on secondary index of collection column which has mixed case name
- Editor not recognize keyword WITH used in CREATE INDEX statement
- Editor not recognize some schema properties and properties' values
- Check for duplicate property names is case sensitive
- MODIFY keyword not recognized in GRANT/REVOKE statements
- NullPointerException when activate content assist in ALTER TABLE/ALTER TYPE ... ADD
- Incorrect validation on primary key column after being renamed
- Index and trigger are case sensitive
- Copy as CQL does not quote identifiers
- Result table and Copy as CSV/INSERT not quote value of inet type
- Execute Button is hidden when the form's width is not large enough
- ArrayIndexOutOfBoundsException thrown when executing a statement
- DevCenter displays values for empty columns
- Result table unable to display more than 5000 rows which was a valid value for 'with limit' field
- IllegalArgumentException in the log file after opening DevCenter
- Java Heap Space error when saving/or running a large script

## 1.1.1

1. Fixed using mixed case keyspace names with the "in keyspace:" combo box (DEVC-229 and DEVC-230)
2. Added the example CQL scripts directory that was missing from 1.1.0
3. Added a comment to the last query in examples/videodb-sample-queries.cql to clarify that this query contains and intentional error (DEVC-227)
4. Fixed the editor not recognizing clustering keys in the ORDER BY clause if the CREATE TABLE statement is not contained in the same script as the query (DEVC-226)
5. Added application icon to the Windows taskbar (DEVC-237)
6. Fixed template proposals not working if the editor is empty (DEVC-238)
7. Fixed CREATE TRIGGER and DROP TRIGGER being proposed in all contexts (DEVC-239)

## 1.1.0

1. Support for Apache Cassandra 2.0.x and DataStax Enterprise 4.0.x (lightweight transactions syntax, `static` columns, `uuid()`, `'now'`, etc.)
2. New and improved validation and code assist rules
3. Option to use a default keyspace for running a script
4. Option to set the max number of rows to be returned by a statement
5. Copy selected or all results as CSV or CQL inserts
6. Option to enabled SSL connection
7. Fresh new look & feel

## 1.0

1. A smart CQL editor that provides syntax highlighting, code auto-completion (both keyword and snippet), 
   and real-time script validation against the current connection.
2. Schema explorer view for browsing the keyspaces, tables, and other database objects
3. Outline view for allowing quick navigating long CQL scripts
4. Configuring connections to Cassandra or DataStax Enterprise clusters requiring authorization.

