# 🎨 NeuralBrush

**NeuralBrush** blends the artistic style of one image onto the content of another using **AdaIN (Adaptive Instance Normalization)** — a real-time neural style transfer technique. Upload a content photo and a style reference, adjust the style strength, and get a stylized result.

---

## ✨ Features

- Upload any content image + any style reference image
- Adjustable **style strength (alpha)** slider for controlling how strongly the style is applied
- Clean, responsive web UI built with Flask + Bootstrap
- Powered by a custom-trained AdaIN encoder-decoder model in PyTorch

---

## 🧠 How It Works

NeuralBrush uses the AdaIN approach introduced by Huang & Belongie (2017):

1. A pretrained **VGG encoder** extracts feature maps from both the content and style images.
2. **Adaptive Instance Normalization** aligns the mean and variance of the content features to match the style features.
3. A trained **decoder** reconstructs the stylized image from these blended features.
4. The `alpha` parameter blends between the original content (`alpha = 0`) and the fully stylized output (`alpha = 1`).

---

## 🛠 Tech Stack

- **Python 3.11**
- **PyTorch** / **Torchvision** — model + inference
- **Flask** + **Flask-WTF** + **Flask-Bootstrap** — web app & form handling
- **Pillow** — image I/O
- **Bootstrap 5** — front-end styling

---

## 📂 Project Structure

```
NeuralBrush/
├── app.py                  # Flask app entry point
├── train.py                 # Training script
├── utils/
│   ├── models.py            # VGGEncoder, Decoder
│   └── utils.py             # AdaIN + helper functions
├── static/
│   └── uploads/             # User-uploaded & generated images
├── templates/
│   └── index.html           # Main web UI
├── examples/                 # Example images shown on the homepage
├── demo_images/              # Sample input/output images
├── vgg_normalised.pth        # Pretrained VGG encoder weights
├── requirements.txt
└── README.md
```

---

## 🚀 Getting Started

### 1. Clone the repo
```bash
git clone https://github.com/AyanJaved/NeuralBrush.git
cd NeuralBrush
```

### 2. Create a virtual environment
```bash
python -m venv venv
venv\Scripts\activate      # Windows
source venv/bin/activate   # Mac/Linux
```

### 3. Install dependencies
```bash
pip install -r requirements.txt
```

### 4. Run the app
```bash
python app.py
```

Then open your browser to:
```
http://localhost:5000
```

---

## 🖼 Usage

1. Upload a **content image** (the photo you want to stylize).
2. Upload a **style image** (the artwork/style reference).
3. Adjust the **style strength** slider (0 = original photo, 1 = fully stylized).
4. Click **Transfer Style** and download your result.

---

## 📊 Dataset

The model was trained using:
- **Content images:** COCO dataset
- **Style images:** WikiArt dataset

---

## 🗺 Roadmap

- [ ] Add support for video style transfer
- [ ] Deploy a hosted demo
- [ ] Add more built-in style presets
- [ ] Batch processing for multiple images

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome! Feel free to check the [issues page](https://github.com/AyanJaved/NeuralBrush/issues).

---


## 🙏 Acknowledgements

- [Huang & Belongie, *Arbitrary Style Transfer in Real-time with Adaptive Instance Normalization*](https://arxiv.org/abs/1703.06868)
- VGG19 architecture (Simonyan & Zisserman)