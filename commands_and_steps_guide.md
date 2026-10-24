# 💻 Detailed Steps & Commands Guide

This guide provides an in-depth look at the commands used in this project, how to customize them, and advanced arguments you can add to your `Start.bat` file to change how Llamafile operates.

---

## 1. The Base Command Structure

The core of this project relies on a single command inside the `Start.bat` file. 

```bat
.\llamafile-0.10.5.exe --server --model "qwen3-4b-thinking-2507.Q4_K_M.gguf" --ctx-size 2048
```

### Breakdown of the Command:
* `.\llamafile-0.10.5.exe` : This tells Windows to execute the Llamafile application located in the current directory (`.\`).
* `--server` : Starts the built-in web server and user interface so you can chat via your browser.
* `--model "filename.gguf"` : Specifies the exact AI model file to load. **This must match your downloaded file exactly.**
* `--ctx-size 2048` : Allocates memory for the conversation context (how much it can remember at once). 

---

## 2. Context Size Commands

To adjust the memory and conversation length, modify the `--ctx-size` number.

**For Low-End PCs (4GB - 8GB RAM):**
```bat
.\llamafile-0.10.5.exe --server --model "qwen3-4b-thinking-2507.Q4_K_M.gguf" --ctx-size 1024
```
```bat
.\llamafile-0.10.5.exe --server --model "qwen3-4b-thinking-2507.Q4_K_M.gguf" --ctx-size 2048
```

**For Mid-Range PCs (16GB RAM):**
```bat
.\llamafile-0.10.5.exe --server --model "qwen3-4b-thinking-2507.Q4_K_M.gguf" --ctx-size 4096
```
```bat
.\llamafile-0.10.5.exe --server --model "qwen3-4b-thinking-2507.Q4_K_M.gguf" --ctx-size 8192
```

**For High-End PCs (32GB+ RAM):**
```bat
.\llamafile-0.10.5.exe --server --model "qwen3-4b-thinking-2507.Q4_K_M.gguf" --ctx-size 16384
```

---

## 3. Advanced Commands & Network Settings

You can add additional "flags" to your command to change the server's behavior.

### Change the Port (Default is 8080)
If port 8080 is already in use by another application on your PC, you can change it using `--port`.
```bat
.\llamafile-0.10.5.exe --server --model "qwen3-4b-thinking-2507.Q4_K_M.gguf" --ctx-size 2048 --port 8081
```
*(You would then access the AI by going to `http://localhost:8081` in your browser).*

### Allow Access from Other Devices (LAN)
By default, the AI is only accessible from the computer the pendrive is plugged into (localhost / `127.0.0.1`). If you want to access the AI from your phone or another computer on the same Wi-Fi network, use `--host 0.0.0.0`.
```bat
.\llamafile-0.10.5.exe --server --model "qwen3-4b-thinking-2507.Q4_K_M.gguf" --ctx-size 2048 --host 0.0.0.0
```
*(You will need to find the host computer's local IP address, e.g., `192.168.1.5`, and type `http://192.168.1.5:8080` into your phone's browser).*

### Skip Browser Auto-Open
By default, Llamafile will attempt to automatically open your default web browser when the server is ready. To prevent this, add `--nobrowser`.
```bat
.\llamafile-0.10.5.exe --server --model "qwen3-4b-thinking-2507.Q4_K_M.gguf" --ctx-size 2048 --nobrowser
```

---

## 4. The "Ultimate" Batch Command

If you want a highly customized setup that binds to all network interfaces, runs on a custom port, allocates a large context, and doesn't auto-launch the browser, your `Start.bat` file would look like this:

```bat
@echo off
echo Starting Portable AI Server...
.\llamafile-0.10.5.exe --server --model "qwen3-4b-thinking-2507.Q4_K_M.gguf" --ctx-size 8192 --host 0.0.0.0 --port 8080 --nobrowser
pause
```
*(Adding `@echo off` and `pause` are standard Windows batch file commands that make the console output look cleaner and prevent the window from closing instantly if there is an error).*