## 简单的使用方法：


创建虚拟环境

使用pip安装第三方依赖

修改settings.example.py文件为settings.py

修改其中的发送邮件设置为自己的账号和第三方登录密钥

注意切换到当前目录

运行python manage.py migrate 命令，创建数据库和数据表

运行python manage.py runserver  --insecure 启动服务器


![示例图片](https://ftp.bmp.ovh/imgs/2021/02/6784472bec14870f.png ) 


路由设置：

```
from django.contrib import admin
from django.urls import path
from login import views
from django.urls import include



urlpatterns = [
    path('baga/', admin.site.urls),
    path('admin/', views.hack),

    path('index/', views.index),
    path('login/', views.login),
    path('register/', views.register),
    path('logout/', views.logout),
    path('captcha/', include('captcha.urls')), # 增加这一行
    path('confirm/', views.user_confirm),
]

handler404 = views.page_not_found
handler500 = views.page_error

```

## settings配置：
``````

1. 默认使用Sqlite数据库
2. LANGUAGE_CODE = 'zh-hans'  #语言
3. TIME_ZONE = 'Asia/Shanghai'   #时区
4. USE_TZ = False

# 邮件服务设置
5. EMAIL_BACKEND = 'django.core.mail.backends.smtp.EmailBackend'
6. EMAIL_HOST = 'smtp.sina.com'
7. EMAIL_PORT = 25
8. EMAIL_HOST_USER = 'xxxx@sina.com' #填上自己的账号
9. EMAIL_HOST_PASSWORD = 'xxxxx'        #自己的第三方登录密码

# 注册有效期天数
10. CONFIRM_DAYS = 7

``````