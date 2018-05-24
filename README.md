<!doctype html>
<html>
<head>
<title>个人主页</title>
<link href="style.css" rel="stylesheet"  type="text/css" />


<meta charset="utf-8">
</head>
<body> 
<header> 
  <h1> 
        个人  <span class="orange"> 的BLOG </span>
  </h1>
</header>


<nav>
      <ul>
        <li><a href="index.html" class="selected">博客首页 </a> </li>
        <li><a href="index1.html">关于我 </a></li>
        <li><a href="index2.html">给我留言 </a></li>
        <li><a href="index3.html">友情链接 </a></li>
        <li><a href="index4.html">我的信箱 </a></li>
        <li><a href="index5.html">社区 </a></li>
      </ul>
</nav> 




<div id="content">
    <section>
        <h1>晚上</h1>
        <p> 早上起来脑袋都昏沉，直到现在都是。 机器还在响着，车间里更热，所以我不去开空调，只希望自然风再大些。 那些可爱的人们在我的眼皮底下辛苦的干着活，又脏又累，我怎么忍心？？？ 把褥子被子都拿出去晒了，太阳出来又进去，到底是怎么啦提不起劲儿？ 这些工作都做完，喝了一杯温开水，汗流浃背，衣服湿透了，脑袋依然昏沉。 宿舍里很压抑，不知道是自己的原因还是环境就这样？
        </p>


        <p>当年张爸爸在工地上，没有风扇，没有空调，只要一把旧芭蕉扇就度过了几个夏天，何况我晚上还有一台电风扇，比起他的艰辛我这又算什么。 张妈妈在家里放了关于佛的书籍还有音乐，每天重复着大慈大悲，这些音乐听得我特别感动，一有空闲就想听听这样的音乐看看这些书。 他们本来就是一群超善良的人们，过于懂得感恩是值得善待的人们，想到他们我就特心疼特忘情。
        </p>


        <p>昨天感冒了，这种天气下还能感冒，晚上吃了药今天就好了，好神奇啊，身体不舒服一剂药就可以治愈，如果心不舒服了该怎么治疗？也许只是一句问候，一声关怀。可是，就是因为冷漠，才让人更自立的吧！ 
        </p>


    </section>


    <aside>
        <ul>
            <li><a href="index1.html" class="selected">日志 </a> </li>
            <li><a href="index1.html">相册 </a></li>
            <li><a href="index1.html">个人档案 </a></li>
            <li><a href="index1.html">分享 </a></li>
            <li><a href="index1.html">音乐地带 </a></li>
            <li><a href="index1.html">视频 </a></li>
            <li><a href="index1.html">更多 </a></li>
        </ul>
    </aside> 
</div>






<footer>
        <p>版权朱林斯所有</p>
        <hr />
        <small>法律条文</small>
        <small>联系我们</small>
        <small>客户意见</small>
        <small>商户合作</small>
</footer>


</body>


</html>
 
 
 
 
CSS样式
 @charset "utf-8";
*{margin:0px;padding:0px}
/* h5*/
body{
    background-color:#eceddd;
    font-family:Arial, Verdana,'Lucida Grande', Helvetica, sans-serif;
    text-align: center;
    color: #333333;
}


header{
    background: url(Img/bgheader.jpg) no-repeat #85D0ED;
    width: 902px;
    height: 203px;
    padding-top: 0px;
    margin: 0px auto;
    color: #000000;
    }


header h1 {
    float:left;
    font-size:2.9em;
    padding-top:60px;
    padding-left:37px;
    font-family:Arial,verdana, sans-serif;
    color:#37210c;
    font-weight:bolder;
    letter-spacing:-1px;
    }


.orange{
    color:#e67e1f;
    }


nav{
    list-style-type:none;
    margin:0px auto;
    width:902px;
    background-color:#303;
    clear:both;
    }
nav ul{
    list-style:none;
    margin-bottom:0px;
    margin-top:0px;
    margin-left:0px;
    width:902px;
    }
nav ul li{
    text-align:center;
    float:left;
    padding-left:0px;
    padding-top:0px;
    padding-bottom:0px;
    width:150px;
    }


nav ul li a{
    display:block;
    background-color:#37210c;
    border-right:1px solid #fff;
    line-height:2.5em;
    margin-right:0px;
    padding:8px 14px 8px 14px;
    color: #ecf9ff;
    font-weight:normal;
    font-size: 0.8em;
    text-decoration: none;
    }


nav li a:hover{
    color: #000;
    background-color:#ecf9ff;
    }


nav ul li .selected{
    color: #ecf9ff;
    background-color:#e67e1f;
    }
aside{
    float:left;
    list-style:none;
    margin-left:10px;
    height:50%;
    }


aside ul{
    list-style:none;
    margin-bottom:20px;
    margin-top:20px;
    margin-left:0px;
    }




aside li{
    text-align:left;
    padding-left:0px;
    padding-top:0px;
    padding-bottom:0px;
    border-bottom:1px solid #eaeada;
    }




aside ul li a{
    background-image: url(Img/bullet.gif);
    background-repeat:no-repeat;
    background-position:left center;
    display:block;
    background-color:#ffffff;
    line-height:1.7em;
    margin-right:0px;
    padding-top:6px;
    padding-bottom:6px;
    padding-left:22px;
    color: #666666;
    font-weight:normal;
    font-size: 0.8em;
    text-decoration: none;
    width:165px;
    }


aside  li a:hover{
    color: #37210c;
    background-color:#f7f7f2;
    }


aside .selected{
    color: #37210c;
    background-color:#f7f7f2;
    }




#content{
    margin:0 auto;
    width:902px;
    background-color:#dfeef9;
    height:290px;
    clear:both;
    }




section{
    float:left;
    width:75%;
    margin-right:0px;
    margin-top:15px;
    background-color:#FFF;
    text-align:left;
    font-size:0.9em;
    padding:5px;
    }


section h1{
    display:block;
    font-size:0.9em;
    width:50px;
    font-family: arial;
    text-align:left;
    font-weight:bold;
    color:#403f3b;
    font-family:arial;
    font-weight:bold;
    padding:5px;
    margin-top:5px;
    margin-left:12px;
    }


section p{ 
    font: normal 0.9em Arial, Verdana, Helvetica, sans-serif;
    font-size:0.9em;
    color: #000000;
    padding:10px;
    text-align:left;
    }


footer {
    width:902px;
    height: 85px;
    clear:both;
    margin-top: 10px;
    background-color:#dfeef9;
    color:#666666;;
    margin-left:auto;
    margin-right:auto;
    margin-bottom: 0px;
    padding-top: 15px;
    padding-right: 0px;
    padding-bottom: 0px;
    padding-left: 0px;
    }


footer p{
    font-size:0.7em;
    font-family:arial;
    font-weight:normal;
    line-height: 1.4em;
    color:#555555;
    padding:25px 0 0 10px;
    text-align:center;
    }


footer a {
    font-size:1em;
    text-decration:none;
    font-weight:normal;
    color:#467AA7;
    text-align:center;
    }


footer a:hover{
    text-decoration:underline;
    font-weight:normal;
    color:#467AA7;
    text-align:center;
    }
