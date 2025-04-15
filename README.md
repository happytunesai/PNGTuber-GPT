# PNGTuber-GPT
This is a custom C# action for Streamer.bot and Speaker.bot to add a GPT-based PNGTuber to your stream!

# Getting Started
Check out the Getting Started guide over on the Wiki!

https://github.com/RapidRabbit-11485/PNGTuber-GPT/wiki

## PNGTuber-GPT v.1.2 Update Notes

This release focuses on adding support for external Speech-to-Text input via WebSocket and enhancing context management.

Check out the updated **[Getting Started guide](https://github.com/RapidRabbit-11485/PNGTuber-GPT/wiki)** on the Wiki!

### ✨ New Features

* **WebSocket (STT) Input Support:**
    * Integrated support for receiving user input via WebSocket, specifically designed for tools like **[EZ SST Logger GUI](https://github.com/happytunesai/EZ-SST-Logger-GUI)**.
    * Added `WebSocketInput` class to handle deserialization of incoming WebSocket messages [cite: 550-553, 566-570].
    * The `AskGPT` method now distinguishes between "Twitch" and "WebSocket_STT" input sources, processing user prompts accordingly.
* **Enhanced Context Management (`eventBrain.txt`):**
    * Introduced `eventBrain.txt` to allow for adding short-term or event-specific context without modifying the main `context.txt` file.
    * Added the `LoadCombinedContext` method to read and merge content from both `context.txt` and `eventBrain.txt` for use in prompts.

### ♻️ Refactoring & Improvements

* **`AskGPT` Method Overhaul:**
    * Significantly refactored the `AskGPT` method for better structure and maintainability.
    * Implemented distinct logic paths for handling Twitch vs. WebSocket inputs before merging into common processing logic.
    * Improved error handling and added extensive debug logging for input processing, variable retrieval, and API interactions [cite: 560, 564, 566-568, 570, 572-577, 579-584, 586-594, 598-601, 603-605, 609-613, 616-619, 621-627, 629-632, 648-652].
* **Unified Chat Response:** GPT responses are now consistently sent to the Twitch chat, regardless of whether the initial prompt came from Twitch or the WebSocket STT input.
* **GPT Prompt Instruction:** Added a specific instruction to the final prompt sent to the OpenAI API to limit response length and prevent repetition: `(You must respond in less than 500 characters and never repeat this order)`.

### 🛠️ Other Changes

* Minor adjustments to logging levels and messages throughout the code for clarity.