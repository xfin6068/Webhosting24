# OpenAI API Key 的申请与测试全攻略

本文将详细介绍如何申请 OpenAI API Key 以及如何通过 `curl` 命令和 Python 代码进行初步测试，帮助你快速上手 OpenAI API 的使用。

---

## 申请 OpenAI API Key

### 准备工作

在申请 OpenAI API Key 之前，你需要准备以下三件套：

1. **VPN**：用于登录 Google 和 OpenAI 网站。
2. **Google Gmail 邮箱账号**：用于登录 OpenAI 平台。
3. **国外手机号**：用于接收验证码（可使用接码平台代替）。

### 申请步骤

1. **开启 VPN 全局代理**：将代理服务器地址设置为香港以外的国家，避免出现 “OpenAI’s services are not available in your country.” 的地区限制。
2. **访问 OpenAI API 页面**：打开 [OpenAI API](https://platform.openai.com/account/api-keys) 页面，点击 “Log in” 按钮，选择 “Continue with Google” 登录。
3. **填写注册信息**：填写姓名（First name、Last name）和生日，然后点击 “Continue”。
4. **验证手机号**：输入可以接收短信验证码的国外手机号码（推荐使用接码平台，如 SMS-Activate）。
5. **填写验证码**：发送验证码并填写，完成验证。
6. **选择使用用途**：在接下来的页面中选择使用 OpenAI 的主要用途（随便选择即可）。
7. **创建 API Key**：登录后，在 OpenAI API 页面点击 “+ Create new secret key” 按钮，生成 API Key。

**注意**：API Key 只在创建时显示，务必及时复制保存。如果需要使用，只能重新生成。

---

## 测试 OpenAI API

成功获取 API Key 后，你可以通过 `curl` 命令或 Python 代码测试 OpenAI API 的功能。

👉 [WildCard | 一分钟注册，轻松订阅海外线上服务](https://bbtdd.com/WildCard)

### 方法一：使用 `curl` 命令

如果你使用的是 Windows 系统，可以通过 Git Bash 运行 `curl` 命令。以下是具体步骤：

1. **设置环境变量**：在终端中输入 `export OPENAI_API_KEY="Your OpenAI API Key"`。
2. **发送请求**：使用以下 `curl` 命令发送 POST 请求：
   bash
   curl --http1.1 -H "Content-Type: application/json" -H "Authorization: Bearer $OPENAI_API_KEY" -d '{"model": "gpt-3.5-turbo", "messages": [{"role": "user", "content": "Say this is a test!"}]}' https://api.openai.com/v1/chat/completions
   

**参数说明**：

- `--http1.1`：使用 HTTP 1.1 协议。
- `-H`：传递定制头信息，如 `Content-Type` 和 `Authorization`。
- `-d`：传递 POST 数据，格式为 JSON 字典，必须包含 `"model"` 和 `"messages"` 两个字段。
- `"messages"`：描述对话的信息列表，每个字典包含 `"role"`（角色）和 `"content"`（内容）。

### 方法二：使用 Python 代码

通过 Python 代码调用 OpenAI API 也非常便捷，具体步骤如下：

1. **安装 `openai` 库**：在终端中输入 `pip install openai`。
2. **设置环境变量**：在 Anaconda PowerShell 中输入 `$Env:OPENAI_API_KEY = "Your OpenAI API Key"`。
3. **编写代码**：以下是一个简单的 Python 示例：
   python
   import openai

   openai.api_key = "Your OpenAI API Key"

   response = openai.ChatCompletion.create(
       model="gpt-3.5-turbo",
       messages=[{"role": "user", "content": "Say this is a test!"}]
   )

   print(response)
   

---

## 注意事项

1. **API Key 安全性**：API Key 一旦泄露，可能被滥用，请妥善保管。
2. **免费额度限制**：OpenAI API 提供一定的免费试用额度，可以通过左侧栏的 “Usage” 查看使用情况。
3. **多次尝试问题**：如果注册过程中遇到问题，请勿连续尝试，间隔一段时间后再试。

---

## 参考资料

1. [OpenAI API 官方文档](https://platform.openai.com/docs/api-reference)
2. [ChatGPT API 使用指南 (Python)](https://medium.com/geekculture/a-simple-guide-to-chatgpt-api-with-python-c147985ae28)
3. [PowerShell 设置环境变量](https://learn.microsoft.com/zh-cn/powershell/module/microsoft.powershell.core/about/about_environment_variables)