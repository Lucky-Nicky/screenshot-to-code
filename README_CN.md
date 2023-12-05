# 截图转代码

这个简单的应用程序可以将截图转换为代码（HTML/Tailwind CSS、React、Vue或Bootstrap）。它使用GPT-4 Vision生成代码，使用DALL-E 3生成类似的图像。现在您还可以输入URL来克隆一个实时网站！

https://github.com/abi/screenshot-to-code/assets/23818/6cebadae-2fe3-4986-ac6a-8fb9db030045

请参阅下面的[示例](#-示例)部分以获取更多演示。

## 🚀 试一试！

🆕 [在这里试用](https://screenshottocode.com)（请使用您自己的OpenAI密钥 - **您的密钥必须具有访问GPT-4 Vision的权限。有关详细信息，请参阅下面的[常见问题](#%EF%B8%8F-常见问题)部分**）。或者请参阅下面的[入门指南](#-入门指南)以获取本地安装说明。

## 🌟 最近更新

- 11月30日 - 深色模式，Ionic输出代码（感谢[@dialmedu](https://github.com/dialmedu)），设置OpenAI基本URL
- 11月28日 - 🔥 🔥 🔥 自定义堆栈：React、Bootstrap或TailwindCSS
- 11月23日 - 发送当前复制版本的截图（有时可以提高后续生成的质量）
- 11月21日 - 在代码编辑器中编辑代码并实时预览更改（感谢[@clean99](https://github.com/clean99)）
- 11月20日 - 粘贴URL进行截图和克隆（需要[ScreenshotOne免费API密钥](https://screenshotone.com?via=screenshot-to-code)）
- 11月19日 - 支持深色/浅色代码编辑器主题 - 感谢[@kachbit](https://github.com/kachbit)
- 11月16日 - 添加了一个设置，可以禁用DALL-E图像生成（如果您不需要的话）
- 11月16日 - 在应用程序内直接查看代码
- 11月15日 - 您现在可以指示AI根据您的要求更新代码。如果AI搞乱了一些样式或错过了某个部分，这很有帮助。

## 🛠 入门指南

该应用程序具有React/Vite前端和FastAPI后端。您将需要一个具有访问GPT-4 Vision API权限的OpenAI API密钥。

运行后端（我使用Poetry进行软件包管理 - 如果您没有，请执行`pip install poetry`）：

```bash
cd backend
echo "OPENAI_API_KEY=sk-your-key" > .env
poetry install
poetry shell
poetry run uvicorn main:app --reload --port 7001
```

运行前端：

```bash
cd frontend
yarn
yarn dev
```

打开 http://localhost:5173 使用该应用程序。

如果您希望在不同的端口上运行后端，请在`frontend/.env.local`中更新VITE_WS_BACKEND_URL

出于调试目的，如果您不想浪费GPT4-Vision的配额，可以以模拟模式运行后端（它会流式传输预先录制的响应）：

```bash
MOCK=true poetry run uvicorn main:app --reload --port 7001
```

## Docker

如果您的系统上安装了Docker，在根目录中运行：

```bash
echo "OPENAI_API_KEY=sk-your-key" > .env
docker-compose up -d --build
```

该应用程序将在 http://localhost:5173 上运行。请注意，您无法使用此设置开发应用程序，因为文件更改不会触发重新构建。

## 🙋‍♂️ 常见问题

- **我在设置后端时遇到错误。我该如何解决？** [请尝试这个](https://github.com/abi/screenshot-to-code/issues/3#issuecomment-1814777959)。如果仍然不起作用，请提出一个问题。
- **如何获取OpenAI API密钥？** 请参阅 https://github.com/abi/screenshot-to-code/blob/main/Troubleshooting.md
- **如何提供反馈？** 欢迎提出反馈、功能请求和错误报告，请提出一个问题或在[Twitter](https://twitter.com/_abi_)上联系我。

## 📚 示例

**纽约时报**

| 原始截图                                                                                                                                                        | 复制品                                                                                                                                                         |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| <img width="1238" alt="Screenshot 2023-11-20 at 12 54 03 PM" src="https://github.com/abi/screenshot-to-code/assets/23818/3b644dfa-9ca6-4148-84a7-3405b6671922"> | <img width="1414" alt="Screenshot 2023-11-20 at 12 59 56 PM" src="https://github.com/abi/screenshot-to-code/assets/23818/26201c9f-1a28-4f35-a3b1-1f04e2b8ce2a"> |

**Instagram页面（不包含泰勒·斯威夫特的图片）**

https://github.com/abi/screenshot-to-code/assets/23818/503eb86a-356e-4dfc-926a-dabdb1ac7ba1

**Hacker News**，但一开始颜色有误，所以我们稍微调整了一下

https://github.com/abi/screenshot-to-code/assets/23818/3fec0f77-44e8-4fb3-a769-ac7410315e5d

## 🌍 托管版本

🆕 [在这里试用](https://screenshottocode.com)（请使用您自己的OpenAI密钥 - **您的密钥必须具有访问GPT-4 Vision的权限。有关详细信息，请参阅[常见问题](#%EF%B8%8F-常见问题)部分**）。或者请参阅[入门指南](#-入门指南)以获取本地安装说明。

[!["Buy Me A Coffee"](https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png)](https://www.buymeacoffee.com/abiraja)

常见问题：
1.拉取Python包失败，解决办法，加上清华源镜像库
2. .env文件不存在，在后端文件建.env文件
