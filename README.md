#spring-oauth-server


<strong>Spring与Oauth2的整合示例</strong>

项目用Maven管理


使用的技术与版本号
<ol>
 <li>Spring (3.1.1.RELEASE)</li>
 <li>Spring Security (3.1.0.RELEASE)</li>
 <li>MyBatis (3.2.1)</li>
 <li>spring-security-oauth2 (1.0.5.RELEASE)</li>
 <li>Log4j (1.2.14)</li>
</ol>
<hr/>

<h3>
   Oauth客户端项目请访问 <a href="http://git.oschina.net/mkk/spring-oauth-client">spring-oauth-client</a>
</h3>
<h3>
   在线测试访问地址 <a href="https://andaily.com/spring-oauth-server/">https://andaily.com/spring-oauth-server/</a>
</h3>
<hr/>

<p>
<strong>如何使用?</strong>
<ol>
<li>
项目是Maven管理的, 需要本地安装maven(开发用的maven版本号为3.1.0), 还有MySql(开发用的mysql版本号为5.5)
</li>
<li>
<a href="http://git.oschina.net/shengzhao/spring-oauth-server/repository/archive?ref=master">下载</a>(或clone)项目到本地
</li>
<li>
创建MySQL数据库(如数据库名oauth2), 并运行相应的SQL脚本(脚本文件位于others/database目录),
<br/>
   运行脚本的顺序: initial_db.ddl -> oauth.ddl -> initial_data.ddl
</li>
<li>
修改<a href="http://git.oschina.net/shengzhao/spring-oauth-server/blob/master/src/main/resources/spring-oauth-server.properties">spring-oauth-server.properties</a>(位于src/main/resources目录)中的数据库连接信息(包括username, password等)
</li>
<li>
将本地项目导入到IDE(如Intellij IDEA)中,配置Tomcat(或类似的servlet运行服务器), 并启动Tomcat(默认端口为8080);
<br/>
注意将项目的 contextPath(根路径) 设置为 'spring-oauth-server'.
<br/>
   另: 也可通过maven package命令将项目编译为war文件(spring-oauth-server.war),
         将war放在Tomcat中并启动(注意: 这种方式需要将spring-oauth-server.properties加入到classpath中并正确配置数据库连接信息).
</li>
<li>
参考<a href="http://git.oschina.net/shengzhao/spring-oauth-server/blob/master/others/oauth_test.txt">oauth_test.txt</a>(位于others目录)的内容并测试之(也可在浏览器中访问相应的地址,如: http://localhost:8080/spring-oauth-server).
</li>
</ol>
</p>


<hr/>
<strong>grant_type</strong>
<br/>
说明Oauth支持的grant_type(授权方式)与功能
<ol>
    <li><code>authorization_code</code> -- 授权码模式(即先登录获取code,再获取token)</li>
    <li><code>password</code> -- 密码模式(将用户名,密码传过去,直接获取token)</li>
    <li><code>refresh_token</code> -- 刷新access_token</li>
    <li><code>implicit</code> -- 简化模式(在redirect_uri 的Hash传递token; Auth客户端运行在浏览器中,如JS,Flash)</li>
    <li><code>client_credentials</code> -- 客户端模式(无用户,用户向客户端注册,然后客户端以自己的名义向'服务端'获取资源)</li>
</ol>



<hr/>
<strong>帮助与改进</strong>
<ol>
<li>
<p>
 与该项目相关的博客请访问 <a target="_blank" href="http://blog.csdn.net/monkeyking1987/article/details/16828059">http://blog.csdn.net/monkeyking1987/article/details/16828059</a>
</p>
</li>
<li>
<p>
 如果在使用过程中遇到特殊的问题(如:如何将oauth_code存入数据库),请访问项目的 <a href="http://git.oschina.net/shengzhao/spring-oauth-server/wikis/pages">Wiki</a> 
 与 <a href="http://git.oschina.net/shengzhao/spring-oauth-server/attach_files">附件</a>. 
 <br/>
 我会把大家反馈的问题解决办法添加在这里.
 <br/>
 若在这两个地方没有找到解决办法的,
 欢迎发邮件到<a href="mailto:shengzhao@shengzhaoli.com">shengzhao@shengzhaoli.com</a>一起讨论.
</p>
</li>

<li>
<p>
 如果在使用项目的过程中发现任何的BUG或者更好的提议, 建议将其提交到项目的 <a href="http://git.oschina.net/shengzhao/spring-oauth-server/issues">Issues</a> 中, 
 我会一直关注并不断改进项目. 
</p>
</li>
</ol>

<hr/>
<strong>功能扩展</strong>
<ol>
    <li>
        <code>oauth_code存入数据库的配置</code>,  请下载文件 <a href="https://git.oschina.net/shengzhao/spring-oauth-server/attach_files/download?i=4858&u=http%3A%2F%2Ffiles.git.oschina.net%2Fgroup1%2FM00%2F00%2F31%2FcHwGbFQXzC-AeseiAAfnNw23X70580.jpg%3Ftoken%3De81934223d99a0fddc02639017b568a6%26ts%3D1421151523%26filename%3Doauth_code%E5%AD%98%E5%85%A5%E6%95%B0%E6%8D%AE%E5%BA%93%E7%9A%84%E9%85%8D%E7%BD%AE.jpg">oauth_code存入数据库的配置.jpg</a>
    </li>
    <li>
        <code>改变token过期的时间的配置</code>, 请下载文件<a href="https://git.oschina.net/shengzhao/spring-oauth-server/attach_files/download?i=6589&u=http%3A%2F%2Ffiles.git.oschina.net%2Fgroup1%2FM00%2F00%2F43%2FcHwGbFRpuk6ANN2CAANJ-Rkiz_c649.jpg%3Ftoken%3D686e6d5b1e9ab04446dbfeb977c3b7a1%26ts%3D1421151523%26filename%3D%E6%94%B9%E5%8F%98token%E8%BF%87%E6%9C%9F%E7%9A%84%E6%97%B6%E9%97%B4%E7%9A%84%E9%85%8D%E7%BD%AE.jpg">改变token过期的时间的配置.jpg</a>
    </li>
    <li>
        <code>自定义 grant_type</code>, 默认情况支持的grant_type包括 [password,authorization_code,refresh_token,implicit], 若不需要其中的某些grant_type,
        则可以修改 oauth_client_details 表中的 authorized_grant_types 字段的值;
        <br/>
        若想把整个Oauth服务修改来只支持某些grant_type, 请修改 <i>security.xml</i>文件中的
        <label>oauth2:authorization-server</label> 中的内容,将对应的 grant_type 注释或删掉即可
    </li>
    <li>
        <p>
            <code>如何刷新access_token(refresh_token)</code>, 在通过客户端(如移动设备)登录成功后返回的数据如下
            <br/>
            <pre>{"access_token":"3420d0e0-ed77-45e1-8370-2b55af0a62e8","token_type":"bearer","refresh_token":"b36f4978-a172-4aa8-af89-60f58abe3ba1","expires_in":43199,"scope":"read write"}
            </pre>
            <br/>
            若需要刷新获取新的token(一般在 expires_in 有效期时间快到时), 请求的URL类似如下
            <br/>
            <pre>http://localhost:8080/oauth/token?client_id=mobile-client&client_secret=mobile&grant_type=refresh_token&refresh_token=b36f4978-a172-4aa8-af89-60f58abe3ba1
            </pre>
            <br/>
            注意: refresh_token 参数值必须与登录成功后获取的 refresh_token 一致, 且grant_type = refresh_token
            <br/>
            另: 刷新token 需要 ClientDetails 支持 refresh_token 类型的 grant_type (默认是支持的)
        </p>
    </li>
</ol>


<hr/>
<h3>开发计划</h3>
<p>
从 0.3版本开始将项目的所有计划的开发内容列出来, 方便大家跟进, 也欢迎你加入.
<br/>
项目的开发管理使用开源项目 <a href="http://git.oschina.net/mkk/andaily-developer">andaily-developer</a>.
</p>
<ul>
       <li>
            <p>
                Version: <strong>0.3</strong> [finished]
                <br/>
                Date: 2015-05-14 / 2015-06-07
            </p>
            <ol>
                <li><p>#73 - Upgrade 'spring-security-oauth2' version to '2.0.6.RELEASE' (current: 1.0.5.RELEASE)      [CANCELED]</p></li>
                <li><p><del>#74 - oauth mysql ddl add create_time,  default is now()  </del></p></li>
                <li><p><del>#75 - Add user information API, for <a href="http://git.oschina.net/mkk/spring-oauth-client"><code>spring-oauth-client</code></a> project use
                    <pre>
                    URL: /unity/user_info
                    Login: Yes (ROLE_UNITY)
                    Data Format: JSON

                    URL: /m/user_info
                    Login: Yes (ROLE_MOBILE)
                    Data Format: JSON
                    </pre>
                    </del></p>
                </li>
                <li><p><del>#77 - User add Privilege domain.
                                  Addition initial two user: unityuser(ROLE_UNITY),mobileuser("ROLE_MOBILE).
                                  If default user, return all privilegs, otherwise return specify privilege(s) </del></p></li>
                <li><p><del>#78 - Initial 'sprint-oauth-client' project(maven), add sub-modules</del></p></li>
                <li><p><del>#91 - User log4j replace logback dependency </del></p></li>
                <li><p><del>#92 - Add database table column description. (添加数据库表的字段说明) </del></p></li>
                <li><p><del>#93 - 将默认的 oauth_code存入数据库(当前是存入内存) </del></p></li>
                <li><p><del> spring-oauth-server project add Bootstrap CSS  </del></p></li>
                <li><p><del>#95 - Add 'client-details' management; create/delete, show testing links<del></p></li>

            </ol>
       </li>
       <li>
            <p>
                Version: <strong>0.4</strong> [planning]
                <br/>
                Date: ------
            </p>
            <ol>
                <li><p>#97 - Fix custom access_token_validity,refresh_token_validity issue(#5)</p></li>
                <li><p>将项目添加到在线测试服务器</p></li>
                <li><p>若你有任何的功能或建议需要在新版本中实现, 请点此<a href="http://andaily.com/blog/?page_id=183">告诉我</a>.</p></li>
            </ol>
       </li>
</ul>
<br/>

<hr/>
<strong>数据库表字段说明</strong>
<p>
    在0.3版本中添加了<code>db_table_description.html</code>文件(位于/others目录), 用来说明数据库脚本文件<code>oauth.ddl</code>中各表,各字段的用途及使用场合.
    <br/>
    也可在线访问<a href="http://andaily.com/spring-oauth-server/db_table_description.html">http://andaily.com/spring-oauth-server/db_table_description.html</a>.
</p>



<hr/>
