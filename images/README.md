# images/ 目录说明

## 这是什么
Shoka 主题的 `source/_data/images/` 是**主题静态资源的用户覆盖目录**。

## 为什么需要它
Shoka 主题自带一套图片资源（favicon、404 页面图、搜索图标、播放器素材等），放在
`themes/shoka/source/images/`。hexo-deployer-git 会把主题的 `source/` 整片
复制到 public/，**主题的同名文件会覆盖 `source/images/` 里同名的文件**——这是
为什么直接改 `source/images/favicon.ico` 永远不会生效。

## 解决
主题的 `scripts/generaters/images.js` 会**优先**把 `source/_data/images/` 里的
所有文件拷到 public/，然后才轮到主题的 source/。所以：

- 任何要替换主题图片的资源 → 放到这个目录
- 文件名必须跟主题里的同名（`favicon.ico`、`404.png`、`logo.svg` 等）
- 改完不用做什么特殊处理，正常 `hexo generate && hexo deploy` 就行

## 当前已覆盖
- `favicon.ico` - 站点图标（中心裁方、多分辨率的 194KB 真正 ICO）
- `my-favicon.ico` - 同上（`_config.shoka.yml` 里引用的是这个）
- 其它（404.png、search.png、logo.svg 等）是主题原版，**保留**作为基线，你想换时直接改这个目录的同名文件
