# 基礎教學
---
> [Addressables基礎教學網址](https://unity.csdn.net/65b1ce6dd4226e0eb4272bdc.html?dp_token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6NTA5OTEyOCwiZXhwIjoxNzEwOTE0ODY2LCJpYXQiOjE3MTAzMTAwNjYsInVzZXJuYW1lIjoibTBfNzQ5ODM0OTQifQ.2pNlKP6cWGK8u9qX00YrltYXgTuKgwN8ceWWNwvQrPc)
> 
> 說得很詳細
> 
> 基本功能都有說到
> 
> 包括基礎的熱更新


# 熱更新
---
## (一) 開啟Build Remote Catalog
    
想要使用熱更新，需要先開啟`Catalog`

![](/images/20240319162157.png)

## (二) GoogleCloud設定

> 熱更新需要將打包出來的資源上傳到雲端服務器上
> 
> 這邊選擇使用`GoogleCloud`
> 
> 但在這之前雲端還需要一些設定

* GoogleCloud創一個專案並新增一個儲存桶
 
![](/images/20240319165344.png)

* 存取權設定統一，且公開

![](/images/20240319165730.png)

* 複製公開連結，取得`LoadPath`
  
> 先隨便上傳一個檔案，圖片也可以
> 
> 主要是要拿到公開連結

![](/images/20240320092311.png)


> 這邊複製公開連結後還需要刪除一些
> 
> 因為我們只需要連到這個資料夾的路徑
> 
> 不需要這個檔案的路徑

> **舉例**
> 
> `https://storage.googleapis.com/aifun_addressable_test/Test.txt`
> 
> **刪除**
> 
> `Test.txt`
> 
> **最後需要**
> 
> `https://storage.googleapis.com/aifun_addressable_test/`


## (三) 雲端路徑設定

* 回Unity 替換`Remote`的`LoadPath`
  
> 打開`ManageProfiles`
> 
> 找到`RemoteLoadPath`
> 
> 將其替換

![](/images/20240319173254.png)

> 剛才的路徑尾端記得要加上`[BuildTarget]`

![](/images/20240319173517.png)

* 將需要熱更的`Group`調整成雲端

![](/images/20240319174522.png)


## (四) 執行Builb打包資源包

* 選擇 `Default Build Script`

![](/images/20240319163218.png)
    
> 打包完後可以在`ServerData`裡找到`catalog`與`bundle`包

![](/images/20240319163423.png)
![](/images/20240319163517.png)

* 上傳資源包

> 這時就可以將資源包上傳到雲端
> 
> 這邊使用的平台是Android

![](//images/20240319171310.png)

> 上傳完後可以稍微測試一下
> 
> 看看包出去的資源是不是可以正常載入

## (五) 輸出APK

  > 都測試完就可以輸出APK


## (六) 更新資源包

* 按下`UpDate a Previous Build`
  
![](/images/20240319175343.png)

* 選擇`.bin`檔案

> 因為我是Android平台，所以進入Android資料夾內

![](/images/20240320094017.png)

* 上傳更新後的資源包

> 將新的`catalog`與`bundle`包上傳到相對的資料夾中

![](/images/20240320095652.png)

![](/images/20240320100125.png)

## (七) 雷點紀錄

* `catalog`上傳到`GoogleCloud`不會立即更新
> 由於資源包的更新紀錄都在`catalog`裡
> 
> 所以發現明明上傳了更新包
> 
> 但我的內容卻沒有被更新
> 
> 只需要等大約1小時左右
> 
> 就可以正常更新了
