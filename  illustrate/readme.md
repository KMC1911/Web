# 檔案夾說明  

1. app file 專案的核心目錄，主要用於<u>**存放核心代碼，包含控制器、模型以及路由</u>**。  
* User.php 模型文件  
* /Http/Controllers 底下的 Controller.php 為基類控制器，可在 /Http/Controllers 底下建立另外的資料夾存法其他控制器，來繼承 Controller.php 的控制器  
* 另建 Home file 以及 Admin file 來分類前後端的模組。  
---
2. bootstrap file 存放框架啟動需要的文件，它是系統的東西一般不動它。  
---
3. config file 專案的配置目錄，主要 <u>**存放配置文件**</u>。  
* app.php：專案的主要配置文件。
* auth.php：用來定義用戶認證（登入）的配置文件。  
* database.php：針對於數據庫的配置文彥。  
* filesystems.php：上傳文件、文件儲存需要使用到的配置文件。  
---
4. database file 數據遷移目錄
* factories file 一般不用，自己寫比較麻煩，通常用別人寫的即可。
* migrations file 為遷移文件，用來 create table。
* seeds file 為種子目錄，存放 table 內的 data 填充文件。  
---
5. public file 專案的入口文件和系統的靜態資源項目（如 css, img, js, uploads），它為單一入口文件，相對安全，<u>**後期使用的外部靜態文件（js, css, img 等）都要放到此目錄底下**</u>。  
* ___它的重點是專案的單一入口在這個目錄下，因此後續配置虛擬主機的時候要把站點位置指定到 public file 下___。  
---
6. 
