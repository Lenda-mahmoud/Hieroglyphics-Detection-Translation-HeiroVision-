# 𓂀 Hieroglyphics Detection & End-to-End Translation Pipeline

An AI-powered pipeline designed to detect ancient Egyptian hieroglyphic symbols, classify them using Deep Learning, and translate the full text using LLMs. 

## 🚀 Project Overview
This project provides an end-to-end solution for historical text digitization:
1. **Symbol Detection:** Extracting individual glyph contours using computer vision (OpenCV).
2. **Symbol Classification:** Recognizing over 100+ categories of hieroglyphs using a specialized Deep Learning architecture.
3. **Gardiner Sign Lookup:** Retrieving standardized linguistic definitions from the Gardiner list database.
4. **Contextual Translation:** Leveraging LLMs (Google Gemini AI) to handle reading directions and translate column-by-column into coherent modern text.

---

## 🧠 My Contribution: Deep Learning & Pipeline Integration
As the **Machine Learning Engineer** on this graduation project, I engineered and optimized the core classification model and integrated the full text translation pipeline:

### 1. Few-Shot Similarity Learning (Siamese Network)
* **The Challenge:** Hieroglyphic datasets suffer from severe class imbalance and limited training samples per glyph, making traditional Softmax classifiers perform poorly.
* **The Solution:** I built a **Siamese Network** to shift the problem from direct classification to **Metric Learning (Similarity Verification)**. 
* **Backbone:** Integrated a pretrained **SqueezeNet 1.1** as a lightweight feature extractor to generate dense 512-dimensional embeddings.
* **Loss & Optimization:** Trained with Binary Cross-Entropy (BCE) and Contrastive Learning principles to compute absolute distances between symbol representations.
* **Performance:** Reached an outstanding **~94% Validation Accuracy** on a dataset of 100+ highly complex symbol classes.

### 2. Reference Embeddings Database
* Engineered a script to generate and cache offline reference embeddings for the entire organized dataset (3270 symbols) using **Cosine Distance**. This allows the network to perform real-time, zero-shot classification on newly detected glyphs without retraining the model.

### 3. Pipeline Integration & LLM Orchestration
* Connected the OpenCV bounding boxes directly to the embedding network for sequential symbol routing.
* Prompt-engineered the **Gemini 1.5 Flash** API to digest column-by-column Gardiner definitions, resolve ancient Egyptian structural ambiguities, and deliver cohesive translations.

---

## 📊 Results & Outputs

### Training Performance
Our Siamese Network converges efficiently within 20 epochs:
<p align="center">
  <img src="outputs/training_curves.png" width="600" alt="Training Curves">
</p>

### Pipeline Execution
Here is the system detecting, segmenting, and identifying individual signs from a raw input block:
<p align="center">
  <img src="outputs/detection_output.png" width="700" alt="Pipeline Output">
</p>

### Final Translation Example
> **Input Query:** Sequential column data matched to Gardiner codes.
> 
> **Gemini Contextual Output:** > _"The inscription invokes Geb, the Earth god, to 'stretch out your arms' to his 'sons,' hinting at renewal and rebirth. It calls for a swift transition beyond 'long old age' into the eternal realm, sustained by rituals, 'recitations,' 'tribute,' and the essential 'beer,' ensuring divine placement. Ultimately, the text articulates a hopeful journey towards an enduring, divinely-secured afterlife for the honored individual, guided and blessed by the pantheon.
Output is truncated. View as a scrollable element or open in a text editor. Adjust cell output settings..."_

---

## 🛠️ Tech Stack & Frameworks
* **Deep Learning:** PyTorch, Torchvision
* **Computer Vision:** OpenCV (Contour analysis, OTSU Thresholding)
* **LLM Integration:** Google GenAI SDK (Gemini-1.5-Flash)
* **Data Processing:** Scipy (Cosine Distance), NumPy, Pickle, PIL

## 💻 How to Run
1. **Clone the Repository:**
   ```bash
   git clone [https://github.com/Lenda-mahmoud/Hieroglyphics-Detection-Translation-HeiroVision.git](https://github.com/Lenda-mahmoud/Hieroglyphics-Detection-Translation-HeiroVision.git)
   cd Hieroglyphics-Detection-Translation-HeiroVision
