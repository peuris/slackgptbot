# Introduction
OpenAI ChatGPT integrated into Slack with Python. This bot allows you to interact with ChatGPT directly from your Slack workspace.

## Getting Started
To use this repository, install the required packages:

- Python +3.10 with the latest additions is mandatory for improved garbage collection (GC streamline).
- Install required libraries using the following command:

```
pip3 install -r requirements.txt
```

- ngrok (https://ngrok.com/) for HTTPS to HTTP tunneling between Slack webhooks and the bot (default port 4000).
- or use certbot if you have public DN(S) that can be used with the bot
- Configure your Slack bot. For example, see [Chatimize's Slack Chatbot Guide](https://chatimize.com/slack-chatbot-guide/).

## Configuration
Update the `config.py` file with your specific configurations:

- `ENCRYPTION_FILE`: The file name for storing the encryption key.
- `ENCRYPTION_KEY`: Your specific encryption key.
- `ENCRYPTION_SET`: Boolean flag to enable or disable encryption.
- `OPENAI_API_KEY`: Your OpenAI API key.
- `OPENAI_ENGINE`: Set to "gpt-4-1106-preview" or your desired model.
- `SLACK_API_TOKEN` and `SLACK_BOT_TOKEN`: Tokens for Slack API and Bot integration.
- `VERIFICATION_TOKEN`: Token for verifying requests from Slack.

## SlackChatGPTBot.py
This Python script handles the integration of the ChatGPT model with your Slack workspace. Key features include:

- Streamlined garbage collection for improved performance.
- Use of Flask for creating the bot server.
- Exception handling and logging for robustness.
- Integration with Slack's WebClient and handling Slack API errors.
- Database operations for managing conversations and user data (if applicable).

Ensure you have all the necessary dependencies installed as listed in `requirements.txt`.

## Running the Bot
To run the bot:

1. Start the Flask server by running `SlackChatGPTBot.py`.
2. Use ngrok or a similar service to expose your local server to the internet.
   or use certbot and DNS and use https endpoint
3. Set the ngrok URL in your Slack application's event subscriptions.
   or use certbot and DNS and use https endpoint

## Running
Bot communicates only in threads. Start a conversation with the bot, and the bot will reply in the thread. The bot does not talk in public channels (with minor tweaks in the code, this is possible) but instead turns the conversation into private. Local sqlite3 database is used to build the last 15 conversations (for each thread) to keep the context of the communication live (this can be easily changed in the code). 4069 Tokens are set as the token limit to get large contexts replied back - remember to change this if you use some other model with the ChatGPT API.

The same rules apply as with the chat.openai.com - if the response is cut in the middle just ask the bot to continue where the response was cut or ask to regenerate the answer and so on.

With code replies, proper formatting is supported automatically.
