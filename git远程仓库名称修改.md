### git远程仓库名称修改

方法一：在本地修改远程仓库地址即可：
git remote set-url origin newAddress

方法二：先删除，然后添加地址：

git remote rm origin

git remote add origin newAddress

refer: https://www.cnblogs.com/anliux/p/10802615.html