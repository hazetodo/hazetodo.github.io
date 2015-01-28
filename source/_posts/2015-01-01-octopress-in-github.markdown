---
layout: post
title: "Octopress in github"
date: 2015-01-01 01:25:50 +0800
comments: true
categories: octopress
---

[Octopress](http://octopress.org/) 是一個很棒的 Blog 框架，我們可以很簡單把它放在 GitHub 上。

### 在 GitHub 上建立網頁伺服器

GitHub 有免費的靜態網頁伺服器可供使用，不過必須照它的規則來走。首先要去建立一個新的 repository，並命名為 xxxxx.github.io。
例如我的帳號為 hazetodo，那麼 repository name 就是 hazetodo.github.io
建立完成會有個 URL 為 https://github.com/hazetodo/hazetodo.github.io


### 安裝 Octopress

打開終端機，將 Octopress 的 [repository](https://github.com/imathis/octopress) 複製一份到本地端，並指定希望的資料夾名稱。 
```
git clone git://github.com/imathis/octopress.git [資料夾名稱]
```

然後進入剛建好的這個資料夾
```
cd [資料夾名稱]
```

安裝相關套件
```
bundle install
```

安裝預設主題
```
rake install
```
到這邊已安裝好 Octopress


### GitHub 頁面設定

接下來要做 GitHub 頁面的設定
```
rake setup_github_pages
```
`setup_github_pages` 將會請你輸入 GitHub repository 的 URL 來設定 GitHub pages。
像我就是 https://github.com/hazetodo/hazetodo.github.io


再來執行下面指令來產生部落格檔案
```
rake generate
```

接著 deploy 檔案到 GitHub pages
```
rake deploy
```

最後，將 source 也 push 到 GitHub repository。
``` 
git add .
git commit -m "你的訊息"
git push origin source
```
如果一切順利，你現在已經有了自己的部落格，而對應網址是 [使用者帳號].github.io。


### 新增文章

我們可以使用 `new_post` 來新增文章，這指令將會在 source/_posts/ 下面產生對應的檔案。
```
rake new_post["title"]
```
由於上面的 title 會被用來做為文章的檔案名稱，所以建議使用英文。

若打開每篇文章的內容會看到最上方會有一些設定資訊如下

```
---
layout: post 
title: "Octopress GitHub"                 # 標題
date: 2015-01-01 01:01:01 +0800           # 時間
comments: true                            # 是否開啟評論?
published: true                           # 是否發佈? 若否，將視為草稿不公開
categories: octopress                     # 文章所屬類別
---
```

我們將內容編寫於設定資訊的下方，而撰寫格式則是採用 [Markdown](http://markdown.tw/) 語法。

當撰寫文章時，我們可以新開一個終端機視窗並在專案資料夾下執行 `rake preview`，然後開啟瀏覽器連到 http://localhost:4000 進行預覽。
```
rake preview
```

當編輯完新文章後，執行 `rake generate` 產生部落格檔案，然後再將它們 deploy 到 GitHub pages
```
rake generate
rake deploy
```

最後，別忘了 push 對應的 source 到你的 GitHub repository!

