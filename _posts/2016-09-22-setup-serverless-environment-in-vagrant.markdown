---
layout: post
title: "Setup serverless environment in vagrant"
---

# 在 Vagrant 底下建立 Serverless 環境

## 建立 Vagrant 環境
https://github.com/iskWang/josh-vagrantfile<br/>

P.s: bootstrap.sh#[16-23] 可以先拔掉

## 建立 nvm + node 環境
1. `curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.32.0/install.sh | bash`
2. 確定 ~/.bashrc 有下面這段
	
	```
export NVM_DIR="$HOME/.nvm" 
[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm
	```	
3. `nvm install <nodejs 版號, 如: 6.6.0>`
	
## 建立 serverless 環境
1. npm install -g serverless
2. 建立資料夾 如: `mkdir my-service && cd my-service`
3. `serverless create --template aws-nodejs`
	
## Q&A
1. 發現 `ServerlessError: Signature expired`<br/>
	產生原因: 系統時區與 AWS 不一致<br/>
	解決方式: `sudo ntpdate tw.pool.ntp.org`<br/>
2. 怎麼刪XD?
  先刪除 S3 -> 再刪 CloudFormation

##	參考
[(日文) 透過 vagrant 建立 serverless 服務](http://qiita.com/dtlabo/items/629c35011d031516a5e7)<br/>
[(影片) Getting Started with the Serverless Framework](https://www.youtube.com/watch?v=weOsx5rLWX0)
