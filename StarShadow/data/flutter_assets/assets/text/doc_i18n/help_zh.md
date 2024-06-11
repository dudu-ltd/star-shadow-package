# 星影指南

## 0. 新玩家
如果你还没有自己的图数据库，或者想了解我们推荐的用法，请进入[传送门](https://dudu.ltd/docs/zh/StarShadow/new-player.html)，快速上手星影的用法。

## 1. 菜单栏功能
1. 添加连接，详见第2点【添加数据库连接】
    > 如还没有自己的图数据库，可通过以下方式获取一个免费的图数据库：
    > - [使用 RPM 或 DEB 包安装 NebulaGraph](https://docs.nebula-graph.com.cn/3.8.0/4.deployment-and-installation/2.compile-and-install-nebula-graph/2.install-nebula-graph-by-rpm-or-deb/)
    > - [阿里云计算巢NebulaGraph试用版 3.4.0](https://computenest.aliyun.com/market/service-39f4f251e9484369a778?spm=5176.29141018.J_PGjKnplUAs1kXQYVyQamo.9.7b625d102SpFHx)
    > - 更多安装方式，请参考 [NebulaGraph 官方文档](https://docs.nebula-graph.com.cn/3.8.0/)
2. 打开文件夹，初次打开会默认在用户文档中创建一个文件夹，开发者可以自行选择新路径；
3. 最近打开，保存多个选择过的文件夹路径，开发者可以根据正在开发的项目在多个路径间切换；
4. 退出。


## 2. 添加数据库连接（当前版本只支持 [NebulaGraph](https://docs.nebula-graph.com.cn/3.8.0/)）
1. 数据源名称，便于自己区分不同数据源即可
2. 选择数据库类型（默认NebulaGraph）
3. 主机地址，示例：gdbc.nebula://192.168.0.1:9669
4. 用户名，示例：root
5. 密码，示例：nebula
3. 测试连接
4. 完成数据源添加

## 3. 数据源树结构
- 数据源名称（自定义）
    - basketballplayer
        - 标签
            - player
            - team
        - 关系
            - follow
            - serve
        - 查询（可用于存放项目所用的 nGQL）
            - 常用查询（文件夹）
                - 查看詹姆斯所服役的球队（nGQL）
            - 日常运维（文件夹）
                - 查看会话连接数（nGQL）
    - spaceName2
    - ...

## 4. 数据源树结构所支持的操作及其说明（以上述数据源树结构为例）
### 4.1、【数据源名称】节点
1. 刷新时，执行 [SHOW SPACES](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/3.show-spaces/)
当添加图空间、节点类型或边类型时，用于更新 schema 的树结构。
2. 左侧箭头展开 同刷新
3. 创建图空间时，执行  [CREATE SPACE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/1.create-space/)
用于在当前的主机中，创建一个新的图空间。
4. 编辑
当连接参数发生变动时，用于修改连接参数。
5. 删除
删除当前数据源，对数据库数据不做任何操作。

### 4.2、【basketballplayer】节点（图空间节点）
1. 单击
在主操作区中，打开面板，并展示当前图空间各 tag/type 的数据量，执行 [SHOW STATS](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/7.general-query-statements/6.show/14.show-stats/)
前提：当前图空间执行过 [SUBMIT JOB STATS](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/4.job-statements/#submit_job_stats)。

1. 刷新
当添加节点类型或边类型时，用于更新 schema 的结构。

2. 复制时，执行 [CREATE SPACE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/1.create-space/#_4)
只对当前空间的 schema 进行复制，执行以下语句：
    ```cypher
    CREATE SPACE IF NOT EXISTS newSpace AS basketballplayer;
    ```
3. 清除数据时，执行 [CLEAR SPACE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/6.clear-space/)
保留当前空间的 schema，并清空所有数据，执行以下语句：
    ```cypher
    CLEAR SPACE IF EXISTS basketballplayer;
    ```
4. 删除时，执行 [DROP SPACE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/5.drop-space/)
删除当前图空间，schema 与数据均不保留。执行以下语句：
    ```cypher
    DROP SPACE basketballplayer;
    ```

### 4.3、【标签】节点
1. 刷新 
    - [SHOW TAGS](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/10.tag-statements/4.show-tags/)
        ```cypher
        SHOW TAGS;
        ```
    - [DESCRIBE TAG](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/10.tag-statements/5.describe-tag/)
        ```cypher
        DESCRIBE TAG `player`;
        DESCRIBE TAG `team`;
        ```
    - [SHOW EDGES](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/11.edge-type-statements/4.show-edges/)
        ```cypher
        SHOW EDGES;
        ```
    - [DESCRIBE EDGE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/11.edge-type-statements/5.describe-edge/)
        ```cypher
        DESCRIBE EDGE `follow`;
        DESCRIBE EDGE `serve`;
        ```
2. 创建标签时，执行 [CREATE TAG](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/10.tag-statements/1.create-tag/)

### 4.4、【player】节点（数据库中的 tag）
1. 单击时，执行  [MATCH](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/7.general-query-statements/2.match/)
    在主操作区中打开一个表格面板，展示当前 tag 的数据，并按页加载，每页100条数据，执行以下语句：
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

1. 编辑时，执行 [ALTER TAG](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/10.tag-statements/3.alter-tag/)
2. 删除时，执行 [DROP TAG](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/10.tag-statements/2.drop-tag/)
    ```cypher
    DROP TAG `player`;
    ```

### 4.5、【follow】节点（数据库中的 edgeType）
1. 单击时，执行 [MATCH](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/7.general-query-statements/2.match/)
    在主操作区中打开一个表格面板，展示当前 edgeType 的数据，并按页加载，每页100条数据，执行以下语句：（需要在边表创建了索引的前提下，如展示失败，可通过【索引】按钮进行索引创建。）
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
1. 编辑时，执行 [ALTER EDGE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/11.edge-type-statements/3.alter-edge/)
2. 删除时，执行 [DROP EDGE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/11.edge-type-statements/2.drop-edge/)
    ```cypher
    DROP EDGE `follow`;
    ```


### 4.6、【查询】节点
1. 刷新
从选定的项目工作区中，同步查询脚本的文件结构。
2. 添加
创建一个新的`.ngql`文件。
3. 添加分组
创建一个新的文件夹。
4. 删除
从文件系统中删除文件、文件夹。

### 4.7、【日常运维】节点
文件夹类型的节点，同【查询】节点。

### 4.8、【查看詹姆斯所服役的球队】等nGQL文件节点
1. 重命名：对文件进行重命名；
2. 删除：删除 nGQL 文件。


## 5、主操作区所支持的操作及其说明
### 5.1、space操作区
> 入口：单击图空间节点后出现，如：【basketballplayer】。
2. 导入：支持 csv 导入，同时支持通过 csv 的首行创建 schema；
3. 全选（原意为选中批量操作的schema，进行后续操作，如备份等，未实现）。

### 5.2、tag操作区
> 入口：单击标签节点后出现，如：【player】。
1. 刷新：将页面回归为第一页；
2. 索引：
    1. 展示索引 [SHOW INDEXES](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/2.show-native-indexes/)

    2. 创建索引 [CREATE TAG INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/1.create-native-index/)
        ```cypher
        CREATE TAG INDEX `i_player_age` ON `player`(`age`);
        ```

    3. 重建索引 [REBUILD INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/4.rebuild-native-index/)
        ```cypher
        REBUILD TAG INDEX `i_player_age`;
        ```

    4. 删除索引 [DROP INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/6.drop-native-index/)
        ```cypher
        DROP TAG INDEX `i_player_age`;
        ```
    

3. 添加数据，支持单行添加数据 [INSERT VERTEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/12.vertex-statements/1.insert-vertex/)：
      ```cypher
      INSERT VERTEX `player` (name, age) 
      VALUES 'player999': ('Kobe', 41);
      ```

4. 数据表格支持：
    1. 查看单行详细数据；
    2. 编辑单行数据 [UPDATE VERTEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/12.vertex-statements/2.update-vertex/)；
        ```cypher
        UPDATE VERTEX ON `player` 'player999'
        SET age = 18
        ```
    3. 复制当前右键的单行数据（除 vid 外），脚本同【添加数据】；
    4. 删除节点 [DELETE VERTEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/12.vertex-statements/4.delete-vertex/)：
        ```cypher
        DELETE VERTEX 'player999';
        ```


### 5.3、edge操作区
> 入口：单击关系节点后出现，如：【follow】。
1. 刷新：将页面回归为第一页；
2. 索引：
    1. 展示索引 [SHOW INDEXES](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/2.show-native-indexes/)
    2. 创建索引 [CREATE INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/1.create-native-index/)
        ```cypher
        CREATE EDGE INDEX `i_follow` ON `follow`();
        ```
    3. 重建索引 [REBUILD INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/4.rebuild-native-index/)
        ```cypher
        REBUILD EDGE INDEX `i_follow`;
        ```
    4. 删除索引 [DROP INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/6.drop-native-index/)
        ```cypher
        DROP EDGE INDEX `i_follow`;
        ```

3. 添加数据，支持单行添加数据 [INSERT EDGE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/13.edge-statements/1.insert-edge/)：
    ```cypher
    INSERT EDGE `follow` (degree) 
    VALUES 'player999'->'player888'@0: (1);
    ```
4. 数据表格支持：
    1. 查看单行详细数据；
    2. 编辑单行数据 [UPDATE EDGE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/13.edge-statements/2.update-edge/)
        ```cypher
        UPDATE EDGE ON `follow` 'player999'->'player888'@0
        SET degree = 2;
        ```
    3. 复制当前右键的单行数据（除 ranking 外），脚本同【添加数据】；
    4. 删除边 [DELETE EDGE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/13.edge-statements/4.delete-edge/)
        ```cypher
        DELETE EDGE `follow` 'player999'->'player888'@0;
        ```

### 5.4 查询操作区
> 入口：单击查询节点后出现，如：【查看詹姆斯所服役的球队】。
1. 执行计划
当勾选时，执行查询时会同时返回执行计划 [EXPLAIN 和 PROFILE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/17.query-tuning-statements/1.explain-and-profile/)。
```cypher
PROFILE $ngql
```

2. 运行
    - 当编辑区中，无选中脚本，执行所有脚本；
    - 当编辑区中，有选中脚本，执行选中脚本。

3. 美化代码（未充分测试，可能导致 nGQL 不可用）
    - 当编辑区中，无选中脚本时，格式化当前编辑区中的 nGQL 代码；
    - 当编辑区中，有选中脚本时，格式化选中的 nGQL 代码。

4. 参数区
    - 与数据库中的参数不同。
    - 可以在参数区中，点`+`添加参数，如：name | Kobe | string，并在 ngql 中使用 `{{name}}` 植入。
        ```cypher
        MATCH (n:player)
        WHERE n.player.name == '{{name}}'
        RETURN n;
        ```
    - 支持添加多套参数方案，开发者可根据查询需要进行切换而不用修改编辑区中的 nGQL 脚本。

## 6. 结尾
开发者可以通过图形化，无需编写相应的nGQL脚本，即可完成上述数据库操作。
我们正在努力让星影成为开发者在图数据库实践路上重要的伙伴。