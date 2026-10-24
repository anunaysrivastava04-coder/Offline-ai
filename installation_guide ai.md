# How to Run an Offline AI from a USB Pendrive

**Created by: Anunay Srivastava**

*This guide is based on the instructions detailed in the document "Run Offline AI from a USB Pendrive_2.docx".*

This repository provides a step-by-step guide to setting up a completely offline, portable AI that runs directly from a USB pendrive using Llamafile and a GGUF model.

## 🔗 Important Links and Resources
Before starting, you may need to download resources from the following links:
*   **Fine-tuned Thinking Model:** [pramodlohra/Qween3_4B_thinking_finetune](https://huggingface.co/pramodlohra/Qween3_4B_thinking_finetune)
*   **Llamafile Engine Release:** [Mozilla AI llamafile v0.10.6](https://github.com/mozilla-ai/llamafile/releases/tag/0.10.6)
*   **Qwen GGUF Models:** [Qwen3-8B-GGUF Repository](https://huggingface.co/Qwen/Qwen3-8B-GGUF/tree/main)

---

## Step 1 — Prepare the USB Pendrive
1. Connect your USB pendrive to your PC.
2. Format the pendrive.
3. Select **exFAT** as the file system.
4. Make sure the pendrive has enough free space for the AI model. (The required storage depends on the model you choose).

## Step 2 — Download Llamafile
1. Search for Llamafile GitHub (or use the link provided above).
2. Open the official repository/release page.
3. Download the required Windows `.exe` file.
   * *For example:* `llamafile-0.10.5.exe` (or the newer `0.10.6` version).

## Step 3 — Download an AI Model
1. Download a compatible GGUF model from the links above.
   * *For example:* `qwen3-4b-thinking-2507.Q4_K_M.gguf`
2. Keep the `.gguf` file in the same folder as the llamafile executable.

**Your folder should look like:**
```text
Pendrive
│
├── llamafile-0.10.5.exe
└── qwen3-4b-thinking-2507.Q4_K_M.gguf
```

## Step 4 — Create the Start.bat File
1. Right-click inside the folder.
2. Select **New → Text Document**.
3. Open the new text file in Notepad.
4. Add this command:
   ```cmd
   .\llamafile-0.10.5.exe --server --model "qwen3-4b-thinking-2507.Q4_K_M.gguf" --ctx-size 2048
   ```
5. Click **Save As**.
6. Change "Save as type" to **All Files**.
7. Name the file: `Start.bat`
8. *Make sure Windows does not save it as: `Start.bat.txt`*

## Step 5 — Final Folder Structure
Your pendrive should now look like this:
```text
Pendrive
│
├── llamafile-0.10.5.exe
├── qwen3-4b-thinking-2507.Q4_K_M.gguf
└── Start.bat
```

## Step 6 — Start the AI
1. Simply double-click: `Start.bat`
2. A Command Prompt window will open and the model will start loading.
3. Wait until the server successfully starts.
4. Then open the local address shown by the server in your browser.
   * *Usually:* `http://localhost:8080`

## Step 7 — Understanding `--ctx-size`
The `--ctx-size` option controls the context size of the AI. In simple words, it controls approximately how much text/conversation the model can keep in its active context.

**Example:** `--ctx-size 2048`
Here, 2048 is the context size. You can change it depending on your available RAM.

### Common Values
*   `1024`: (`--ctx-size 1024`) Uses less memory but provides a smaller context.
*   `2048`: (`--ctx-size 2048`) A good lightweight option.
*   `4096`: (`--ctx-size 4096`) Provides more context but requires more memory.
*   `8192`: (`--ctx-size 8192`) Useful for longer conversations and larger prompts, but requires more memory.
*   `16384`: (`--ctx-size 16384`) Requires significantly more memory.
*   `32768`: (`--ctx-size 32768`) Very large context and considerably higher memory requirements.

**Important:** There is no single value that works for every PC. Higher context size generally requires more memory. If you get an insufficient memory error, reduce the context size.

## Step 8 — Recommended Settings
*   **Start with:** `--ctx-size 2048`
*   **If your PC handles it successfully, try:** `--ctx-size 4096`
*   **Then:** `--ctx-size 8192`

Use the highest value that your computer can run reliably. For a low-RAM computer, `2048` is a safer starting point.

## Step 9 — Changing the AI Model
You can replace the model file with another compatible GGUF model.
For example, if your model is: `my-model.Q4_K_M.gguf`
Then change:
```cmd
--model "qwen3-4b-thinking-2507.Q4_K_M.gguf"
```
to:
```cmd
--model "my-model.Q4_K_M.gguf"
```
*The model name in the command must exactly match the actual file name.*

## Step 10 — Changing the Llamafile Version
If you download a different version of llamafile, change `.\llamafile-0.10.5.exe` to the actual `.exe` file name.
For example: `.\llamafile-0.10.6.exe` or `.\llamafile-0.10.7.exe`

### Complete Start.bat Example
For the Qwen model used in this setup:
```cmd
.\llamafile-0.10.5.exe --server --model "qwen3-4b-thinking-2507.Q4_K_M.gguf" --ctx-size 2048
```
If you want a larger context:
```cmd
.\llamafile-0.10.5.exe --server --model "qwen3-4b-thinking-2507.Q4_K_M.gguf" --ctx-size 4096
```
Or:
```cmd
.\llamafile-0.10.5.exe --server --model "qwen3-4b-thinking-2507.Q4_K_M.gguf" --ctx-size 8192
```

## Important Notes
*   Keep the `.exe`, `.gguf`, and `Start.bat` in the correct locations.
*   The model filename in `Start.bat` must match the actual filename.
*   Use `.\` instead of `./` in a normal Windows `.bat` file.
*   `--ctx-size` controls the context size and affects memory usage.
*   If you get insufficient memory, lower the `--ctx-size` value.
*   A larger context does not automatically make the model more intelligent.
*   The AI model itself can run locally without an internet connection.
*   Keep the Command Prompt window open while using the AI server.
*   Do not run unknown `.exe` files from untrusted sources.

---

## Final Setup Refresher
```text
Pendrive
│
├── llamafile-0.10.5.exe
├── qwen3-4b-thinking-2507.Q4_K_M.gguf
└── Start.bat
```
**Double-click `Start.bat` → Wait for the model → Open `http://localhost:8080` → Start chatting.**