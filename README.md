# Flask Web App · NEU

[![Python](https://img.shields.io/badge/Python-3.11-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-2.3.2-000000?logo=flask)](https://flask.palletsprojects.com/)
[![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-CI%2FCD-2088FF?logo=githubactions&logoColor=white)](https://github.com/features/actions)

一个用于演示 Flask 自动化测试与远程部署流程的轻量 Web 应用。推送到 `main` 后，GitHub Actions 会安装依赖、运行测试，并使用仓库 Secrets 连接目标服务器完成部署。

## 快速开始

```bash
python -m venv .venv
# Windows: .venv\Scripts\activate
# macOS/Linux: source .venv/bin/activate
pip install -r requirements.txt
python -m src.app
```

访问 `http://localhost:5000`，页面将显示 `Hello, NEU!`。

## 运行测试

```bash
python -m unittest discover -s tests -v
```

## CI/CD

工作流位于 `.github/workflows/cicd.yml`，包含：

1. 检出代码并配置 Python 3.11。
2. 安装依赖并执行测试。
3. 通过 SSH 拉取最新代码。
4. 重启 Supervisor 管理的 Flask 服务。

部署依赖 `TOUGE_SSH_PRIVATE_KEY` 与 `TOUGE_SERVER_IP` 两个 GitHub Actions Secrets。请勿把私钥或服务器凭据直接提交到仓库。

