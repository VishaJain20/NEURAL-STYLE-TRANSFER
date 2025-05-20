# NEURAL-STYLE-TRANSFER
**Company**: CODTECH IT SOLUTIONS  
**Intern**: Visha Jain  
**Intern ID**: C0DF230  
**Domain**: AI/ML  
**Duration**: 4 weeks  
**Mentor**: Neela Santosh  
# 🎨 Neural Style Transfer with PyTorch & Gradio

This project implements a Neural Style Transfer (NST) application that allows users to apply the artistic style of one image onto another using a deep learning model (VGG19). The app is built using **PyTorch** for backend processing and **Gradio** for a beautiful and user-friendly web interface.

---

## 📌 What is Neural Style Transfer?

Neural Style Transfer is a computer vision technique that blends two images:  
- A **content image** (here I have provided content1.jpg)  
- A **style image** (here I have provided style2.jpg which is an ghibli style image)

The goal is to produce a new image that maintains the content of the first image but adopts the visual style of the second.

---

## 🚀 Features

- ✅ Upload your own content and style images  
- ✅ Real-time progress updates using Gradio  
- ✅ Pretrained VGG19 feature extractor  
- ✅ Downloadable stylized result image  
- ✅ Beautiful UI with custom CSS and themed layout  
- ✅ Includes sample images (e.g., *Starry Night*, a cat photo) for quick demos  
- ✅ GPU acceleration support (if available)

---

## 🧠 How It Works

1. **Image Preprocessing**: Both images are resized, converted to tensors, and normalized.
2. **Feature Extraction**: A pretrained VGG19 model is used to extract content and style features from specific layers.
3. **Style Representation**: Style features are converted to **Gram matrices** to represent correlations between channels.
4. **Optimization Loop**:  
   - A target image is initialized as a copy of the content image.  
   - The loss is calculated based on differences in content and style features.  
   - The image is iteratively updated using backpropagation and an optimizer (Adam).
5. **Output Generation**: The final tensor is converted back to an image and displayed with an option to download.

---

## 🖼️ UI Overview

The Gradio interface includes:
- 📤 Upload buttons for **Content Image** and **Style Image**
- 🖌️ Display for the final **Styled Output**
- 💬 **Status box** for progress and errors
- 📥 **Download** button for saving results
- 🧪 **Sample Image Loader** to test the app instantly
- 🔄 **Clear** button to reset inputs/outputs

All elements are wrapped in a clean, card-based layout with subtle shadows and modern aesthetics using **custom CSS**.

---

## 🧱 Architecture & Design

### 🧩 Backend Components
- **PyTorch**:
  - `torchvision.models.vgg19` is used to extract features.
  - `torch.optim.Adam` is used to iteratively update the target image.
- **Image utilities**:
  - `PIL` and `torchvision.transforms` are used for image preprocessing and reconstruction.
- **Device support**:
  - Automatically detects and uses GPU (`cuda`) if available.
- **Logging**:
  - Built-in `logging` module used for debugging and error handling.

### 🖥️ Frontend Components
- **Gradio Blocks Interface** with:
  - `gr.Image`, `gr.Textbox`, `gr.Button`, `gr.File`
  - `custom_css` for polished look and feel
- **Progress Feedback**:
  - `gr.Progress()` is used to show real-time progress for each phase (loading, extracting features, optimizing, saving).
- **Theming**:
  - `gr.themes.Monochrome()` gives a clean, distraction-free style.

---

## 🧪 Sample Use Case

1. Open the app using `interface.launch()`.
2. Upload your own **content** image (e.g., your photo).
3. Upload a **style** image (e.g., Van Gogh’s painting).
4. Click **"Apply Style Transfer"**.
5. Wait for the progress to complete (around 200 steps).
6. View and download the stylized output.



---

## ⚙️ Parameters Used

- `steps = 200`: Number of optimization steps  
- `style_weight = 1e6`: Strength of style in the final image  
- `content_weight = 1`: Strength of content retention  
- `lr = 0.003`: Learning rate for Adam optimizer  
- `max_image_size = 200`: To ensure memory efficiency  
- Image size limit: ≤ 500x500 (automatically resized if needed)

---

## 🛠️ Error Handling

- Checks for:
  - Missing file paths
  - Oversized images
  - Failed image loads
  - Model loading errors
- All errors are displayed in the Gradio `Status` box and logged using `logging`

---

## 📷 Sample Results
- I have provided sample input and output UI screenshot that depicts how the project works

---

## 🔒 Requirements

- Python 3.7+
- Gradio
- PyTorch
- torchvision
- PIL (Pillow)
