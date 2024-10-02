## [win10] nodejs & npm & yarn 設定環境變數

本節點主要介紹在 win10 系統中如何設定環境變數為開發帶來更好的體驗。

### #NodeJs：

安裝完 node，創建兩個目錄用來分別放置往後安裝其他庫生成的 .cmd 文件以及操作記錄 .log文件，按照文件約定分別命名為 `npm_global` 與 `npm_logs`。

<img src="https://raw.githubusercontent.com/tokoshiekou/code-notes/refs/heads/main/Img/folder.png" alt="folder" height="280">



接下去，按照路徑打開：`CTRL + I` 開啓 win10 settings，在檢索框鍵入 `view advanced system setting`，在彈窗中點擊右下角的 `Environment Variables (環境變數)`

在這裡，先看到用戶變數上半部分，把 `Path` 中映射到 Roaming/npm 選項修改為之前創建的 `npm_global` 目錄路徑，這將用來存放 NPM 或者 Yarn 安裝所生成的庫文件，妳可以選擇自己喜歡的地方放置。

<img src="https://raw.githubusercontent.com/tokoshiekou/code-notes/refs/heads/main/Img/user-variables.png" alt="user-variables" height="400">



系統變數下半部分，為他創建一個變數 `NODE_HOME` 設定 value 為 `原路徑位置\npm_global\node_modules` ，這裡追加 `node_modules` 但實際在文件目錄中無需創建。在系統變數 `Path` 中，新增 node 所在的目錄位置以及填入 `NODE_HOME` 變數。（結果如下圖）

<img src="https://raw.githubusercontent.com/tokoshiekou/code-notes/refs/heads/main/Img/system-variables.png" alt="system-variables" height="520">



最後，找到 node 安裝所在位置，右鍵目錄並檢閲屬性，檢查該目錄是否有修改權限。



### #NPM：

node 默認首選 npm 作爲庫管理工具，爲了讓安裝的庫存儲在 `npm_global` 還需要在 npm 設定 config 變數。

```
npm config set prefix "路徑\npm_global"
npm config set cache "路徑\npm_logs"
```



### #Yarn：

如果妳喜歡使用 yarn 作爲個人庫管理工具，那也同樣可以做到。創建兩個目錄 `yarn_cache` 與 `yarn_global` 。

```
yarn config set global-folder "路徑\yarn_global"
yarn config set cache-folder "路徑\yarn_cache"

# 校驗
yarn global dir
```



--END--
