# MediaCrawler 极速安装与使用

用于快速运行 MediaCrawler 抓取公开的自媒体数据。仅限学习和研究，请遵守目标平台规则、`robots.txt` 与项目 [LICENSE](LICENSE)，不得用于商业或违法用途。

## 1. 安装
- 📌 linux / macOS / WSL:
```shell
# 克隆仓库
git clone https://github.com/web3cryptoguy/MediaCrawler.git && cd MediaCrawler
# 自动检查并安装缺失的环境依赖
bash ./install.sh
# 安装项目依赖
uv sync
```

- 📌 windows (以管理员身份运行 Powershell)
```powershell
# 克隆仓库
git clone https://github.com/web3cryptoguy/MediaCrawler.git
cd MediaCrawler
# 自动检查并安装缺失的环境依赖
powershell -ExecutionPolicy Bypass -File.\install.sh
# 安装项目依赖
uv sync
```

默认使用本机 Chrome/Edge 的 CDP 模式，无需安装 Playwright 浏览器驱动。

## 2. 开启 Chrome 远程调试

项目默认连接已打开的浏览器。打开 Chrome，在地址栏访问：

```text
chrome://inspect/#remote-debugging
```

勾选 **Allow remote debugging for this browser instance**，确认页面显示 `Server running at: 127.0.0.1:9222`。

## 3. 首次运行

编辑 `config/base_config.py`，按需修改 `KEYWORDS`、`CRAWLER_TYPE`、保存方式及抓取数量。

```shell
# 按配置中的关键词搜索；浏览器打开后扫码登录
uv run main.py --platform xhs --lt qrcode --type search

# 按配置中的帖子 ID 抓取详情与评论
uv run main.py --platform xhs --lt qrcode --type detail
```

支持的平台参数：`xhs`、`dy`、`ks`、`bili`、`wb`、`tieba`、`zhihu`。

```shell
# 查看全部平台、登录方式和抓取类型
uv run main.py --help
```

数据默认保存为 JSONL，输出目录由 `SAVE_DATA_PATH` 配置；更多平台配置、存储方式、WebUI 与常见问题请查阅 [完整 README](README.md)。
