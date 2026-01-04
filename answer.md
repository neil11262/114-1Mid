# 第2次隨堂題目-隨堂-QZ2
>
>學號：112111128
><br />
>姓名：張志顯
1. a.

Ans: 
**(1) 陣列跟物件**<br>
**(2)宣告了一個陣列,陣列裡的每個元素都是物件**



1. b.

Ans:
```js
function getLowStock(products) {
 var result = []; // 準備一個空陣列，用來存放稍後找到符合條件的商品名稱
 for (let i = 0; i < products.length; i++){ //使用 for 迴圈，跑過products 陣列裡的每一個商品, i 是索引值，從 0 開始，直到陣列的最後一個項目
  if(products[i].stock < 10) { //檢查「當前這個商品」(products[i]) 的「庫存」(stock) 是否小於 10
    result.push(products[i].name);  //如果條件成立，就把該商品的「名稱」(name) 加入(push) 到 result 陣列中
  }
 }
 return result; //迴圈跑完後，將整理好的名單(result) 回傳
}
```
<!-- 請撰寫時，最後一句話再寫一次 -->


1. c.

Ans:
```js
function updateStock(products, updates) { 
  var result = []; //建立一個空陣列，用來儲存處理完畢後的新清單
  for (var i = 0; i < products.length; i++){  // 透過迴圈，一個一個檢查原本的產品 (products)
    var ObjectName = products[i].name; // 把當前產品的名字取出來，存在變數 ObjectName 中
    if (typeof updates[products[i].name] === "undefined"){ //檢查 updates (更新清單) 裡面，有沒有這個產品的名字？
      result.push({name: products[i].name, stock: products[i].stock}); // 如果不需要更新,建立一個新物件，保留原本的名字，並使用「原本的 stock」
    } else {
      result.push({name: products[i].name, stock: updates[products[i].name]}); //如果需要,就建立一個新物件，保留原本的名字，但使用「updates 裡對應的新 stock」
    }
    }
    return result; //迴圈結束，回傳整理好的新清單
  }
```
<!--  請撰寫時，第一句話再寫一次  -->

2. a.

Ans:
```js
 switch(url){
    case'/': //當網址 (url) 等於根目錄 '/' 時
      answer = 'index.html輸出部分'; // 設定要回應的內容為首頁資訊
      break; //執行完後跳出 switch，避免繼續執行下面的程式碼
      case'/calculator': //當網址 (url) 等於 '/calculator' 時
      answer = 'index2.html輸出部分'; // 設定要回應的內容為計算機頁面資訊
      break; //執行完後跳出 switch
      default: // 當上面的 case 都不符合時
      answer = 'error.html輸出部分'; // 設定要回應的內容為錯誤頁面
      break;
      }
```


2. b.

Ans:
```js
switch(req.url){ // 判斷使用者請求的網址路徑 (req.url)
  case'/': // 情況 1：當使用者訪問根目錄 (例如 http://localhost:3000/)
     filePath = '/index.ejs'; // 指定要讀取的檔案路徑為首頁樣板
     break; // 結束判斷，跳出 switch
  case'/calculator': // 情況 2：當使用者訪問計算機頁面 (例如 http://localhost:3000/calculator)
    filePath = '/index2.ejs'; // 指定要讀取的檔案路徑為第二個樣板
    break; // 結束判斷，跳出 switch
  default: //如果上述網址都不是 (例如請求的是圖片 /logo.png 或 CSS 檔案 /style.css)
    filePath = req.url; // 直接把「請求的網址」當作「檔案路徑」使用
    fileOtherFile = filePath; // 將這個路徑備份到另一個變數 
  }
```
<!--  請撰寫時，第一句話再寫一次  -->

2. c.

Ans:
```js
// 1. 使用 fs (File System) 模組來「非同步」讀取檔案
        // 第一個參數：檔案路徑 ('.' 代表目前目錄，拼接 '/index3.ejs')
        // 第二個參數：設定編碼為 'utf8' (這很重要，確保讀出來是文字字串，而不是二進位 Buffer)
        // 第三個參數：回呼函式 (Callback)，當檔案讀取完成後會執行這裡，帶入錯誤 (err) 或檔案內容 (template)
        fs.readFile(('.' + '/index3.ejs'), 'utf8', (err, template) => {
          // 2. 使用 EJS 引擎進行渲染 (Render)
          // 將讀取到的 EJS 原始碼 (template) 編譯成瀏覽器看得懂的標準 HTML 字串
          // 變數 html 此時就是純 HTML 文字了
         const html = ejs.render(template);

          // 3. 設定 HTTP 回應標頭 (Response Header)
          // 狀態碼 200: OK（代表請求成功）
          // Content-Type: 告訴瀏覽器回傳的內容是 HTML 文件，並且使用 UTF-8 編碼 (避免中文亂碼)
          res.writeHead(200, { 'Content-Type': 'text/html; charset=utf-8' });
          
          // 4. 發送回應並結束連線
          res.end(html);
        });
```
<!--  請撰寫時，第一句話和最後一句再寫一次  -->

2. d.

Ans:**2次**


