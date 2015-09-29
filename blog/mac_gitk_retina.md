<!--
author: Bruce Yu
date: 2015-07-31
title: Mac Retina解决gitk模糊的问题
tags: Gitk versionControl Mac
category: GitBlog
status: publish
summary: sdfdsf
-->

##Mac Retina解决gitk模糊的问题
个人是gitk的忠实用户，但是在MAC下安装后，发现极其模糊

git在Mac下其实早就适配了高分辨率了，Patch如下：

https://gist.githubusercontent.com/cynthia/5f2355a87c2f15d96dbe/raw/6727e73a007b0efabf55dd065e588467ffccc016/wish_app_info_plist.patch

我们只需要把这里面最为关键的

    <key>NSHighResolutionCapable</key>
        <true/>
复制到Info.plist文件里面就可以了

    vim /System/Library/Frameworks/Tk.framework/Versions/Current/Resources/Wish.app/Contents/Info.plist
然后在</dict>前面加上上面的配置。
这之后，我们还需要更新一下Wish.app程序
我是这样做的：

    cp Wish.app WishBackup.app
    rm -rf Wish.app
    cp WishBackup.app Wish.app