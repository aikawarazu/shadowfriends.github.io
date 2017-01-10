RVM是Ruby的版本管理器工具。
1、安装RVM
# sudo apt-get curl
# curl -L https://get.rvm.io | bash -s stable
# source ~/.rvm/scripts/rvm
2、安装RVM的环境依赖
# rvm requirements
3、安装Ruby
# rvm install ruby
如果想在Ubuntu上安装多个Ruby版本，那么可以使用下面的命令来指定使用rvm作为默认的Ruby版本管理。
# rvm use ruby --default
检查当前成功安装的Ruby版本
# ruby -v
安装gems
# gem list
# gem install [gem-name]
比如gem-name可以写sass
如果要从本地安装gems，命令如下：
# gem install --local [path of gem file]
可以使用命令更新已安装的gems，命令如下：
# gem update --system
或者
# gem update

-- 参考：http://blog.csdn.net/chszs/article/details/42462517
