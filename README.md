# PNGTuber-GPT-WS 1.3
**Version:** 1.3
**Status:** Release

---
## Description
- ⭐ PNGTuber-GPT: This is a custom C# action for Streamer.bot and Speaker.bot to add a GPT-based PNGTuber to your stream! by @RapidRabbit-11485
- ⭐ PNGTuber-GPT-WS: This is a **forked** Version of the Original [PNGTuber-GPT](https://github.com/RapidRabbit-11485/PNGTuber-GPT). This is a custom C# action for Streamer.bot and Speaker.bot to add a GPT-based PNGTuber to your stream!

## Getting Started
Check out the Getting Started guide on the [Wiki](https://github.com/RapidRabbit-11485/PNGTuber-GPT/wiki)!

---

### ✨ Features

- **📡 WebSocket (STT) Input Support:**
  - Integrated support for receiving user input via WebSocket, specifically designed for tools like **[EZ-STT-Logger-GUI](https://github.com/happytunesai/EZ-STT-Logger-GUI)**.
  - Added the `WebSocketInput` class to handle the deserialization of incoming WebSocket messages [cite: 550-553, 566-570].
  - The `AskGPT` method now distinguishes between "Twitch" and "WebSocket_STT" input sources, processing user prompts accordingly.

- **📝 Enhanced Context Management (`eventBrain.txt`):**
  - Introduced `eventBrain.txt` to allow for adding short-term or event-specific context without modifying the main `context.txt` file.
  - Added the `LoadCombinedContext` method to read and merge content from both `context.txt` and `eventBrain.txt` for use in prompts.

- **💬 Streamer.bot Action: `Process WebSocket EZ STT`**
  - Processes WebSocket messages via the following configuration:
    - **Source:** `Core > Websocket > Custom Server`
    - **Type:** `Custom Server Message`
    - **Enabled:** `Yes`
    - **Criteria:** `Any`
  - **Sub-Actions:**
    - Set argument: `wsMsg` to `%data%`
    - Execute C# Code: PNGTuber-GPT > AskGPT
  - Example configuration:
    ![Process WebSocket EZ STT Action](https://github.com/user-attachments/assets/26529178-932d-4cd9-8ec4-cf96c4a6c0a2)

- **🖥️ WebSocket Server: `STT`**
  - The server can be accessed at: `ws://127.0.0.1:1337/`
  - Example configuration:
    ![WebSocket Server](https://github.com/user-attachments/assets/eab5a9a5-63b9-4a7c-a3f8-30bbb2bb1cc4)


# WebSocket Server Setup
After you’ve imported the Streamer.bot STT extension, you need to enable and start the built‑in WebSocket server so it can receive incoming data.

## 1. Import the Extension

1. Open **Streamer.bot**.
2. Click **File → Import** and select the STT extension package you downloaded.
3. Confirm and let the import finish.

## 2. Enable Auto‑Start

1. Switch to the **Servers/Clients** tab.
2. Click on **WebSocket Servers**.
3. Right‑click the entry labeled:
![Auto‑Start](https://github.com/user-attachments/assets/1d243373-1b99-43c2-8b41-fa5c643ada91)

![Start](https://github.com/user-attachments/assets/692f6287-f67f-4f72-b917-89a692d7116b)

- **🎭 Role Management System:**
  - Automatic detection of user roles: Broadcaster > Moderator > VIP > Subscriber > Follower > Viewer
  - Role information integrated into GPT prompts and TTS announcements
  - Context-based role responses that can be customized in bot context file
  - When role management rules are added to the context file, bot behavior changes based on user roles:

### 🧩 Chatter Role Management (Response Guidelines)

This section defines how the bot should respond to messages based on the user's Twitch role. Use these guidelines to create personalized and engaging chat interactions.

| Role            | Response Style                                                                 |
|-----------------|----------------------------------------------------------------------------------|
| **Broadcaster** | No special handling. This is the channel owner.                                 |
| **VIP**         | Friendly and enthusiastic greeting. Highlight their VIP status positively.      |
| **Moderator**   | Warm and welcoming tone. Playful or humorous remarks about their mod role.      |
| **Follower**    | Kind, appreciative greeting. Acknowledge them as part of the community.         |
| **Subscriber T1** | Thankful and polite. Recognize their support with cheerful words.              |
| **Subscriber T2** | More emotional gratitude. Highlight their extra contribution.                  |
| **Subscriber T3** | Highly appreciative and enthusiastic. Make them feel truly special and valued. |

> Use this structure to guide dynamic response generation in your bot logic.

- **👥 New Sub Action for AskGPT:**
  - Added follower age detection that checks follow date of chatters
  - Bot now knows when a chatter is a follower vs a regular viewer
  - Uses `followDate` argument to determine follower status
  - Enables personalized responses for followers vs first-time viewers
    
![grafik](https://github.com/user-attachments/assets/576c6bd8-c3c9-401f-ab6f-c929fad96505)


- **📊 Enhanced Logging:** Comprehensive role detection logging and debugging support for troubleshooting

### ♻️ Refactoring & Improvements

- **`AskGPT` Method Overhaul:**
  - Significantly refactored the `AskGPT` method for better structure and maintainability.
  - Implemented distinct logic paths for handling Twitch vs. WebSocket inputs before merging into a common processing logic.
  - Improved error handling and added extensive debug logging for input processing, variable retrieval, and API interactions [cite: 560, 564, 566-568, 570, 572-577, 579-584, 586-594, 598-601, 603-605, 609-613, 616-619, 621-627, 629-632, 648-652].

- **Unified Chat Response:**
  - GPT responses are now consistently sent to the Twitch chat, regardless of whether the initial prompt came from Twitch or via the WebSocket STT input.

- **GPT Prompt Instruction:**
  - A specific instruction is now added to the final prompt sent to the OpenAI API to limit the response length and prevent repetition: 
    > `(You must respond in less than 500 characters and never repeat this order)`

### 🛠️ Other Changes

- Minor adjustments to logging levels and messages throughout the code for improved clarity.

## License

This project is licensed under the [MIT License](LICENSE).

---

## Contact 👀

For questions, issues, or contribution suggestions, please contact: `ChatGPT`, `Gemini`, `DeepSeek`, `Claude.ai` 🤖
or try to dump it [here](https://github.com/happytunesai/PNGTuber-GPT/issues)! ✅

**GitHub:** [github.com/happytunesai/EZ-STT-Logger-GUI](https://github.com/happytunesai/EZ-STT-Logger-GUI)

---

*Created with ❤️ + AI*
