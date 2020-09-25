## VUE.JS 前端操作利器-簡潔的程式碼由此開端
***

### 為何使用VUE.JS?
> 原因一 : 不需在JS內寫HTML語法，導致維護不易。

> 原因二 : 許多較繁複的JS被VUE.JS包成較方便使用的語法。

> 原因三 : 相較於Angular、React，VUE的學習曲線較平緩，方便快速上手

### VUE.JS初學架構

1. 將需控制的區塊設置id(一般教學大部分以此為範例)

```
    <div id="app">
        {{ message }} /資料綁定message的值
    </div>
```

2. srcipt區塊內程式碼
```
    var app = new Vue
    ({
        el: '#app',
        data: 
        {
            message: 'Hello Vue!'
        }
    });
```

### 常用一，以VUE官方立場，建議使用AXIOS替代AJAX取得後端資料

重點一 : VUE原始data內的資料以object，無法直接傳值到後端

重點二 : AXIOS只是一個傳值方法，需利用QS的套件轉換格式後傳出
```
EX: let str = qs.stringify(obj); // 将Object对象转换为以&链接的url
```

### 常用二，拿到後端資料後利用V-for取代html內寫php的foreach

> 使用 v-for 迭代陣列中的元素。如下所示，list 是一個陣列，item 代表用於迭代的元素，使用 item.id 或 item.name 可帶出屬性。其中第二個參數 index 是索引值 (optional)。

```
    <div id="app">
    <ul>
        <li v-for="(item, index) in list">
        index: ${ index }, name: ${ item.name }
        </li>
    </ul>
    </div>

    var vm = new Vue({
    el: '#app',
    delimiters: ['${', '}'],
    data: {
        list: [
        { id: '123456789', name: '選項 1' },
        { id: '234567890', name: '選項 2' },
        { id: '345678901', name: '選項 3' },
        ],
    },
    });
```

### 常用三，V-if條件控制HTML內容
```
    <div id="app">
        <p v-if="showMessage">還剩下21天！</p>
    </div>

    <script>
        new Vue({
        el: "#app",
        data: {
            showMessage: false
        }
        });
    </script>
  ```

### VUE總結
***
VUE包好許多JS，加深學習後可讓使用者操作更加人性化，不需跳頁也能實現功能，
且讓頁面的程式碼更加簡潔，加速開發效率，也能將一些前端常用到的部分模組化，
相信會更加方便!!!
 



