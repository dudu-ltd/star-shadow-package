# Guide of StarShadow

## 0. New Players
If you don't have your own graph database yet, or want to learn about the recommended usage, please visit the [link](https://dudu.ltd/docs/en/StarShadow/new-player.html) to quickly get started with StarShadow.

## 1. Menu Bar Functions
1. Add Connection, see [Add Database Connection](#2-add-database-connection)
    > If you don't have your own graph database yet, you can get a free graph database in the following ways:
    > - [Install NebulaGraph Using RPM or DEB Packages](https://docs.nebula-graph.com.cn/3.8.0/4.deployment-and-installation/2.compile-and-install-nebula-graph/2.install-nebula-graph-by-rpm-or-deb/)
    > - [NebulaGraph 3.4.0 provided by Alibaba Cloud Computing Nest](https://computenest.aliyun.com/market/service-39f4f251e9484369a778?spm=5176.29141018.J_PGjKnplUAs1kXQYVyQamo.9.7b625d102SpFHx)
    > - For more installation methods, please refer to the [NebulaGraph Official Documentation](https://docs.nebula-graph.com.cn/3.8.0/)
2. Open Folder, the first time you open it will default to creating a folder in the user documents, developers can choose a new path by themselves;
3. Recently Opened, save multiple selected folder paths, developers can switch between multiple paths according to the project being developed;
4. Exit.

## 2. Add Database Connection (The current version only supports [NebulaGraph](https://docs.nebula-graph.com.cn/3.8.0/))
1. Data source name, for your own distinction between different data sources
2. Select the database type (default NebulaGraph)
3. Host address, example: gdbc.nebula://192.168.0.1:9669
4. Username, example: root
5. Password, example: nebula
3. Test connection
4. Complete data source addition

## 3. Data Source Tree Structure
- Data source name (custom)
    - basketballplayer
        - Tags
            - player
            - team
        - Relationships
            - follow
            - serve
        - Queries (can be used to store nGQL used by the project)
            - Common Queries (folder)
                - View the teams that James has served (nGQL)
            - Daily Operations (folder)
                - View the number of session connections (nGQL)
    - spaceName2
    - ...

## 4. Operations Supported by the Data Source Tree Structure and Their Descriptions (using the above data source tree structure as an example)
### 4.1, [Data Source Name] Node
1. When refreshing, execute [SHOW SPACES](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/3.show-spaces/)
Used to update the schema tree structure when adding graph spaces, node types, or edge types.
2. Expand the left arrow to refresh the same
3. When creating a graph space, execute [CREATE SPACE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/1.create-space/)
Used to create a new graph space on the current host.
4. Edit
Used to modify connection parameters when the connection parameters change.
5. Delete
Delete the current data source without any operation on the database data.

### 4.2, [basketballplayer] Node (Graph Space Node)
1. Click
In the main operation area, open the panel and display the data volume of each tag/type in the current graph space, execute [SHOW STATS](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/7.general-query-statements/6.show/14.show-stats/)
Prerequisite: The current graph space has executed [SUBMIT JOB STATS](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/4.job-statements/#submit_job_stats).

1. Refresh
Used to update the structure of the schema when adding node types or edge types.

2. When copying, execute [CREATE SPACE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/1.create-space/#_4)
Only copy the schema of the current space, execute the following statement:
    ```cypher
    CREATE SPACE IF NOT EXISTS newSpace AS basketballplayer;
    ```
3. When clearing data, execute [CLEAR SPACE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/6.clear-space/)
Keep the schema of the current space and clear all data, execute the following statement:
    ```cypher
    CLEAR SPACE IF EXISTS basketballplayer;
    ```
4. When deleting, execute [DROP SPACE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/5.drop-space/)
Delete the current graph space, and neither the schema nor the data is retained. Execute the following statement:
    ```cypher
    DROP SPACE basketballplayer;
    ```
### 4.3, [Tags] Node
1. Refresh
    - [SHOW TAGS](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/10.tag-statements/4.show-tags/)
        ```cypher
        SHOW TAGS;
        ```
### 4.4, [player] Node (Tag in the database)
1. When clicked, execute [MATCH](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/7.general-query-statements/2.match/)
    Open a table panel in the main operation area to display the current tag data and load it by page, 100 data per page, execute the following statement:
    ```cypher
    MATCH (n:player) 
    RETURN 
        id(n), 
        n.`player`.`name` as `name`, 
        n.`player`.`age` as `age` 
    SKIP 0 LIMIT 100;

    MATCH (n:player) 
    RETURN 
        id(n), 
        n.`player`.`name` as `name`, 
        n.`player`.`age` as `age` 
    SKIP 100 LIMIT 100;

    // ...
    ```
1. Edit, execute [ALTER TAG](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/10.tag-statements/3.alter-tag/)
2. Delete, execute [DROP TAG](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/10.tag-statements/2.drop-tag/)
    ```cypher
    DROP TAG `player`;
    ```
### 4.5, [follow] Node (edgeType in the database)
1. When clicked, execute [MATCH](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/7.general-query-statements/2.match/)
    Open a table panel in the main operation area to display the current edgeType data and load it by page, 100 data per page, execute the following statement: (Need to create an index in the edge table, if the display fails, you can create an index through the [Index] button.)
    ```cypher
    MATCH (src)-[r:follow]->(dst) 
    RETURN 
        id(src), 
        rank(r), 
        id(dst), 
        r.`degree` as `degree` 
    SKIP 0 LIMIT 100;

    MATCH (src)-[r:follow]->(dst) 
    RETURN 
        id(src), 
        rank(r), 
        id(dst), 
        r.`degree` as `degree` 
    SKIP 100 LIMIT 100;

    // ...
    ```
1. Edit, execute [ALTER EDGE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/11.edge-type-statements/3.alter-edge/)
2. Delete, execute [DROP EDGE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/11.edge-type-statements/2.drop-edge/)
    ```cypher
    DROP EDGE `follow`;
    ```
### 4.6, [Query] Node
1. Refresh
Synchronize the file structure of the selected project workspace.
2. Add
Create a new `.ngql` file.
3. Add Group
Create a new folder.
4. Delete
Delete files and folders from the file system.

### 4.7, [Daily Operations] Node
A folder type node, same as the [Query] node.

### 4.8, [View the teams that James has served] and other nGQL file nodes
1. Rename: Rename the file;

2. Delete: Delete the nGQL file.

## 5. Operations Supported by the Main Operation Area and Their Descriptions    
### 5.1, Space Operation Area
> Entry: Click the graph space node to display, such as: [basketballplayer].
2. Import: Support csv import, and support creating schema through the first line of csv;
3. Select All (originally intended to select schema for batch operations, such as backup, not implemented).

### 5.2, Tag Operation Area
> Entry: Click the tag node to display, such as: [player].
1. Refresh: Return to the first page;
2. Index:
    1. Display index [SHOW INDEXES](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/2.show-native-indexes/)

    2. Create index [CREATE TAG INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/1.create-native-index/)
        ```cypher
        CREATE TAG INDEX `i_player_age` ON `player`(`age`);
        ```

    3. Rebuild index [REBUILD INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/4.rebuild-native-index/)
        ```cypher
        REBUILD TAG INDEX `i_player_age`;
        ```

    4. Delete index [DROP INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/6.drop-native-index/)
        ```cypher
        DROP TAG INDEX `i_player_age`;
        ```
3. Add Data, support adding data in a single line [INSERT VERTEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/12.vertex-statements/1.insert-vertex/):
    ```cypher
    INSERT VERTEX `player` (name, age) 
    VALUES 'player999': ('Kobe', 41);
    ```
4. Data Table Support:
    1. View detailed data of a single row;
    2. Edit data of a single row [UPDATE VERTEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/12.vertex-statements/2.update-vertex/);
        ```cypher
        UPDATE VERTEX ON `player` 'player999'
        SET age = 18
        ```
    3. Copy the current right-clicked single-row data (except vid), the script is the same as [Add Data];
    4. Delete node [DELETE VERTEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/12.vertex-statements/4.delete-vertex/):
        ```cypher
        DELETE VERTEX 'player999';
        ```
### 5.3, Edge Operation Area
> Entry: Click the relationship node to display, such as: [follow].
1. Refresh: Return to the first page;
2. Index:
    1. Display index [SHOW INDEXES](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/2.show-native-indexes/)
    2. Create index [CREATE INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/1.create-native-index/)
        ```cypher
        CREATE EDGE INDEX `i_follow` ON `follow`();
        ```
    3. Rebuild index [REBUILD INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/4.rebuild-native-index/)
        ```cypher
        REBUILD EDGE INDEX `i_follow`;
        ```
    4. Delete index [DROP INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/6.drop-native-index/)
        ```cypher
        DROP EDGE INDEX `i_follow`;
        ```
3. Add Data, support adding data in a single line [INSERT EDGE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/11.edge-type-statements/1.insert-edge/):
    ```cypher
    INSERT EDGE `follow` (degree)
    VALUES 'player999' -> 'player888': (1);
    ```
### 5.4, Query Operation Area
> Entry: Click the query node to display, such as: [View the teams that James has served].
1. Execution Plan
When checked, the execution plan [EXPLAIN and PROFILE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/17.query-tuning-statements/1.explain-and-profile/) will be returned at the same time as the query is executed.
    ```cypher
    PROFILE $ngql
    ```
2. Run
    - When there is no selected script in the editing area, execute all scripts;
    - When there is a selected script in the editing area, execute the selected script.

3. Beautify Code (not fully tested, may cause nGQL to be unusable)
    - When there is no selected script in the editing area, format the nGQL code in the current editing area;
    - When there is a selected script in the editing area, format the selected nGQL code.

4. Parameter Area
    - Different from the parameters in the database.
    - You can add parameters in the parameter area by clicking `+`, such as: name | Kobe | string, and use `{{name}}` in ngql.
        ```cypher
        MATCH (n:player)
        WHERE n.player.name == '{{name}}'
        RETURN n;
        ```
    - Support adding multiple sets of parameter schemes, developers can switch according to the query needs without modifying the nGQL script in the editing area.

## 6. End
Developers can complete the above database operations without writing the corresponding nGQL scripts through the graphical interface.
We are working hard to make Star Shadow an important partner for developers on the road to graph database practice.


