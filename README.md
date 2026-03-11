<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&ColorList=0D4F8B,0A8A6A,1A6B3A&height=200&section=header&text=Satellite%20Forensics%20AI&fontSize=55&fontColor=DEE2D9&animation=fadeIn&fontAlignY=40&desc=13-Band%20EuroSAT%20%7C%20Hybrid%20CNN-ViT%20%7C%20Explainable%20AI%20%7C%20Research%20Publication&descAlignY=65&descAlign=50" width="100%"/>
</div>

<div align="center">

![PyTorch](https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Kaggle](https://img.shields.io/badge/Kaggle-GPU-20BEFF?style=for-the-badge&logo=kaggle&logoColor=white)
![Status](https://img.shields.io/badge/Status-Publication_Ready-FFD700?style=for-the-badge)

</div>

---

## What This Is

Most satellite classification systems use 3-band RGB — discarding 10 additional spectral bands that carry geological and chemical signatures invisible to the human eye. This project uses all 13 Sentinel-2 bands from EuroSAT (27,597 images, 10 land-use classes) and runs a rigorous ablation study proving that neither local nor global reasoning alone is sufficient — only their fusion is.

---

## Results

| Model | Accuracy | F1 | Δ Baseline |
|:------|:--------:|:--:|:----------:|
| ANN | 81.88% | 0.817 | — |
| CNN | 96.26% | 0.962 | +14.38% |
| HAM | 96.52% | 0.965 | +14.64% |
| ViT | 92.54% | 0.925 | +10.66% |
| **Hybrid CNN+ViT** | **96.98%** | **0.9698** | **+15.10%** |

Validated with **Grad-CAM** heatmaps and **Monte Carlo Dropout** uncertainty quantification.

---

## Research Team

| | Name | Role |
|:-|:-----|:-----|
| 🎯 | [Abu Sameer](https://github.com/Abu-Sameer-66) | Project Lead — Architecture, XAI, Paper |
| 🛠️ | [Hamdan Ahmed](https://github.com/hamdan0006) | Data Engineering — Pipeline, Preprocessing |
| 📊 | [Abdullah Kamal](https://github.com/Aabdullahgil) | Evaluation — Models, Results, Reporting |

---

## Publication

Target: **MDPI Remote Sensing** · **IEEE GRSL** · Google Scholar Indexed

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&ColorList=0D4F8B,0A8A6A,1A6B3A&height=100&section=footer" width="100%"/>
</div>
