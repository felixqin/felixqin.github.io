---
layout: post
category : Server
tagline: "Supporting tagline"
tags : [Server, WEB, nginx, auth]
---


# Nginx 认证实践



## 配置 nginx auth

```nginx
server {
        listen 80;
        server_name localhost;
        auth_request /auth;

        location /api/ {
            proxy_pass  http://172.18.0.1:8090;
        }

        location /auth {
            proxy_pass  http://172.18.0.1:8090/api/auth;
            proxy_pass_request_body off;
            proxy_set_header Content-Length "";
            proxy_set_header X-Original-URI $request_uri;
        }
}
```



## C++ REST SDK 实际 Basic Auth

```cpp
void handle_auth(web::http::http_request message)
{
    auto it = message.headers().find("Authorization");
    if (it != message.headers().end())
    {
        auto auth = it->second;
        ucout << auth << std::endl;
        if (auth.compare(0, 6, "Basic ") == 0)
        {
            auto auth_base = auth.substr(6);
            auto auth_data = utility::conversions::from_base64(auth_base);

            std::string username;
            auto it = auth_data.begin();
            it = Base::Split(it, auth_data.end(), ':', std::back_inserter(username));
            std::string password(it, auth_data.end());
            TRACEF("username(%s) password(%s)\n", username.c_str(), password.c_str());

            auto um = Base::GetComponentInstance<Manager::IUserManager>();
            std::string password0;
            um->GetPassword(username.c_str(), password0);
            TRACEF("password(%s) password0(%s)\n", password.c_str(), password0.c_str());
            if (password == password0)
            {
                message.reply(web::http::status_codes::OK);
                return;
            }
        }
    }

    web::http::http_response response;
    response.headers().add("WWW-Authenticate", "Basic realm=\"Closeli\"");
    response.set_status_code(web::http::status_codes::Unauthorized);
    message.reply(response);
}
```



## 参考链接

[Nginx 的两种认证方式](http://www.cnblogs.com/wangxiaoqiangs/p/6184181.html)





