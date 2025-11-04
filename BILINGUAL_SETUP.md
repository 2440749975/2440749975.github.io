# 中英文双语学术主页配置说明

本文档说明如何使用和维护中英文双语学术主页。

## 📁 已修改/新增的文件

### 新增文件：
1. **`_pages/about-en.md`** - 英文版首页
2. **`_includes/language-switcher.html`** - 语言切换组件（页面内）
3. **`_data/navigation-en.yml`** - 英文版导航配置
4. **`assets/css/language-switcher.css`** - 语言切换器样式
5. **`BILINGUAL_SETUP.md`** - 本说明文档

### 修改的文件：
1. **`_config.yml`** - 网站标题改为中英文双语
2. **`_data/navigation.yml`** - 修正中文版导航链接
3. **`_includes/masthead.html`** - 修正左上角语言切换链接，支持中英文导航自动切换
4. **`_layouts/default.html`** - 集成页面内语言切换组件
5. **`_includes/head/custom.html`** - 添加CSS引用

## 🌐 页面访问地址

- **中文版**: https://2440749975.github.io/
- **英文版**: https://2440749975.github.io/en/

## ✏️ 如何修改内容

### 修改中文版内容
编辑文件：`_pages/about.md`

主要部分：
- 个人简介（第20行开始）
- 学历 `# 🎓 学历`
- 论文专利 `# 📝 论文专利`
- 荣誉奖项 `# 🏅 荣誉奖项`
- 学术会议 `# 🏛️ 学术会议`
- 工作实习 `# 💻 工作实习`

### 修改英文版内容
编辑文件：`_pages/about-en.md`

结构与中文版相同，对应的英文标题：
- About Me
- Education
- Publications
- Honors and Awards
- Academic Conferences
- Work Experience & Internships

### 修改个人信息
编辑文件：`_config.yml`

```yaml
title: "唐健 | Jian Tang"  # 网站标题
description: "电磁无损检测 | Electromagnetic Nondestructive Testing"

author:
  name: "唐健"
  email: "tangj@hust.edu.cn"
  googlescholar: "https://scholar.google.com/citations?user=WMkMTb4AAAAJ"
  # ... 其他社交链接
```

### 修改导航菜单
编辑文件：`_data/navigation.yml`

可以添加、删除或修改导航项：
```yaml
main:
  - title: "简介"
    url: "/#about-me"
  
  - title: "学历"
    url: "/#-xl"
  # ...
```

## 🎨 自定义样式

如需修改语言切换器的外观，编辑：`assets/css/language-switcher.css`

主要可调整参数：
```css
.language-switcher {
  text-align: right;    /* 对齐方式: left, center, right */
  padding: 12px 0;      /* 内边距 */
  font-size: 14px;      /* 字体大小 */
}

.language-switcher .lang-link {
  color: #52adc8;       /* 链接颜色 */
  /* ... */
}

.language-switcher .lang-link.active {
  color: #2e7d9a;       /* 当前语言颜色 */
  font-weight: bold;    /* 粗体 */
  /* ... */
}
```

## 🚀 部署方法

### 方法1：直接在GitHub提交（推荐）

```bash
# 在项目目录下
cd 2440749975.github.io

# 查看修改状态
git status

# 添加所有修改
git add .

# 提交修改
git commit -m "添加中英文双语支持"

# 推送到GitHub
git push origin master
```

### 方法2：本地测试后再部署

```bash
# 安装依赖（首次运行）
bundle install

# 启动本地服务器
bundle exec jekyll serve
# 或者在Windows上运行
./run_server.bat

# 访问 http://127.0.0.1:4000 测试

# 测试无误后提交
git add .
git commit -m "添加中英文双语支持"
git push origin master
```

## 📝 注意事项

1. **修改_config.yml后需要重启服务器**
   - 如果在本地测试，修改配置文件后必须重启Jekyll服务器

2. **图片路径问题**
   - 确保图片路径正确（如 `/images/xxx.png`）
   - 中英文版都使用相同的图片路径

3. **Google Scholar统计**
   - 确保在GitHub Secrets中设置了 `GOOGLE_SCHOLAR_ID`
   - 路径：Settings → Secrets and variables → Actions

4. **锚点链接**
   - 中文版使用中文锚点（如 `#-xl`）
   - 英文版使用英文锚点（如 `#-education`）
   - 导航菜单需要对应正确的锚点

5. **部署时间**
   - 推送到GitHub后，等待1-3分钟页面才会更新
   - 可以在仓库的Actions标签查看部署状态

## 🔧 常见问题

### Q1: 语言切换器不显示？
**A**: 检查以下几点：
1. `_layouts/default.html` 是否包含 `{% include language-switcher.html %}`
2. `_includes/head/custom.html` 是否引入了CSS文件
3. 清除浏览器缓存后重试

### Q2: 点击语言切换后404错误？
**A**: 
1. 确认 `_pages/about-en.md` 文件存在
2. 确认该文件的 `permalink: /en/` 设置正确
3. 等待GitHub Pages重新部署（1-3分钟）

### Q3: 样式显示不正常？
**A**: 
1. 检查CSS文件路径是否正确
2. 清除浏览器缓存
3. 使用浏览器开发者工具查看是否有CSS加载错误

### Q4: 导航菜单链接错误？
**A**: 
1. 检查 `_data/navigation.yml` 中的URL是否正确
2. 中文版链接应该以 `/` 开头
3. 确保锚点与页面中的实际锚点一致

### Q5: 本地运行报错？
**A**: 
```bash
# 更新依赖
bundle update

# 清理并重新构建
bundle exec jekyll clean
bundle exec jekyll serve
```

## 📊 文件结构总览

```
2440749975.github.io/
├── _config.yml                    # ✅ 已修改 - 双语标题
├── _data/
│   └── navigation.yml             # ✅ 已修改 - 添加English链接
├── _includes/
│   ├── head/
│   │   └── custom.html            # ✅ 已修改 - 添加CSS引用
│   └── language-switcher.html     # ✅ 新增 - 语言切换组件
├── _layouts/
│   └── default.html               # ✅ 已修改 - 集成切换器
├── _pages/
│   ├── about.md                   # ✅ 原有 - 中文版
│   └── about-en.md                # ✅ 新增 - 英文版
├── assets/
│   └── css/
│       └── language-switcher.css  # ✅ 新增 - 切换器样式
└── BILINGUAL_SETUP.md             # ✅ 新增 - 本文档
```

## 🎯 下一步建议

1. **个性化配置**
   - 修改 `_config.yml` 中的个人信息（如果需要）
   - 根据需要调整语言切换器的位置和样式

2. **内容完善**
   - 完善英文版的个人简介
   - 添加更多论文和项目信息
   - 更新最新的研究成果

3. **功能扩展**
   - 可以考虑添加更多语言（如日语、法语等）
   - 添加Google Analytics追踪
   - 集成评论功能

4. **SEO优化**
   - 为中英文页面添加不同的meta描述
   - 添加多语言标签支持

## 📧 技术支持

如遇到问题：
1. 查看Jekyll官方文档：https://jekyllrb.com/
2. 查看GitHub Pages文档：https://docs.github.com/en/pages
3. 查看原模板文档：https://github.com/RayeRen/acad-homepage.github.io

---

配置完成！🎉 现在你的学术主页支持中英文双语了。

