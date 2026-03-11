<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&ColorList=0D4F8B,0A8A6A,1A6B3A&height=250&section=header&text=Satellite%20Forensics%20AI&fontSize=58&fontColor=DEE2D9&animation=fadeIn&fontAlignY=35&desc=13-Band%20Multispectral%20%7C%20Hybrid%20CNN-ViT%20%7C%20Explainable%20AI%20%7C%20Research%20Publication&descAlignY=60&descAlign=50" width="100%"/>
</div>
<div align="center">
  <img src="https://readme-typing-svg.herokuapp.com?font=Fira+Code&weight=600&size=20&pause=1000&color=00D4FF&center=true&vCenter=true&width=900&lines=13-Band+EuroSAT+Multispectral+Classification;Hybrid+CNN-ViT+Feature+Fusion+%7C+96.98%25+Accuracy;Grad-CAM+Explainability+%2B+MC+Dropout+Uncertainty;Google+Scholar+Publication+Ready." alt="Typing SVG"/>
</div>
<br/>
<div align="center">
Show Image
Show Image
Show Image
Show Image
Show Image
</div>

Overview
Standard satellite classification discards 10 of 13 available Sentinel-2 bands — treating a multispectral instrument like an ordinary camera. This project rejects that approach entirely.
We built an end-to-end pipeline that ingests raw 13-band .tif files using rasterio, extracts spectral signatures invisible to the human eye — Near-Infrared (NIR), Short-Wave Infrared (SWIR) — and classifies 10 land-use categories across 27,597 images. The scientific contribution is a rigorous ablation study that mathematically justifies each architectural choice, culminating in a Hybrid CNN-ViT model that outperforms every individual baseline.

Ablation Study — Results
Every model in this pipeline serves a purpose beyond accuracy. Each one proves the next one's necessity.
ModelAccuracyF1 ScoreParametersΔ BaselineScientific PurposeANN81.88%0.817027,430,794—Proves spatial destruction costs 14%CNN96.26%0.9623818,410+14.38%Local texture — 33× fewer paramsHAM96.52%0.9651824,298+14.64%SE blocks weight critical spectral bandsViT92.54%0.92542,868,170+10.66%Global context — needs fusion to shineHybrid CNN+ViT96.98%0.96983,458,858+15.10%Local + Global = SOTA

Highway F1 went from 0.501 → 0.943 (+44%) — the clearest proof that spatial structure is non-negotiable.


Architecture
Input (B, 13, 64, 64)
       │
       ├─────────────────────┬─────────────────────┐
       │                     │                     │
  CNN Branch            ViT Branch                 │
  (Local Specialist)    (Global Specialist)        │
       │                     │                     │
  3× Conv Blocks        8×8 Patch Embed            │
  BatchNorm + ReLU      64 Patch Tokens            │
  MaxPool + Dropout     4 Transformer Blocks       │
  AdaptiveAvgPool       CLS Token Output           │
       │                     │                     │
   (B, 2048)             (B, 192)                  │
       │                     │                     │
       └──────── CONCAT ──────┘                    │
                  │                                │
              (B, 2240)                            │
                  │                                │
         Fusion Classifier                         │
         Linear(512) → Linear(128) → Linear(10)   │
                  │                                │
           Predictions ◄───────────────────────────┘

Explainability & Uncertainty
This project goes beyond accuracy metrics — two layers of scientific validation are built in.
Grad-CAM generates class activation heatmaps that visually confirm the model attends to correct spectral regions — forest canopy, river channels, road geometry — not background noise.
Monte Carlo Dropout runs 50 stochastic forward passes per sample to compute epistemic uncertainty. Pasture and PermanentCrop consistently show the highest uncertainty, confirming their genuine spectral overlap is a scientific challenge, not a model failure.

Stack
<div align="center">
Show Image
Show Image
Show Image
Show Image
Show Image
Show Image
</div>

Repository Structure
satellite-multispec-hybrid-classifier/
│
├── notebook.ipynb                 ← Complete pipeline (Steps 0–16)
│
├── results/
│   ├── ablation_results.xlsx      ← Publication-ready results table
│   ├── CM_0_ALL_COMBINED.png      ← All 5 confusion matrices
│   ├── CM_1_ANN.png  →  CM_5_Hybrid.png
│   ├── GradCAM_FULLHD.png         ← Explainability — all 10 classes
│   └── MC_Dropout_FULLHD.png      ← Uncertainty analysis
│
└── README.md

Research Team
<table width="100%">
  <tr>
    <td align="center" width="33%">
      <a href="https://github.com/Abu-Sameer-66">
        <img src="https://github.com/Abu-Sameer-66.png" width="80px" style="border-radius:50%"/><br/>
        <b>Abu Sameer</b>
      </a><br/>
      <sub>Project Lead & Core Architect</sub><br/><br/>
      <sub>Hybrid CNN-ViT architecture design · Grad-CAM XAI · MC Dropout uncertainty · Research paper authorship</sub>
    </td>
    <td align="center" width="33%">
      <a href="https://github.com/hamdan0006">
        <img src="https://github.com/hamdan0006.png" width="80px" style="border-radius:50%"/><br/>
        <b>Hamdan Ahmed</b>
      </a><br/>
      <sub>Data Engineering Lead</sub><br/><br/>
      <sub>rasterio 13-band pipeline · Per-band normalization · Stratified splitting · ANN & CNN training</sub>
    </td>
    <td align="center" width="33%">
      <a href="https://github.com/Aabdullahgil">
        <img src="https://github.com/Aabdullahgil.png" width="80px" style="border-radius:50%"/><br/>
        <b>Abdullah Kamal</b>
      </a><br/>
      <sub>Model Evaluation Lead</sub><br/><br/>
      <sub>HAM & ViT training · Evaluation engine · Confusion matrices · Excel results automation</sub>
    </td>
  </tr>
</table>

Publication

Paper under preparation for journal submission.

Title: Hybrid CNN-Transformer Architecture for Multi-Spectral Satellite Image Classification with Explainability and Uncertainty Quantification on EuroSAT 13-Band Data
Target: MDPI Remote Sensing (Open Access · Google Scholar Indexed) · IEEE GRSL
bibtex@article{sameer2025satellite,
  title   = {Hybrid CNN-Transformer Architecture for Multi-Spectral 
             Satellite Image Classification with Explainability},
  author  = {Sameer, Abu and Ahmed, Hamdan and Kamal, Abdullah},
  journal = {MDPI Remote Sensing},
  year    = {2025},
  note    = {Under Review}
}

<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=gradient&ColorList=0D4F8B,0A8A6A,1A6B3A&height=100&section=footer" width="100%"/>
</div>
