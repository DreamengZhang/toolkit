# 工具箱 toolkit

本地小工具集合：Flask API + React 前端。在 Projects 控制台（3999）启动 **toolkit-api**（5010）与 **toolkit-web**（5174）。

```
toolkit/
  backend/    # API，python run_api.py
  frontend/   # 页面，npm run dev
```

## 环境准备

```powershell
cd E:\projects\toolkit\backend
python -m venv .venv
.\.venv\Scripts\pip install -r requirements.txt
copy .env.example .env
# 填写 MYSQL_PASSWORD 后执行 sql\schema.sql

cd E:\projects\toolkit\frontend
npm install
```

控制台启动后访问 http://127.0.0.1:5174/ 。API 健康检查：http://127.0.0.1:5010/api/health

## PDF 转换

路径：首页 → **PDF 转换**

1. 点击上传区选择 PDF，或拖入文件。
2. 选择输出格式（PNG / JPEG / Word / 文本）；图片格式可选 DPI。
3. 点击 **转换**，下载 ZIP 或单文件。

需 API 与 MySQL 工具列表正常；转换本身主要依赖本机 PDF 库。

## 图片拼接

路径：首页 → **图片拼接**

1. 每行 4 格，点击 **+** 选图，或使用顶部 **批量添加** / 拖拽多图（从左到右、从上到下填空，不够自动加行）。
2. 可 **拖拽** 已有图片到其他格子交换位置。
3. 设置间距，点击 **生成拼接图**；结果为等宽等高格子、等距排列（居中裁剪填满）。
4. **下载 PNG** 保存。

## 图片水印

路径：首页 → **图片水印**

### 添加水印

1. 上传区选择原图。
2. **文字**：填写内容、字号、颜色、位置、不透明度；可勾选平铺。
3. **图片**：切换类型为图片，再上传水印图，可调相对宽度与不透明度。
4. 点击 **生成**，预览后 **下载 PNG**。

### 去除水印

1. 切换到 **去除水印**，上传原图。
2. 在预览上拖拽框选水印区域（可多块，可贴边拖到画布边缘）。
3. 点击 **去除**，再 **下载 PNG**。适合局部半透明水印；非 AI 全图消除。

## 二维码生成

路径：首页 → **二维码生成**

1. 在 **内容** 中输入网址或任意文本。
2. 点击 **生成**，预览二维码并 **下载 PNG**；可用手机扫描验证。

## 取色器

路径：首页 → **取色器**（纯前端，可不启 API）

1. 上方 **上传图片**，在预览图上 **点击** 任意位置吸取该点颜色。
2. 下方色块旁：**拾色**（提示从图片取色）、窄 **HEX** 可手改、**复制** 复制 HEX。

## 端口与变量

| 服务 | 端口 | 说明 |
|------|------|------|
| toolkit-web | 5174 | Vite 开发服务器 |
| toolkit-api | 5010 | `TOOLS_API_PORT` |

后端 `.env`：`MYSQL_*`、`UPLOAD_MAX_MB`（上传上限）等见 `backend/.env.example`。
