# Offline-ai

# 🚀 Portable Offline AI from a USB Pendrive

**Created by: Anunay Srivastava**  
*Reference Document: "Run Offline AI from a USB Pendrive"*

Welcome to the Portable Offline AI repository! This project provides everything you need to set up, carry, and run a powerful Artificial Intelligence assistant directly from a USB flash drive.

---

## ❓ What is this?

This project is a lightweight, zero-installation setup that allows you to run Large Language Models (LLMs)—specifically the Qwen architecture—entirely locally using a USB pendrive. 

It works by combining **Llamafile** (a highly optimized, standalone execution engine by Mozilla AI) with **GGUF** (a file format for compressed, highly efficient AI models). Instead of dealing with complex Python environments, Docker containers, or GPU drivers, this method bundles the AI engine and the "brain" (model) into a simple folder you can carry in your pocket.

## 🎯 What is the use of it?

* **🔒 100% Privacy & Security:** Your prompts, questions, and sensitive data never leave your computer. Nothing is sent to the cloud, making it perfect for processing private documents or code.
* **📶 Completely Offline:** Once downloaded, the AI requires zero internet connection. Use it on an airplane, in remote areas, or on air-gapped secure computers.
* **⚡ Zero Installation (Plug & Play):** You do not need to install software on the host PC. You simply plug in the USB drive, double-click a file, and chat via your web browser.
* **🎒 Ultimate Portability:** Carry your personalized AI assistant, complete with your preferred models and context settings, on your keychain to use on any compatible Windows PC.

---

## 🔗 Important Links and Resources

Before starting the setup, you will need to download resources from the following links:

* **Fine-tuned Thinking Model:** [pramodlohra/Qween3_4B_thinking_finetune](https://huggingface.co/pramodlohra/Qween3_4B_thinking_finetune)
* **Llamafile Engine Release:** [Mozilla AI llamafile v0.10.6](https://github.com/mozilla-ai/llamafile/releases/tag/0.10.6)
* **Qwen GGUF Models:** [Qwen3-8B-GGUF Repository](https://huggingface.co/Qwen/Qwen3-8B-GGUF/tree/main)

---

## 🛠️ Installation & Setup Guide

### Step 1 — Prepare the USB Pendrive
1. Connect your USB pendrive to your PC.
2. Format the pendrive.
3. Select **exFAT** as the file system.
4. Make sure the pendrive has enough free space for the AI model. *(The required storage depends on the model you choose).*

### Step 2 — Download Llamafile
1. Search for Llamafile GitHub (or use the link provided above).
2. Open the official repository/release page.
3. Download the required Windows `.exe` file.
   * *For example:* `llamafile-0.10.5.exe` (or the newer `0.10.6` version).

### Step 3 — Download an AI Model
1. Download a compatible GGUF model from the links above.
   * *For example:* `qwen3-4b-thinking-2507.Q4_K_M.gguf`
2. Keep the `.gguf` file in the same folder as the llamafile executable.

**Your folder should look like:**
```text
Pendrive
│
├── llamafile-0.10.5.exe
└── qwen3-4b-thinking-2507.Q4_K_M.gguf
