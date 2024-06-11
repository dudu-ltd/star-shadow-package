
# 星影指南

## 0. 新玩家
如果你還沒有自己的圖數據庫，或者想了解我們推薦的用法，請進入[傳送門](https://dudu.ltd/docs/zh/StarShadow/new-player.html)，快速上手星影的用法。

## 1. 菜單欄功能
1. 添加連接，詳見第2點【添加數據庫連接】
    > 如還沒有自己的圖數據庫，可通過以下方式獲取一個免費的圖數據庫：
    > - [使用 RPM 或 DEB 包安裝 NebulaGraph](https://docs.nebula-graph.com.cn/3.8.0/4.deployment-and-installation/2.compile-and-install-nebula-graph/2.install-nebula-graph-by-rpm-or-deb/)
    > - [阿里雲計算巢NebulaGraph試用版 3.4.0](https://computenest.aliyun.com/market/service-39f4f251e9484369a778?spm=5176.29141018.J_PGjKnplUAs1kXQYVyQamo.9.7b625d102SpFHx)
    > - 更多安裝方式，請參考 [NebulaGraph 官方文檔](https://docs.nebula-graph.com.cn/3.8.0/)
2. 打開文件夾，初次打開會默認在用戶文檔中創建一個文件夾，開發者可以自行選擇新路徑；
3. 最近打開，保存多個選擇過的文件夾路徑，開發者可以根據正在開發的項目在多個路徑間切換；
4. 退出。


## 2. 添加數據庫連接（當前版本只支持 [NebulaGraph](https://docs.nebula-graph.com.cn/3.8.0/)）
1. 數據源名稱，便於自己區分不同數據源即可
2. 選擇數據庫類型（默認NebulaGraph）
3. 主機地址，示例：gdbc.nebula://192.168.0.1:9669
4. 用戶名，示例：root
5. 密碼，示例：nebula
3. 測試連接
4. 完成數據源添加

## 3. 數據源樹結構
- 數據源名稱（自定義）
    - basketballplayer
        - 標籤
            - player
            - team
        - 關係
            - follow
            - serve
        - 查詢（可用於存放項目所用的 nGQL）
            - 常用查詢（文件夾）
                - 查看詹姆斯所服役的球隊（nGQL）
            - 日常運維（文件夾）
                - 查看會話連接數（nGQL）
    - spaceName2
    - ...

## 4. 數據源樹結構所支持的操作及其說明（以上述數據源樹結構為例）
### 4.1、【數據源名稱】節點
1. 刷新時，執行 [SHOW SPACES](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/3.show-spaces/)
當添加圖空間、節點類型或邊類型時，用於更新 schema 的樹結構。
2. 左側箭頭展開 同刷新
3. 創建圖空間時，執行  [CREATE SPACE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/1.create-space/)
用於在當前的主機中，創建一個新的圖空間。
4. 編輯
當連接參數發生變動時，用於修改連接參數。
5. 刪除
刪除當前數據源，對數據庫數據不做任何操作。

### 4.2、【basketballplayer】節點（圖空間節點）
1. 單擊
在主操作區中，打開面板，並展示當前圖空間各 tag/type 的數據量，執行 [SHOW STATS](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/7.general-query-statements/6.show/14.show-stats/)
前提：當前圖空間執行過 [SUBMIT JOB STATS](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/4.job-statements/#submit_job_stats)。

1. 刷新
當添加節點類型或邊類型時，用於更新 schema 的結構。

2. 複製時，執行 [CREATE SPACE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/1.create-space/#_4)
只對當前空間的 schema 進行複製，執行以下語句：
    ```cypher
    CREATE SPACE IF NOT EXISTS newSpace AS basketballplayer;
    ```
3. 清除數據時，執行 [CLEAR SPACE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/6.clear-space/)
保留當前空間的 schema，並清空所有數據，執行以下語句：
    ```cypher
    CLEAR SPACE IF EXISTS basketballplayer;
    ```
4. 刪除時，執行 [DROP SPACE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/9.space-statements/5.drop-space/)

### 4.3、【標籤】節點
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

2. 創建標籤時，執行 [CREATE TAG](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/10.tag-statements/1.create-tag/)

### 4.4、【player】節點（數據庫中的 tag）
1. 單擊時，執行  [MATCH](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/7.general-query-statements/2.match/)
    在主操作區中打開一個表格面板，展示當前 tag 的數據，並按頁加載，每頁100條數據，執行以下語句：
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

1. 編輯時，執行 [ALTER TAG](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/10.tag-statements/3.alter-tag/)
2. 刪除時，執行 [DROP TAG](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/10.tag-statements/2.drop-tag/)
    ```cypher
    DROP TAG `player`;
    ```

### 4.5、【follow】節點（數據庫中的 edgeType）
1. 單擊時，執行 [MATCH](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/7.general-query-statements/2.match/)
    在主操作區中打開一個表格面板，展示當前 edgeType 的數據，並按頁加載，每頁100條數據，執行以下語句：（需要在邊表創建了索引的前提下，如展示失敗，可通過【索引】按鈕進行索引創建。）
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

1. 編輯時，執行 [ALTER EDGE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/11.edge-type-statements/3.alter-edge/)

2. 刪除時，執行 [DROP EDGE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/11.edge-type-statements/2.drop-edge/)
    ```cypher
    DROP EDGE `follow`;
    ```

### 4.6、【查詢】節點
1. 刷新
從選定的項目工作區中，同步查詢腳本的文件結構。
2. 添加
創建一個新的`.ngql`文件。
3. 添加分組
創建一個新的文件夾。
4. 刪除
從文件系統中刪除文件、文件夾。

### 4.7、【日常運維】節點
文件夾類型的節點，同【查詢】節點。

### 4.8、【查看詹姆斯所服役的球隊】等nGQL文件節點
1. 重命名：對文件進行重命名；
2. 刪除：刪除 nGQL 文件。

## 5、主操作區所支持的操作及其說明
### 5.1、space操作區
> 入口：單擊圖空間節點後出現，如：【basketballplayer】。
2. 導入：支持 csv 導入，同時支持通過 csv 的首行創建 schema；
3. 全選（原意為選中批量操作的schema，進行後續操作，如備份等，未實現）。

### 5.2、tag操作區
> 入口：單擊標籤節點後出現，如：【player】。
1. 刷新：將頁面回歸為第一頁；
2. 索引：
    1. 展示索引 [SHOW INDEXES](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/2.show-native-indexes/)

    2. 創建索引 [CREATE TAG INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/1.create-native-index/)
        ```cypher
        CREATE TAG INDEX `i_player_age` ON `player`(`age`);
        ```

    3. 重建索引 [REBUILD INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/4.rebuild-native-index/)
        ```cypher
        REBUILD TAG INDEX `i_player_age`;
        ```

    4. 刪除索引 [DROP INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/6.drop-native-index/)
        ```cypher
        DROP TAG INDEX `i_player_age`;
        ```
3. 添加數據，支持單行添加數據 [INSERT VERTEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/12.vertex-statements/1.insert-vertex/)：
      ```cypher
      INSERT VERTEX `player` (name, age) 
      VALUES 'player999': ('Kobe', 41);
      ```
4. 數據表格支持：
    1. 查看單行詳細數據；
    2. 編輯單行數據 [UPDATE VERTEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/12.vertex-statements/2.update-vertex/)；
        ```cypher
        UPDATE VERTEX ON `player` 'player999'
        SET age = 18
        ```
    3. 複製當前右鍵的單行數據（除 vid 外），腳本同【添加數據】；
    4. 刪除節點 [DELETE VERTEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/12.vertex-statements/4.delete-vertex/)：
        ```cypher
        DELETE VERTEX 'player999';
        ```


### 5.3、edge操作區
> 入口：單擊關係節點後出現，如：【follow】。
1. 刷新：將頁面回歸為第一頁；
2. 索引：
    1. 展示索引 [SHOW INDEXES](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/2.show-native-indexes/)
    2. 創建索引 [CREATE INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/1.create-native-index/)
        ```cypher
        CREATE EDGE INDEX `i_follow` ON `follow`();
        ```
    3. 重建索引 [REBUILD INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/4.rebuild-native-index/)
        ```cypher
        REBUILD EDGE INDEX `i_follow`;
        ```
    4. 刪除索引 [DROP INDEX](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/14.native-index-statements/6.drop-native-index/)
        ```cypher
        DROP EDGE INDEX `i_follow`;
        ```
3. 添加數據，支持單行添加數據 [INSERT EDGE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/13.edge-statements/1.insert-edge/)：
    ```cypher
    INSERT EDGE `follow` (degree) 
    VALUES 'player999'->'player888'@0: (1);
    ```
4. 數據表格支持：
    1. 查看單行詳細數據；
    2. 編輯單行數據 [UPDATE EDGE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/13.edge-statements/2.update-edge/)
        ```cypher
        UPDATE EDGE ON `follow` 'player999'->'player888'@0
        SET degree = 2;
        ```
    3. 複製當前右鍵的單行數據（除 ranking 外），腳本同【添加數據】；
    4. 刪除邊 [DELETE EDGE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/13.edge-statements/4.delete-edge/)
        ```cypher
        DELETE EDGE `follow` 'player999'->'player888'@0;
        ```
### 5.4 查詢操作區
> 入口：單擊查詢節點後出現，如：【查看詹姆斯所服役的球隊】。
1. 執行計劃
當勾選時，執行查詢時會同時返回執行計劃 [EXPLAIN 和 PROFILE](https://docs.nebula-graph.com.cn/3.8.0/3.ngql-guide/17.query-tuning-statements/1.explain-and-profile/)。
```cypher
PROFILE $ngql
```

2. 執行
    - 當編輯區中，無選中腳本，執行所有腳本；
    - 當編輯區中，有選中腳本，執行選中腳本。

3. 美化代碼（未充分測試，可能導致 nGQL 不可用）
    - 當編輯區中，無選中腳本時，格式化當前編輯區中的 nGQL 代碼；
    - 當編輯區中，有選中腳本時，格式化選中的 nGQL 代碼。

4. 參數區
    - 與數據庫中的參數不同。
    - 可以在參數區中，點`+`添加參數，如：name | Kobe | string，並在 ngql 中使用 `{{name}}` 植入。
        ```cypher
        MATCH (n:player)
        WHERE n.player.name == '{{name}}'
        RETURN n;
        ```
    - 支持添加多套參數方案，開發者可根據查詢需要進行切換而不用修改編輯區中的 nGQL 腳本。

## 6. 結尾
開發者可以通過圖形化，無需編寫相應的nGQL腳本，即可完成上述數據庫操作。
我們正在努力讓星影成為開發者在圖數據庫實踐路上重要的夥伴。

