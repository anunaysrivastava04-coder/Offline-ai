# System Requirements

To ensure a smooth and responsive experience when running your offline AI from a USB pendrive, the host computer and the pendrive itself should meet the following specifications.

---

## 💻 Hardware Requirements (Host PC)

Since the AI model is loaded from the USB drive into the host computer's active memory (RAM), the performance depends heavily on the computer you plug the drive into.

### Minimum Requirements
* **Operating System:** Windows 10 (64-bit) or later *(This guide uses a Windows `.exe` and `.bat` file)*.
* **Processor (CPU):** Any modern 64-bit Intel or AMD processor (AVX2 support highly recommended).
* **Memory (RAM):** 8 GB RAM. *(Sufficient for 4B parameter models with a smaller context size like 2048).*
* **Graphics (GPU):** None required. The model will run entirely on the CPU if no compatible GPU is found.

### Recommended Requirements (For Faster Speeds & Larger Contexts)
* **Operating System:** Windows 10 / 11 (64-bit).
* **Processor (CPU):** Recent multi-core CPU (Intel Core i5/i7/i9 10th Gen+ or AMD Ryzen 5/7/9 3000 series+).
* **Memory (RAM):** 16 GB to 32 GB RAM. *(Recommended for 8B models and context sizes of 8192 or higher).*
* **Graphics (GPU):** NVIDIA GPU with CUDA support (e.g., RTX 2060, 3060, or better) or a compatible AMD GPU. Llamafile will automatically attempt to offload computations to the GPU for significantly faster text generation.

---

## 💾 USB Pendrive Requirements

Because the computer has to read a multi-gigabyte file into memory every time you start the AI, the speed of your USB drive is a major factor in how fast the server starts.

### Minimum
* **Capacity:** 8 GB free space.
* **Speed:** USB 2.0 *(Warning: Model loading times will be very slow, potentially taking several minutes).*
* **Format:** exFAT *(Required to store files larger than 4GB, which is common for GGUF models).*

### Recommended
* **Capacity:** 16 GB to 32+ GB (Allows you to store multiple models and larger parameter sizes).
* **Speed:** USB 3.0, USB 3.1, or USB-C Flash Drive. *(Loading the model into memory will take seconds rather than minutes).*
* **Format:** exFAT.

---

## 🧠 RAM & Context Size Matrix

When editing your `Start.bat` file, keep your host PC's total RAM in mind. The model size plus the `--ctx-size` dictates how much RAM will be consumed.

| Model Size | `--ctx-size` | Estimated Total RAM Usage | Recommended PC RAM |
| :--- | :--- | :--- | :--- |
| **4B Model** (e.g., Qwen 4B) | 2048 | ~3.5 GB | 8 GB |
| **4B Model** | 8192 | ~5.0 GB | 8 GB - 16 GB |
| **8B Model** (e.g., Qwen 8B) | 2048 | ~6.5 GB | 16 GB |
| **8B Model** | 8192 | ~8.0 GB+ | 16 GB - 32 GB |

*Note: If Llamafile crashes or immediately closes upon launching the `Start.bat` file, it is usually because the host computer does not have enough free RAM to support the requested model and context size.*