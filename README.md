# MIMV
**Masked Image Modeling for Video**

## Feedback & Considerations

Videos are typically compressed, so there may be some overhead when trying to decompress, break into frames, and apply the model.

- Perhaps we re-compress after application?
- We can also check the SOTA video models to see how they handle this issue.
- Otherwise, we can just bring it up as a pitfall.
  - Could be interesting to quantify the impact of compression on computational complexity.
- Don’t focus on PSNR and SSIM because they will likely be really bad.
  - Still worth applying SSIM just to observe the behavior.

---

## Pipeline

### Step 1: Dataset Preparation
- Select a suitable video dataset with clear visual semantics  
  *(e.g., Kinetics-400, UCF101)*
- Preprocess videos into individual frames  
  *(Each video becomes a sequence of frames)*

### Step 2: Frame-by-Frame Masking Strategy
- For each video clip:
  - Apply random masking independently to each frame using SimMIM's simple masking strategy.

### Step 3: Training Objectives
- Combine two loss functions:
  - **Reconstruction Loss**: L1 loss
  - **Adversarial Loss**: GAN loss
- Total Loss:  
  \[
  \mathcal{L}_{total} = \mathcal{L}_{rec} + \lambda \mathcal{L}_{adv}
  \]  
  *(Where λ balances the adversarial loss relative to the reconstruction loss)*

### Step 4: Evaluation and Validation

#### 1. Video Classification
- Fine-tune learned representations on standard benchmarks  
  *(e.g., Kinetics-400, UCF101)*

#### 2. Video Reconstruction Quality
- Measure quantitative metrics such as:
  - **PSNR**
  - **SSIM** *(just to see, even if results are poor)*
