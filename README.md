# Introduction
openAI ChatGPT integrated into slack with Python

## Getting Started
to use this repository, install required packages:

1. Python 3.11
using the following command:
```
pip3 install -r requirements.txt
```
2. ngrok - https://ngrok.com/ for your https to http tunnel between slack webhooks and bot (default port 4000)
4. Configure your slack bot (for example: https://chatimize.com/slack-chatbot/)
5. Configure config.py with necessary tokens
6. Configure your chat GTP API (https://platform.openai.com/signup)

default model = gpt-3.5-turbo - change in config
docs: https://platform.openai.com/docs/guides/chat


## Using
run SlackChatGPTBot.py and enjoy the experience

## Running
Bot communicates only in threads. Start a conversation with the bot, and the bot will reply in the thread. The bot does not talk in public channels (with minor tweaks in the code, this is possible) but instead turns the conversation into private. Local sqlite3 database is used to build the last 15 conversations (in each thread) to keep the context of the communication live (this can be easily changed in the code). 2000 Tokens are set as the token limit to get large contexts replied back - remember to change this if you use some other model with the ChatGPT API.

The same rules apply as with the chat.openai.com - if the response is cut in the middle just ask the bot to continue where the response was cut or ask to regenerate the answer and so on.

With code replies, proper formatting is supported automatically.
