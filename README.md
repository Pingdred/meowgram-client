## Meowgram

<p align="center">
  <img src="https://raw.githubusercontent.com/Pingdred/Meowgram/main/logo.png" alt="Meowgram logo"/>
</p>

Welcome to **Meowgram**, a Telegram client designed to seamlessly integrate with [Cheshire Cat Ai](https://cheshirecat.ai/).

---

## Prerequisites

Before you begin, make sure you have the following:

- Python `>= 3.10`
- A running instance of [Cheshire Cat](https://github.com/cheshire-cat-ai/core#quickstart) (version `>= 1.8.0`)
- Telegram **API Hash**
- A **Telegram bot TOKEN**, which you can get by creating a bot through [BotFather](https://core.telegram.org/bots/features#creating-a-new-bot)
- *(Optional)* **Docker** and **Docker Compose** if you plan to run the bot in a container.

### Obtaining the API Hash

1. Log in to your Telegram account using the developer phone number.
2. Navigate to **API Development Tools**.
3. In the **Create New Application** window, fill in the App title and Short name.
4. Click **Create Application**. Your **API Hash** is secret—**do not share it**.

---

## Installation

Follow these steps to get Meowgram up and running:

1. **Clone the repository:**

   ```bash
   git clone https://github.com/Pingdred/Meowgram.git
   ```

2. **Navigate to the project directory:**

   ```bash
   cd Meowgram
   ```

3. **Create a `.env` file** and set the following parameters. You can use the provided `.env.example` file as a template:

   ```toml
   # Telegram Credentials
   API_ID = "YOUR_API_ID"
   API_HASH = "YOUR_API_HASH"
   BOT_TOKEN = "YOUR-BOT-TOKEN"

   # Access Control (Comma-separated list of allowed Telegram IDs)
   ACCESS_LIST = "123456789,987654321" 

   # Cheshire Cat Connection
   CHESHIRE_CAT_URL = "localhost"
   CHESHIRE_CAT_PORT = 1865
   
   # Optional: Set this if your Cheshire Cat instance is protected by an API Key
   CHESHIRE_CAT_AUTH_KEY = "your_secret_websocket_key"
   ```

> **Important:**
> Ensure that your Cheshire Cat instance is running by following the [quick start guide](https://github.com/cheshire-cat-ai/core#quickstart). 
>
> **Auto-Registration:** 
> Meowgram will automatically register new allowed Telegram users into the Cheshire Cat's database upon their first interaction, ensuring seamless communication.

---

## Running Meowgram

You can run Meowgram using either standard Python or Docker.

### Option A: Standard Python

1. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
2. **Run the bot**:
   ```bash
   python src/main.py
   ```

### Option B: Docker Compose (Recommended)

To run Meowgram effortlessly in the background as a container:

1. Build and start the container:
   ```bash
   docker compose up -d --build
   ```
2. View the logs to ensure everything is working:
   ```bash
   docker logs meowgram_bot -f
   ```

---

## Meowgram Connect

**Meowgram Connect** is a plugin that enhances your chat experience with additional customization options, such as buttons for forms.

You can find **Meowgram Connect** in the plugin registry and install it directly from the Cheshire Cat Admin interface under the **Plugins** tab.

![Meowgram Connect](assets/Screenshot%20from%202024-05-13%2015-46-05.png)

---

## Media Support

Meowgram supports the media features introduced in Cheshire Cat `1.8.0`. Each plugin that utilizes these features is compatible with Meowgram to manage `images` and `audio`.

### Available Plugins for Speech-to-Text (STT)

To send voice notes via Meowgram, you need a **Speech-to-Text** (STT) plugin. Currently, the following plugins are supported:

- **[Whispering Cat](https://github.com/Furrmidable-Crew/Whispering_Cat)** This plugin enables speech-to-text functionality, allowing you to dictate messages seamlessly.

### Available Plugins for Text-to-Speech (TTS)

To receive voice notes, you need a **Text-to-Speech** (TTS) plugin. The following plugin is currently supported:

- **[TTS powered by OpenAI](https://github.com/Pingdred/openai-tts)** This plugin converts text into speech, allowing you to listen to received voice notes. To see the audio as a voice message, set `opus` as the Speech Format in the plugin settings.

### Add your Plugin

If you've developed your own plugin and would like to see it listed here, feel free to open an issue to propose the addition.