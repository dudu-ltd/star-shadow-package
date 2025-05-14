
# 2.1.0

* [Feature] Support clearing a single table.
* [Optimization] Performance improvement. When visualization is not activated, close unnecessary background operations to avoid CPU usage.
* [Optimization] Optimize the program exit experience.
* [Optimization] Beautify the arrow style of graph visualization.
* [Fix] Fixed the problem that INT64 exceeds half of the maximum length and becomes negative.


# 2.0.1

* [fix] Fixed the problem that the license cannot be set manually.
* [UI] The font of the AI module is consistent with the global one.

# 2.0.0

## Shanqing.

* [Feature] Support defining code templates, supporting different scopes, such as specific graph space, specific data source, global, etc.
* [Feature] Integrated AI large model, default DeepSeek-R1, other models can be configured.
  1. [Feature] Built-in 8 roles, functions include: workflow for creating graphs, modeling, initializing data, index creation, script tuning and repair...
  1. [Feature] Support custom roles, large models, and flat configuration workflows.
  1. [Feature] Support quick call AI in the query area through right-click menu.
  1. [Feature] Support quickly carrying local table structure (optional, default not passed to AI).
  1. [Feature] Support appending data mode in the question (not uploading data, only uploading table association of graph data, default not passed).
  1. [Feature] Conversation content supports SVG rendering.
  1. [Feature] Conversation content, role, model API parameters local storage.

* [Feature] Data migration.
  1. Graph space data overview.
  1. Selected table copy supports partial selection, full selection, and no selection (default is full selection).
  1. When backing up data, the index is backed up synchronously and the index is rebuilt.

* [Feature] Background tasks and notifications.
  1. Optimize the loading method of schema tree, using background tasks for silent loading.
  1. The import function uses the background task list instead of the loading progress ring.
  1. Tasks with calculable endpoints display specific progress percentage.
  1. Establish a notification mechanism for task error messages, viewable through the global interface in the lower right corner.
  1. Task list details display.

* [Feature] Authorization mechanism.
  1. Online user login silently installs temporary authorization code.
  1. Support offline authorization.
  1. [Operation Habit Change] Cancel trial function, change to license method.

* [Operation Habit Change] Cancel the 【Guide】 and 【Tip】 tabs in the far right function area, change to view through the documentation station.
* [Operation Habit Change] The query parameter area is minimized by default.
* [Operation Habit Change] Move the trigger to view Hosts information in the data source to right-click 【Overview】.
* [Operation Habit Change] Move the quick add query button to the main operation area tab.
* [Operation Habit Change] The query area does not enable the execution plan by default.
* [Feature] The selected tab in the main operation area synchronizes selection in the navigation tree.
* [Feature] The tags opened in the main area support synchronously expanding nodes in the navigation tree.
* [Feature] When the program starts, initialize and load the previously opened main page.
* [Feature] The global information of the application adds device number.
* [Feature] The query function implements code completion based on syntax.
* [Feature] When adding edges, you can query points and select them as start and end nodes.
* [Feature] In the tree navigation, right-click the table object to generate NgBatis entity class.
* [Optimization] Further improve the experience of code prompts based on syntax.
* [Optimization] When editing schema, automatically scroll to the bottom when adding attributes.
* [Optimization] Table style optimization, so that 30 rows of data do not overflow the screen.
* [Fix] Fixed the problem of not loading nodes when refreshing data in graph visualization and then triggering neighboring nodes.
* [Fix] Fixed the problem that edge data filtering does not work and point filtering must have an index.
* [Fix] Fixed the problem that the color of the data panel in graph visualization is too light to see clearly.
* [Fix] Use Chinese as the default language.
<!-- * [Fix] Attempt to fix the problem that command+c cannot copy on macOS. -->
* [Fix] Fixed the problem of importing geo field types.
* [Fix] Fixed the problem of geo type display error.
* [Fix] Fixed the problem of schema navigation tree error after deleting and recreating the same name space.
* [Fix] Fixed the problem that vid is int and cannot be imported without setting id value offset.
* [Fix] Fixed the problem that the query area tab page is too many to see the tab content.
* [Fix] Fixed the problem that the query result tab page is too many to see the tab content.
* [Fix] Fixed the problem that edge table names and attributes cannot use Chinese.
* [Fix] Fixed the problem of CSV import type adaptation.
* [Fix] Fixed the problem of displaying the same column with different types in the table.
* [Fix] Fixed the problem of creating tags pop-up error.
* [UI] Optimize the display effect when the main operation area button is out of bounds.
* [UI] Beautify the style of window separator lines.
* [UI] Add icons to the query area log tab.
* [UI] Add a unified close button to some form pop-ups.
* [UI] Adjust the minimum width of the main operation area to 40% limit to 100 pixels.

# 1.3.0

## Candlelight.

* [Feature] Graph visualization supports closing node position movement, and dragging nodes, manually adjusting node position.
* [Feature] Graph visualization supports using field values as node image display.
* [Feature] Graph visualization displays the data node data panel after selecting the node.
* [Feature] Graph visualization supports using table paging to load neighboring nodes when triggering node clicks.
* [Feature] Graph visualization layout supports forward and backward, controlling the loading of neighboring nodes.
* [Feature] Graph visualization layout algorithm supports adjusting layout parameters.
* [Feature] Graph visualization supports controlling the display and hiding of nodes and relationships by node type and edge type.
* [Feature] Add 【Quick Start】 in the lower left corner of the main interface, support creating tags, relationships, and queries in the lower left corner.
* [Feature] Partial log function: user directory/.star_shadow/logs/date.log.
* [Optimization] Improve the performance of closing nodes in the schema navigation.
* [Optimization] When opening the software, the window is automatically maximized.
* [Optimization] Add tag name to the floating data panel of the graph visualization.
* [Optimization] Graph visualization display, text control within 10 characters.
* [Fix] In the graph visualization, when there are many nodes, the entire display area collapses into a black screen.
* [Fix] Fixed the problem that the relationship name contains operators and cannot be opened.
* [Fix] Fixed the internationalization error in the settings page after viewing the license.
* [Fix] Fixed the problem that `!=` is formatted as `=` in the `Format` code function.
* [Fix] In light mode, the text color of the markdown document content is displayed incorrectly.
* [Fix] The problem of expiration of login, and the login status is not removed.

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