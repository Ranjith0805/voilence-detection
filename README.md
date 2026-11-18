# 🛡️ SafeWatch – AI Violence Detection for CCTV

SafeWatch watches CCTV footage, detects violence (fights, punching, pushing) and raises an alarm automatically.
It uses **deep learning on both video and audio**.

**Deep Learning Project – B.Tech CSE, Amity University Rajasthan**
By: Erkichedu Ranjith Kumar

---

## 🚀 Demo
- Live demo (Gradio): https://792c92cad80217e4e4.gradio.live  *(works while the Colab session is running)*
- Notebook: `SafeWatch_Violence_Detection.ipynb` (open in Google Colab and Run all)

## 🧠 How it works
```
Video  → 16 frames (4 sec) → MobileNetV2 CNN (1,280 features/frame) → Bi-LSTM → Violence score
Audio  → YAMNet (521 sound classes) → Danger sounds (scream, shout, glass break, gunshot)
Both   → Alarm logic → 🚨 ALARM
```

| Part | Model | Job |
|---|---|---|
| Eyes | MobileNetV2 (pretrained CNN) | Understands what is in each frame |
| Memory | 2-layer Bi-LSTM (1.6M params) | Understands motion across frames |
| Ears | YAMNet | Detects danger sounds |

## 🚨 Alarm rule
| Level | Condition |
|---|---|
| 🟢 All clear | Violence score below 50% |
| 🟡 Suspicious | Score above 50% |
| 🔴 Alarm | Score above 80% for 3 windows in a row, **or** above 60% with danger audio for 2 windows |

## 📊 Dataset
**Real Life Violence Situations (RLVS)** – 2,000 videos (1,000 violence, 1,000 normal), Kaggle.
Split: 70% train, 15% validation, 15% test.

## ✅ Results
| Model | Test Accuracy |
|---|---|
| CNN + Bi-LSTM (ours) | **95.9%** |
| CNN only (baseline) | 96.9% |

## 🛠️ Tech used
Python · TensorFlow/Keras · OpenCV · TensorFlow Hub · Gradio · Google Colab

## ▶️ How to run
1. Open the notebook in Google Colab
2. Runtime → Change runtime type → T4 GPU
3. Runtime → Run all
4. Open the Gradio link printed at the end and upload a video

## 🔮 Future scope
- Connect directly to live CCTV (RTSP) cameras
- Send SMS / app alerts to security staff
- Detect weapons and identify the people involved
