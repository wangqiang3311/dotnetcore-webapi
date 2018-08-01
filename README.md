# dotnetcore-webapi

    1、实现了跨域访问

    2、可以查看接口文档

    3、修改了跨域策略，任何网站的任何请求方法，如get、post等都可以访问接口

    4、git账号设置，没有必要每次输入用户名和密码  git config --global credential.helper wincred

    5、edge和firefox的跨域请求失败，原因待查明，chrom浏览器ok

# 自托管配置

  1、在Main方法中添加如下代码：
  
    var config = new ConfigurationBuilder()
                      .SetBasePath(Directory.GetCurrentDirectory())
                      .AddJsonFile("hosting.json", optional: true)
                      .Build();

            var host = new WebHostBuilder()
                .UseKestrel()
                .UseConfiguration(config)
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseIISIntegration()
                .UseStartup<Startup>()
                .Build();

            host.Run();
            
            
 2、在网站根目录下添加hosting.json
 
   {
    "server.urls": "http://localhost:60000;http://localhost:60001"
   }
  
