---
layout: post
category : WEB后端
tagline: "Supporting tagline"
tags : [WEB, REST, gSOAP, 资料]
---


# 智能设备REST开发



## 开源库资源

[Microsoft REST SDK](https://github.com/Microsoft/cpprestsdk)

[restbed](https://github.com/Corvusoft/restbed)

[restclient-cpp](https://github.com/mrtazz/restclient-cpp)



## 代码示例

基于 cpprest 的服务器核心代码

```c++
CRestServer::CRestServer()
    : m_listener(U("http://0.0.0.0:8090"))
{
    TRACEPOINT();
    m_listener.support(web::http::methods::GET, std::bind(&CRestServer::handle_get_or_post, this, std::placeholders::_1));
    m_listener.support(web::http::methods::POST, std::bind(&CRestServer::handle_get_or_post, this, std::placeholders::_1));
}

CRestServer::~CRestServer()
{
    TRACEPOINT();
    Stop();
}

bool CRestServer::Start()
{
    TRACEPOINT();
    m_listener.open();
    return true;
}

bool CRestServer::Stop()
{
    TRACEPOINT();
    m_listener.close().wait();
    return true;
}

void CRestServer::handle_get_or_post(web::http::http_request message)
{
    ucout << "Method: " << message.method() << std::endl;
    ucout << "URI: " << web::http::uri::decode(message.relative_uri().path()) << std::endl;
    ucout << "Query: " << web::http::uri::decode(message.relative_uri().query()) << std::endl << std::endl;
    message.reply(web::http::status_codes::OK, "ACCEPTED");
}

```





## 参考链接

[RESTful API 设计指南](http://www.ruanyifeng.com/blog/2014/05/restful_api.html)

[RESTful API 设计最佳实践](http://www.csdn.net/article/2013-06-13/2815744-RESTful-API)



