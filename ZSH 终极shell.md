##ZSH 终极shell
（学习于：：：http://www.jianshu.com/p/24a0ded2e3ba）
查看已经安装的 shell
    cat /etc/shells

将用户默认shell 改为 zsh 
    chsh -s /bin/zsh

安装 “oh my zsh”
    wget —no-check-certificate http://install.ohmyz.sh -0 - | sh

配置zsh
 1、设置命名别名
    vi ~/.zshrc
    在文件尾部添加一下内容
    alias zshconfig='vi ~/.zshrc'
    alias vimconfig='vi ~/.vimrc'
    alias ll='ls -l'
    alias vi='vim'
    alias subl='open -a "Sublime Text"'
2、设置文件类型默认打开方式
    vi ~/.zshrc
3、文件尾部添加一下内容
    alias -s txt='vi’ 
    alias -s lua='vi’ 
    alias -s cpp='vi’ 
    alias -s c='vi’ 
    alias -s h='vi’ 
    alias -s zip='unzip’ 
    alias -s gz='tar -xzvf’
    alias -s tgz='tar -xzvf’ 
    alias -s bz2='tar -xjvf’
3、启用命令纠错功能
    vi ~/.zshrc
    找到 
    # Uncomment the following line to enable command auto-correction.
    # ENABLE_CORRECTION=“true"

zsh 回原来 执行 python 
    ipython +文件名称