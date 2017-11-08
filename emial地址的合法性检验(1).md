在你的网站或者应用程序对话框中，有一个输入框要求用户输入一个电子邮件(E-mail)地址。在使用这个地址发送Email之前，你要使用一个正则表达式对它进行合法性检验，这有助于减少你可能会收到的由于无法投递而返回的邮件数量

> ### Step1 简单形式

 检查email地址中是否包含了"@"符号，并不包含任何空白  


    var strEmail_1 = "ngu@lee@163.com",
    	regEmail_1 = /^\S+@\S+$/gi;
    	
    console.log(strEmail_1.match(regEmail_1));//ngu@lee@163.com

> ### Step2 对字符加限制的简单形式
在"@"符号之后的域名部分限制为只能使用域名允许的字符，在@符号之前的域名部分只能使用在email中常见的字符；  


    var strEmail_1 = "ngulee@163.com",
    	regEmail_1 = /^[A-z0-9_.-]+@[A-z0-9.-]+$/gi;
    	
    //当strEmail_1 = "ngul@ee@163.com"
    console.log(strEmail_1.match(regEmail_1));//null
    
    //当strEmail_1 = "ngulee@163.com"
    console.log(strEmail_1.match(regEmail_1));//ngulee@163.com
    
> ### Step2 包括所有字符的简单形式


    var strEmail_1 = "ngulee@163.com",
    	regEmail_1 = /^[\w!#$%&^+/*=?'{|}~.-]+@[A-z0-9.-]+$/gi;
    	
    console.log(strEmail_1.match(regEmail_1));//ngulee@163.com  
    
> ### Step4 不允许前导、拖尾、连续的点号
在用户名和域名中都可以包含一个或者多个点号，但是不允许出现两个连续的点号。另外在用户名和域名中，第一位和最后一位不允许出现点号；


    var strEmail_1 = "ng.u.lee@163.c.o.m",
    	regEmail_1 = /^[\w!#$%&^+/*=?'{|}~-]+(?:\.[\w!#$%&^+/*=?'{|}~-]+)*@[A-z0-9-]+(?:\.[A-z0-9-]+)*$/gi;
    
    console.log(strEmail_1.match(regEmail_1));//ng.u.lee@163.c.o.m   

> ### Step5 顶级域名必须包含2-6个字符
在之前一个版本的正则表达式上添加了新要求，域名至少包含一个点(.)符号，且在最后边那个点(.)后面只能是字母；

    var strEmail_1 = "secondlevel@qq.com",
    	regEmail_1 = /^[\w!#$%&^+/*=?'{|}~-]+(?:\.[\w!#$%&^+/*=?'{|}~-]+)*@(?:[A-z0-9-]+\.)+[A-z]{2,6}$/gi;
    
    console.log(strEmail_1.match(regEmail_1));//ng.u.lee@163.c.o.m  


