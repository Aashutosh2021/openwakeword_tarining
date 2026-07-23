# How to Train the "Hey Ultron" Wake Word Model

Because the official data generation tools for OpenWakeWord require Linux and are computationally heavy, the best and fastest way to train a robust model is to use their pre-configured Google Colab notebook. 

Here are the complete step-by-step instructions to train the model for "Hey Ultron" and download it to your PC.

### Step 1: Open the Colab Notebook
1. Click this link to open the official training notebook: [OpenWakeWord Colab Notebook](https://colab.research.google.com/github/dscripka/openWakeWord/blob/main/notebooks/automatic_model_training.ipynb)
2. Ensure you are signed into a Google account.
3. In the top menu, click **Runtime > Change runtime type**.
4. Set the **Hardware accelerator** to **T4 GPU** (or any available GPU) and click **Save**. This will speed up the training significantly.

### Step 2: Configure the Wake Word
1. Scroll down to the cell titled **Define the Target Wake Word/Phrase**.
2. Look for the `target_word` variable. Change it to:
   ```python
   target_word = "hey ultron"
   ```
3. Run the cell by clicking the Play button (▶) on the left side of the cell.

### Step 3: Run the Training Pipeline
1. In the top menu, click **Runtime > Run all**.
2. A warning might appear saying the notebook is authored by GitHub. Click **Run anyway**.
3. **Wait for it to finish.** This process will automatically:
   - Install the required dependencies.
   - Generate thousands of synthetic audio clips of "hey ultron" with varying pitches, speeds, and background noises.
   - Download massive datasets of false-positive "background" noise.
   - Train the neural network model.

> [!NOTE]
> The entire pipeline usually takes **45 to 60 minutes** to complete. Leave the browser tab open while it runs.

### Step 4: Download the Model
1. Once all cells have completed successfully, scroll to the very bottom of the notebook.
2. In the final cell, the notebook automatically exports the trained model as an ONNX file.
3. On the left sidebar of the Colab interface, click the **Folder icon** (📁) to open the file browser.
4. You should see a file named `hey_ultron.onnx` (or `hey ultron_v0.1.onnx`).
5. Click the three dots (⋮) next to the file and select **Download**.

### Step 5: Provide the Model
Once you have the downloaded `.onnx` file:
1. Move the `hey_ultron.onnx` file into your project folder: `E:\UltronAssistant\app\src\main\assets\`
2. Reply to me here saying "The model is downloaded", and I will update the Android app code (`WakeWordManager.kt`) to switch over to the new "Hey Ultron" model!
