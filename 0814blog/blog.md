### 主題 : ngimgCrop實現圖片裁切
#
>### 環境建置
1.下載ngimpCrop檔案 https://github.com/alexk111/ngImgCrop.git

2.引入angular.js  

```<script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/angularjs/1.8.0/angular.min.js"></script>```

3.欲利用angular.js，HTML需注意三個地方，  
* 將ng-app="app"寫於要使用angular的範圍，通常放於body標籤後
* 將ng-controller="Ctrl"寫於function要控制、作用的區域
* script內寫入    
```angular.module('app', ['ngImgCrop'])
.controller('Ctrl', function($scope) 
{
    //以$scope作為與html做連結的橋樑
    $scope.myImage = ''; //html內name是myImage的內容為空
};
```

>### 操作方法
1.快速利用功能可進入下載好的資料夾內的test.html適用範例

2.將ng-app、ng-controller、angular.module('app',['ngImgCrop']).controller加到欲使用 ngimgCrop的HTML檔

3.ngimgCrop內建許多功能，依照需求調整
```
<img-crop
image="{string}"  需要進行裁剪的圖片檔案  如$scope.myImage
result-image="{string}"　　儲存裁剪結果的圖片檔案　　如$scope.myCroppedImage
[change-on-fly="{boolean}"]　　　可選項：表示是否在拖拽裁剪區域時實時更新結果檔案
[area-type="{circle|square}"]　　可選項：表示裁剪視窗是方的還是圓的，預設是圓的
[area-min-size="{number}"]　　　　可選項，表示裁剪結果的最小大小，預設是80，即結果最小是高80畫素、寬80畫素
[result-image-size="{number}"]　　可選項，表示裁剪結果大小，預設是200，即高200畫素、寬200畫素
[result-image-format="{string}"]　　可選項，表示裁剪結果儲存的檔案型別，可以選擇image/jpeg、image/png、image/webp，預設是image/png
[result-image-quality="{number}"]　　可選項，表示裁剪結果的質量，取值在0.0到1.0之間
[on-change="{expression}"]　　　　　　可選項，檢測到圖片修改後執行的表示式
[on-load-begin="{expression"]　　　　可選項，圖片開始載入執行的表示式
[on-load-done="{expression"]　　　　可選項，圖片載入完成執行的表示式
[on-load-error="{expression"]　　　　可選項，圖片載入失敗執行的表示式
></img-crop>
```

4.裁切後的圖片為base64的格式，需轉換成檔案格式上傳



>### 報告歷程

1. 錯誤一  
找不到抓裁切圖片的方法，無法進行後續上傳的工作  
>修正:查看ngimgCrop的function，找到拿裁切圖片base64格式的地方

2. 錯誤二  
將ngimgCrop移植進去後，裁切圖片無法上傳到upload  
>修正:先將圖片格式轉成file檔，利用XHR方式上傳圖片

3. 嘗試一  
CI內有內建上傳語法，簡單幾行就可以上傳圖片  
```
$field_name = "some_field_name";
$this->upload->do_upload($field_name)
```
>### 總結
ngimgCrop是挺方便的裁切圖片外掛，如果能使用得心應手，將裁切功能加入到網頁內，可以避免上傳圖片爆版的問題!



