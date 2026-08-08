# 图片仓库

这是一个用于存放网页、油猴脚本和其他项目静态图片资源的公共仓库。

图片上传到这里以后，可以通过 **jsDelivr CDN** 生成稳定的公开访问链接。

## 推荐目录

```text
image/
├─ avatars/          # 头像
├─ backgrounds/      # 壁纸、背景图
├─ icons/            # 图标
├─ illustrations/    # 插画、立绘
├─ stickers/         # 贴纸、表情
└─ tools/            # 图片处理小工具
```

> GitHub 不保存真正的“空文件夹”。第一次往某个目录上传图片后，对应目录就会自动出现。

---

## 1. 上传前先转换图片

仓库内提供了一个浏览器版小工具：

```text
tools/image-converter.html
```

下载到电脑后双击打开即可使用，不需要安装软件，也不需要命令行。

推荐设置：

- 壁纸 / 插画 / 照片：`WebP`，画质 `85`
- 透明图标：优先 `WebP`；需要保留 PNG 时选择 `PNG`
- 最长边：一般可设为 `2000px`
- 文件名：建议使用英文、数字和短横线，例如 `night-beach.webp`

转换步骤：

1. 把图片拖进转换器。
2. 选择输出格式。
3. 选择准备上传到的目录，例如 `backgrounds` 或 `icons`。
4. 点击“开始转换”。
5. 下载转换后的图片。
6. 上传到本仓库对应目录。

---

## 2. 上传图片到 GitHub

例如需要上传一张夜晚海边背景图：

```text
backgrounds/night-beach.webp
```

在 GitHub 仓库页面中：

1. 进入对应目录；如果目录还不存在，可以在上传时直接创建路径。
2. 点击 **Add file → Upload files**。
3. 拖入转换后的图片。
4. 点击 **Commit changes**。

提交完成后，图片就已经存进 GitHub。

---

## 3. 生成 CDN 链接

本仓库的 jsDelivr CDN 基础地址：

```text
https://cdn.jsdelivr.net/gh/lingwangshu018/image@main/
```

只需要在后面加图片在仓库中的相对路径。

例如仓库文件：

```text
backgrounds/night-beach.webp
```

对应 CDN 链接：

```text
https://cdn.jsdelivr.net/gh/lingwangshu018/image@main/backgrounds/night-beach.webp
```

再例如：

```text
icons/wechat.webp
```

对应：

```text
https://cdn.jsdelivr.net/gh/lingwangshu018/image@main/icons/wechat.webp
```

---

## 4. 在油猴脚本 / 网页中使用

推荐只写一次基础地址：

```js
const IMAGE_CDN = 'https://cdn.jsdelivr.net/gh/lingwangshu018/image@main/';
```

然后按相对路径调用：

```js
const nightBeach = IMAGE_CDN + 'backgrounds/night-beach.webp';
const wechatIcon = IMAGE_CDN + 'icons/wechat.webp';
```

HTML 中也可以直接使用：

```html
<img src="https://cdn.jsdelivr.net/gh/lingwangshu018/image@main/icons/wechat.webp" alt="微信图标">
```

CSS 背景图：

```css
.phone-wallpaper {
  background-image: url('https://cdn.jsdelivr.net/gh/lingwangshu018/image@main/backgrounds/night-beach.webp');
}
```

---

## 5. 文件名建议

为了避免 URL 出现编码问题，推荐：

```text
night-beach.webp
lion-birthday.webp
wechat.webp
summer-room-01.webp
```

尽量避免：

```text
微信图片_20260808(最终版)!!!.png
```

转换器中的“自动安全命名”可以帮助整理文件名。

---

## 6. 图片更新后的缓存

jsDelivr 会缓存文件。

因此，已经公开使用的图片如果内容发生很大变化，推荐直接换一个新文件名，例如：

```text
night-beach-v2.webp
```

而不是一直覆盖旧的 `night-beach.webp`。

这样最不容易遇到“GitHub 已经更新，但页面暂时还显示旧图”的情况。

---

## 最简单的日常流程

```text
原图
 ↓
图片转换器
 ↓
WebP / PNG 成品
 ↓
上传到 image 仓库对应文件夹
 ↓
复制相对路径
 ↓
前面加 https://cdn.jsdelivr.net/gh/lingwangshu018/image@main/
 ↓
得到可以直接放进网页或油猴脚本的 CDN 地址
```
