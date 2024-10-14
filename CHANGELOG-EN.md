# 1.2.0

## Fireworks.

* [Feature] Add entry to GitHub release repository. (It's time to ask for stars and watches)
* [Feature] The close function of the main window tab, on the basis of v1.1.0, supports closing the right side and closing other tabs.
* [Feature] Add code completion function when writing scripts for queries.
* [Feature] When writing query scripts, automatically prompt the use of functions involved in code completion, and support direct jump to the official website of the .database product to view the documentation.
* [Feature] When writing query scripts, support right-click menu to execute scripts.
* [Feature] When writing query scripts, support multi-line quick comment `Ctrl+/`.
* [Feature] When writing query scripts, support code search function `Ctrl+F`.
* [Feature] When writing query scripts, ... (For more shortcut key functions, please refer to [reqable/re-editor](https://github.com/reqable/re-editor)).
* [Operation Habit Change] The shortcut key `Ctrl+R` for the query function `Run` is not available, changed to `Alt+R`.
* [Operation Habit Change] The shortcut key for the query function `Format` is changed to `Alt+L`.
* [Operation Habit Change] Cancel the shortcut key `Alt+F` to open the file menu.
* [Optimization] Refactor the code editor to improve the overall performance when writing query scripts, and introduce many of the above functions.
* [Optimization] Unified fonts of different components, using [Ali Pu Hui Ti].
* [Optimization] The timeliness of tree structure update after navigation tree node operation.
* [Optimization] The style problem of the `delete` button is marked with a dangerous color.
* [Optimization] Append directionality to graph visualization.
* [Optimization] In the graph visualization, the starting and ending points of the edge are set in the center of the node to improve the visual experience.
* [Fix] Overlapping problem of task nodes in execution plan visualization.
* [Fix] Query file renaming, file name suffix causes the loss of navigation tree nodes.
* [Fix] After deleting the schema navigation tree element, the opened tab is not removed.
* [Fix] Fixed the error caused by adding a connection using the default connection.
* [Fix] The problem of incorrect page number and serial number in the query result table.
* [Fix] The problem that the desc space syntax is not recognized.

# 1.1.0

## Autumn.

* [Feature] Visualization supports configuring the field used for node names. Support node color configuration.
* [Feature] In the data table view of tags and relationships, support switching to the graph visualization view.
* [Feature] The paging loading mode of the data table is changed to use the paging button loading method.
* [Feature] tag, edge data values can be directly modified in the table.
* [Feature] Comments support modification.
* [Feature] Query files support opening in the resource manager.
* [Feature] Append the main area of the data source, support adding hosts.
* [Feature] Trial function added to all platforms.
* [Feature] Support quickly closing multiple tabs.
* [Feature] Fixed the problem that the table data was not updated in time when running the script.
* [Feature] Feedback module adds condition filtering function.
* [Feature] In the data table, support deleting a single tag from a multi-tag node.
* [Optimization] Beautify the graph visualization component and compatible with light theme.
* [Optimization] Modify the login interface, remove the login video, and compress the installation package size.
* [Optimization] Optimize the selection experience of table cells.
* [Optimization] Avoid the problem of page refresh when switching tabs.
* [Optimization] Avoid secondary queries when refreshing the interface.
* [Fix] Feedback module, when it is not your own comment, do not display "...".
* [Fix] Fixed the problem that the progress bar of other tabs was not loaded when closing the tag page.
* [Fix] Data update problem of long text containing line breaks `\n`.
* [Fix] Some multi-tag nodes are displayed incorrectly in the table data.
* [Fix] Solve the problem that empty values and no tags cannot be distinguished when there are multiple tags on the node.
* [Fix] The problem of importing unsupported time types.
* [Fix] The column name of the return value cannot be Chinese.
* [Fix] After editing the point-edge schema, the table data refreshes without corresponding changes.
* [Fix] Fixed the problem of data loss caused by renaming fields. (No longer support renaming).
* [Fix] The problem that tags, relationships, and query files cannot be opened.
* [Fix] Check the privacy policy and terms of service when using the trial function.
* [Fix] Fixed the problem that the query file was renamed and the parameters were not synchronized.
* [Document] Add an explanation about commercial licenses.

# 1.0.0-beta

## Sprout.

* [Feature] The graph data display supports using a table with multi-dimensional headers.
* [Feature] Integrated graph visualization plug-in, and support graph visualization when writing queries.
* [Feature] Conveniently operate and manage Schema using the navigation tree.
* [Feature] Path format data visualization.
* [Feature] Subgraph data uses a pop-up embedded table triggered by a cell in the table.
* [Feature] Support data import using CSV.
* [Feature] Support quickly creating Schema with CSV headers.
* [Feature] Support adding, deleting, modifying, and querying data for a single table (tag table, relationship table).
* [Feature] Support individual users to use WeChat payment to become our personal sponsor.
* ...