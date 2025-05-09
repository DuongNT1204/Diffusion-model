
# Results: [Notion Link](https://www.notion.so/Nguyen-Tung-Duong-1ed2eb74111a80959769fd70f562353c?pvs=4)

## 🚀 Quick Start (Setup Runpod Server)

To quickly launch **Kohya GUI** on **Runpod**:

1. **Select GPU**: Choose a suitable GPU such as **4090**, **3090**, or another supported model. You can use the pre-configured [Runpod template](https://www.runpod.io/console/explore/3c0tdgrly3) which is set up with **Torch 2.2.0** for **Kohya** and **ComfyUI** for inference after training.
2. Click **Deploy** to start the pod.
3. Once the pod is deployed, use the **Jupyter Lab** server to configure **Kohya** for training.

---

## 🛠 Set up Kohya and GUI

To manually set up **Kohya GUI** on **Runpod**, follow these steps:

1. Open the terminal in **Jupyter Lab** and run the following commands to set up the environment and the **Kohya GUI**:

   ```bash
   cd /workspace
   git clone --recursive https://github.com/bmaltais/kohya_ss.git
   wget -O Realistic_sdxl.safetensors "https://huggingface.co/SG161222/RealVisXL_V5.0/resolve/main/RealVisXL_V5.0_fp16.safetensors?download=true"
   cd kohya_ss
   ./setup-runpod.sh
   ./gui.sh --share --headless
   ```

2. After running these commands, you will be able to access the **Kohya GUI** via the shared link or through the exposed port.

---

## 📌 Training Diffusion Model using Kohya GUI

Follow these steps to train your diffusion model using **Kohya GUI**:

### 1. **Caption Your Images**
- Navigate to the **Utilities** tab in the GUI.
- Use the **BLIP tool** to automatically label your training images.
- If you're training with **Itay/Irit** images, use a specific prefix such as `a photo of Itay/Irit,` to help the model recognize key features and improve the training process.

### 2. **Prepare Dataset (LoRA Tab)**
- Switch to the **LoRA** tab within the GUI.
- Load and organize your training dataset by uploading your images. Ensure that the data is properly formatted for the LoRA model.
- For this setup, I used the base model: [RealVisXL V5.0](https://huggingface.co/SG161222/RealVisXL_V5.0). You can download it to **Runpod** by running the following command:

   ```bash
   wget -O Realistic_sdxl.safetensors "https://huggingface.co/SG161222/RealVisXL_V5.0/resolve/main/RealVisXL_V5.0_fp16.safetensors?download=true"
   ```

### 3. **Set Training Parameters**
- In the **LoRA** tab, you will be able to modify your model's hyperparameters according to your needs.
- My specific hyperparameters can be found in the file: `config_kohya.json`.
- Recommend using rank LoRA values of 64 or 128 for optimal results. Adjusting the rank according to your dataset size and requirements will help with performance and training quality.

### 4. **Start Training**
- Once everything is set up, click **Start Training** to begin the training process.
- You can monitor the training progress in real time through the **GUI** interface.

---

## 🖥️ Using ComfyUI to Infer with Your Model:

After training your model, you can use **ComfyUI** for inference:

1. In the terminal, run the following command to start **ComfyUI**:
   
   ```bash
   bash run_gpu.bat
   ```

2. Use the **LoRA workflow** within **ComfyUI** for inference tasks.
3. For **face detailer** inference, I’ve created a custom workflow that you can use. The workflow is located in the file: `'Using_lora_with_face_detailer.json'`.

---

## 🔄 Diffuser Training

For **diffuser model training**:

1. Modify the path to the data in the provided notebook.
2. Proceed with training directly on your model using the configured paths.

---

With these steps, you should be able to easily set up and train your models using **Kohya GUI** on **Runpod** and run inference with **ComfyUI**. Happy training and experimenting! 🚀
