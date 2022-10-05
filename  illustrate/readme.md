# Laravel 建檔說明  
## 一、Folder 介紹
1. app folder 專案的核心目錄，主要用於<u>**存放核心代碼，包含控制器、模型以及路由</u>**。  
* User.php 模型文件  
* /Http/Controllers 底下的 Controller.php 為基類控制器，可在 /Http/Controllers 底下建立另外的資料夾存法其他控制器，來繼承 Controller.php 的控制器  
* 另建 Home folder 以及 Admin folder 來分類前後端的模組。  
---
2. bootstrap folder 存放框架啟動需要的文件，它是系統的東西一般不動它。  
---
3. config folder 專案的配置目錄，主要 <u>**存放配置文件**</u>。  
* app.php：專案的主要配置文件。
* auth.php：用來定義用戶認證（登入）的配置文件。  
* database.php：針對於數據庫的配置文彥。  
* filesystems.php：上傳文件、文件儲存需要使用到的配置文件。  
---
4. database folder 數據遷移目錄。
* factories file 一般不用，自己寫比較麻煩，通常用別人寫的即可。
* migrations file 為遷移文件，用來 create table。
* seeds file 為種子目錄，存放 table 內的 data 填充文件。  
---
5. public folder 專案的入口文件和系統的靜態資源項目（如 css, img, js, uploads），它為單一入口文件，相對安全，<u>**後期使用的外部靜態文件（js, css, img 等）都要放到此目錄底下**</u>。  
* ___它的重點是專案的單一入口在這個目錄下，因此後續配置虛擬主機的時候要把站點位置指定到 public folder 下___。  
---
6. resources folder 存放視圖文件及語言包的文件。  
* lang folder： 存放語言包（如果專案需要本地化則需配置語言包）。
* views folder：存放視圖文件的 folder （視圖文件也可分
目錄管理）。  
---
7. routes folder 是定義路由的 folder， <u>**web.php 是定義路由的文件** </u> 。
---
8. storage folder 主要存放緩存文件及日誌文件。
* 後期客戶上傳文件到本地則存在 storage folder。  
* app folder：存放用戶的上傳的文件。
* framework folder：框架運行時的緩存文件。
* log folder：日誌目錄。
---
9. test folder 測試文件。
---
10. vendor folder 主要存放第三方的類庫文件。  
---
## 二、File 介紹  
1. .env file 主要設置一些系統相關的配置文件訊息。  
* <u>**config folder 裡面的文件配置內容一般都是讀取該文件裡面的配置訊息（config 裡面的配置基本都是來自.env file）**</u>。
* 可配置伺服器、資料庫、email等。
---
2. artisan file 框架的腳手架文件，主要用於代碼生成，如控制器、模型文件等。
* 執行命令：#php artisan 需要執行的指令，但必須達成以下條件：  
要求一：php 必須添加環境變量，並且保證版本。  
要求二：artisan 必須存在命令行當前的的工作路徑下。  
---
3. composer.jason 依賴包配置文件，宣告當前需要的軟體依賴，但是不能刪除，composer 需要使用 。
---  
## 重點掌握目錄
|  目錄   |  作用  |
| :---:  | :---: |
|   app folder  | 保存模組文件（默認） |
| app/Http/Controllers  | 保存控制器文件 |
| resources/views  | 保存視圖文件 |
| config folder  | 配置文件目錄 |
| routes folder  | 存放路由文件 |
| database/migrations  | 存放 DB 資料表文件（操作數據表結構） |
| database/seeds  | 存放 DB 種子文件（模擬測試數據） |
---
## 路由別名
路由別名相當於在路由定義的時候，為路由起了一個別名，在以後的程序中可以通過這個別名來獲取路由的訊息。
例如：  
```
Route::any('/test/1123/1561/yuikyu',funtion(){}
     echo "hello world!"
})->('名字')
```  
可透過```php artisan route:list```查看。  

## 路由群組  
比如後台有以下路由：
```
/admin/login  
/admin/logout  
/admin/index  
/admin/user/add  
/admin/user/del  
...
```
他們的共同點是都有/admin/，為方便管理，可將他們放到一個路由分組中。
使用 **prefix** 屬性指定路由。  
```
Route::group['prefix'=>'admin'],function(){
    Route::get('login',function(){
        //匹配“/admin/users”URL

    });
    Route::get('logout',function(){
        //匹配“/admin/users”URL

    });
    Route::get('index',function(){
        //匹配“/admin/users”URL

    });
});
```