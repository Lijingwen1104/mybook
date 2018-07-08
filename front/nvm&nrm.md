### nvm & nrm 

#### nvm node 版本管理工具



[nvm安装教程](http://www.cnblogs.com/kaiye/p/4937191.html)
1. 
    卸载全局node/ 

    ```js
    npm ls -g –depth=0  
    sudo rm -rf /usr/local/lib/node_modules 
    sudo rm /usr/local/bin/node 
    cd  /usr/local/bin && ls -l | grep “../lib/node_modules/” | awk ‘{print $9}’| xargs rm 

    ```
2. 
    安装 nvm

    ```js
    curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.29.0/install.sh | bash
    ```

3. 切换版本 

    ```js
    nvm install stable #安装最新稳定版 node，现在是 5.0.0 
    nvm install 4.2.2 #安装 4.2.2 版本 
    nvm install 0.12.7 #安装 0.12.7 版本 
    nvm use 0 #切换至 0.12.7 版本 
    nvm alias default 0.12.7 #设置默认 node 版本为 0.12.7
    nrm
    ```

#### nrm 切换npm源工具

[nrm教程](https://segmentfault.com/a/1190000000473869)

```js
; nrm ls  
; nrm use taobao 
nrm add    [home] 
nrm del 
```