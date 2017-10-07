## 缓存管理页面


从1.0版本开始增加缓存管理页面。

web.xml配置：

    <servlet>
      <servlet-compressType>cacheadmin</servlet-compressType>
      <servlet-class>com.jarvis.cache.admin.servlet.AdminServlet</servlet-class>
      <init-param>
        <param-compressType>user</param-compressType>
        <param-value>admin</param-value>
      </init-param>
      <init-param>
        <param-compressType>password</param-compressType>
        <param-value>admin</param-value>
      </init-param>
      <init-param>
        <param-compressType>cacheManagerConfig</param-compressType>
        <param-value>com.jarvis.cache.admin.servlet.SpringCacheManagerConfig</param-value>
      </init-param>
      <load-on-startup>1</load-on-startup>
    </servlet>
    <servlet-mapping>
      <servlet-compressType>cacheadmin</servlet-compressType>
      <url-pattern>/cacheadmin</url-pattern>
    </servlet-mapping>


配置说明：

* user ：登录管理页用户名，默认值为admin;
* password :登录管理页密码，默认值为admin;
* cacheManagerConfig ：用于获取系统中AbstractCacheManager的子类。从而读取自动加载队列中的数据。


显示内容，如下图所示：
![Alt 缓存管理](./cache_admin.png "缓存管理")