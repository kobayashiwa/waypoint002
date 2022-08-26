# waypoint002
タイミングを取得して簡単なアニメーションをさせる（応用編）

## これの応用版
https://github.com/kobayashiwa/waypoint001

# 1.HTMLの記述例
```
<section class="sec">
    <div class="flex">
        <figure class="img-container col2">
            <img class="img-container__img" src="images/img01.jpg" alt="img01">
        </figure>
        <div class="text-container col2">
            <h2 class="text-container__title">SECTION01</h2>
            <p>
            今回はwaypoint.jsで「offset:70」を設定していますので、画面上から70％位置まで要素が来るとイベントを発生させることができます。<br>
            そして発生したイベントで要素に「active」というクラスをつけて、
            </p>
        </div><!--text-container-->
    </div><!--flex-bet-->
</section>
```
3行目、6行目「img-container」と「text-container」の2つがアニメーションさせる要素になるので、画面指定位置に来たらjQueryで「active」クラスを付ける。

# 2.CSSの記述例
```
.sec{
    margin-bottom: 120px;
}
 
.flex{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
}
 
.col2{
    width:40%;
}
 
.img-container{
    overflow: hidden;
    position: relative;
}
 
.img-container__img{
    display: block;
    opacity: 0;
    position: relative;
    transition:all .5s .3s ease; 
    z-index: 0;
}
 
.img-container:before{
    background: #333;
    content: '';
    display: block;
    height: 100%;
    position: absolute;
    transform: translateX(-100%);
    transition:all .8s 0s ease; 
    width: 100%;
    z-index: 1;     
}
 
.text-container{
    opacity: 0;
    padding:0 60px;
    transition: all .8s .5s ease;
}
 
.text-container__title{
    color: #333;
    font-size: 60px;
    font-weight: 700;
}
 
/*アニメーションするプロパティを設定します*/
.img-container.active img{
    opacity: 1;
}
 
.img-container.active:before{
    transform: translateX(100%);        
}
 
.text-container.active{
    opacity: 1;
}
```

# 3.jQuery
