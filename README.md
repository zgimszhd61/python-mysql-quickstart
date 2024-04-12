在Mac上本地部署MySQL的过程可以通过两种主要方式进行：使用DMG安装包安装和使用Homebrew安装。以下是这两种方法的详细步骤：

## 使用DMG安装包安装MySQL

1. **下载MySQL安装包**：
   - 访问MySQL官方网站的下载页面（https://www.mysql.com/downloads/），滚动至页面底部，选择"DOWNLOADS" => "MySQL Community Server"，选择适合Mac的DMG安装包下载。

2. **安装MySQL**：
   - 双击下载的DMG文件开始安装。
   - 按照安装向导的提示点击“继续”，接受许可协议，选择安装位置（如果需要），并设置root用户的密码。安装过程中可能会提示选择密码加密方式，建议选择加强版密码加密。
   - 安装完成后，可以在“系统偏好设置”中找到MySQL，双击可以启动或停止MySQL服务，也可以进行卸载或配置。

3. **配置环境变量**：
   - 为了能在任何地方通过终端执行MySQL命令，需要配置环境变量。打开终端，执行`vim ~/.bash_profile`或`open ~/.bash_profile`，进入编辑模式。
   - 添加以下内容：
     ```
     export PATH=${PATH}:/usr/local/mysql/bin
     alias mysqlstart='sudo /usr/local/mysql/support-files/mysql.server start'
     alias mysqlstop='sudo /usr/local/mysql/support-files/mysql.server stop'
     ```
   - 保存并退出编辑器，然后执行`source ~/.bash_profile`使配置生效。

4. **启动MySQL并测试**：
   - 在终端输入`mysql -u root -p`，输入安装时设置的root密码，如果能成功登录，表示MySQL安装并配置成功[1]。

## 使用Homebrew安装MySQL

1. **安装Homebrew**（如果尚未安装）：
   - 打开终端，执行以下命令：
     ```bash
     /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
     ```
   - 安装完成后，执行`brew update`确保Homebrew是最新版本。

2. **通过Homebrew安装MySQL**：
   - 在终端执行`brew install mysql`，Homebrew会自动下载并安装MySQL。

3. **启动MySQL服务**：
   - 执行`brew services start mysql`启动MySQL服务。

4. **配置MySQL服务器**：
   - 执行`mysql_secure_installation`脚本，按照提示设置root密码，以及其他安全相关的配置，如删除匿名用户，禁止root用户远程登录等。

5. **测试MySQL安装**：
   - 执行`mysql -u root -p`，输入设置的密码，如果能成功登录，表示MySQL安装并配置成功[4]。

以上是在Mac上本地部署MySQL的两种主要方法。选择哪种方法取决于个人偏好，DMG安装包提供了图形界面的安装过程，而Homebrew则更适合喜欢使用命令行的用户。

Citations:
[1] https://juejin.cn/post/6844903831298375693
[2] https://blog.csdn.net/ljx1400052550/article/details/133048563
[3] https://juejin.cn/post/6982133511029276680
[4] https://www.sjkjc.com/mysql/install-on-macos/
[5] https://blog.csdn.net/bigge_L/article/details/118766906
[6] https://cloud.tencent.com/developer/article/1782220
[7] https://developer.aliyun.com/article/1148500
[8] https://blog.51cto.com/u_16213383/8456894
