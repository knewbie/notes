# git使用总结


## 本地仓库绑定远程仓库
本地仓库先单独建立，并有提交。这时才创建好远程仓库，并需要将本地仓库进行推送。

```
$ git init .
$ git remote add origin remote_url
$ git branch --set-upstream-to=origin/<branch> master
$ git pull --allow-unrelated-histories
$ git push -u origin master


```

