# 建置Vue模塊流程

### 起因
>前台頁面的JS的function或是某數的值常有重複的部分，不管是在重寫新案子或是同案子不同頁面時，copy同一個function是較麻煩的一件事，能**像PHP有個library的模塊**，建構前台案子將會方便許多。 
<font size="2">(因前台剛好以VUE來寫，就研究關於VUE的寫法。)</font>

### 步驟一 (JS : modules)
JavaScript語言長期以來並未內建支援模組系統，，從ES6中加入了模組系統的支援，這邊比較狹隘的定義模組這部分，簡單來說就是能夠**利用import、export**，這兩者將JS資料或是function做輸出導入的動作。

```js
    //模塊輸出.JS
    export default 
    {
        //所需要輸出的內容擺這，最外層需由export default包住。
    }

    //模塊導入.js
    import mixin from '/模塊輸出.js'
    //import後面接名稱再來寫入來源。

    //利用模塊.html
    最主要是引入部分需加上modules此type
    <script type="modules" src="/模塊導入.js"></script>
    
```

### 步驟二 (vue.js : mixin)
mixin是vue內一種讓組件之間能共用方法的神奇方法，所有的component都能夠拿來使用，像是常用的mounted就能拿來好好利用，代表使用axios與預設的值都能用做使用!

#### mixin又分為全域與區域兩部分做使用
> 1. 區域 : 
```js
    new Vue({
        el : '#coolday', //綁定ID為coolday這個區域
        mixins : [mixin] //中括模塊導入.js所設立之名稱

        //備註 : 當function名稱與組件內相同會以組件內定義的function為主哦!
    })
```

>2. 全域 : 
```js
    Vue.mixin({
        methods : {
            alert(){
                if(my_heart_is_broken == yes)
                {
                    alert(ohoh!!!!!);
                }
            };
        }

        //備註 : 使用此方法物必小心，因為導入全域後所有的VUE組件都會吃到內容
    })
```

### 步驟三 (代值)
當以上兩步驟完成後，值已經能用被使用，只要在組件內利用(this.要的東西)，就能拿到值或是function，有了常用的模塊後，就能將常用的JS放入，包起來更加方便~順暢~

### 錯誤方向紀錄
原先以為模組部分就是vue.prototype，試過了一小段時間，發現....恩....好像不能很輕易的套用在html上，似乎還要有像是vue.loader,vue.router等等之類的加上去，才能順利跑.....!果斷切割....後才找到mixin~~


