<title>登录</title>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
    <script type="text/javascript">
        function val(){
            var name=window.document.getElementById("user").value;
            var password=window.document.getElementById("password").value;//获取值
            if (name == ""||password ==""){
                window.alert("用户名或密码不能为空!");
                return false;
            }
        
             if(name!="12345678"||password!="12345678"){//判断用户名密码登录
                window.alert("用户名或密码错误!");
                return false;
            }
            return true;
        }
    </script>
    <style type="text/css">
a{text-decoration:none}
</style>
</head>
<body >
<table border=0 ><tr><th width=2000 height=150 border=1 bgcolor='ccffff'><center><table><th><img src="images/30.jpg" width='100' height='100'></th>
<th><font size='7' color='ff7517'>图书用户管理系统</th></table></center></th><tr>
<table style="background-image:url(images/.jpg);background-size: 100%; opacity: 1; filter: alpha(opacity = 30)"><th >
<table border=0><tr><th width=1500 height=600 border=1><img src="images/4.jpg" height='400' width=400></th><th>
<form action="form.html" method="post" onsubmit="return val()" target="_blank">
<table border=0 bgcolor=F0F0F0>
<tr><th width=12 height=45></th><th colspan=3 width=82 height=45 align='left'>账户登录</th></tr>
<tr><th width=12 height=20></th><th width=20 height=20><img src="images/7.png" ></th><th width=50 height=20>
<input type="text" style="height:40px" placeholder="手机号/会员号/邮箱地址" size=40 id="user"></th><th width=12 height=20></th></tr>
<tr><th colspan=4 width=94 height=20></th></tr>
<tr><th width=12 height=20></th><th width=20 height=20><img src="images/8.png" ></th><th width=50 height=20>
<input type="password" style="height:40px" placeholder="📠" id="password" size=40></th><th width=12 height=20></th></tr>
<tr><th colspan=4 width=94 height=20></th></tr>
<tr><th width=12 height=20></th>
<th colspan=2 width=70 height=20 bgcolor=FF5809><input type="submit" 
    style="background-color:FF5809;height:40px;width:140px;font-size:20px;color:white;border:none" 
    value="登录" ></th>
    <th width=12 height=20></th></tr>
    <tr><th colspan=4 width=94 height=20></th></tr>
<tr><th width=12 height=20></th><th width=70  height=20 colspan=2><img src="images/9.png" ></th><th width=12 height=20></th></form></tr>
<tr><th colspan=4 width=94 height=6></th></tr>
<tr><th width=12 height=40><th colspan=2><table width=310 border=0><tr><th  width=35 height=20 align='left'><font size=2>忘记密码</font></th>
<th  width=35 height=20 align='right'><font size=2><a href="zhuce.html" target="_blank">免费注册</a></font></th></tr></table></th><th></th></tr>
<tr><th colspan=4 width=94 height=6></th></tr>
</table>

</th><th width='700'></th></tr></table></th><tr><th bgcolor='f9fa9b' height=120><p>📧联系邮箱：1234@qq.com</p><p>联系地址：枣庄学院</p><p>📞联系电话：178****6451</p></th></table>
</body>
