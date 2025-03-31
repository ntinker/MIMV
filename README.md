# MIMV
Masked image modeling for video. 

Feedback:

Videos are typically compressed, so there may be some overhead when trying to decompress, break into frames, and apply the model
- Perhaps we re-compress after application?
- We can also check the SOTA video models to see how they handle this issue
- Otherwise, we can just bring it up as a pitfall
    + Could be interesting to somehow quantify the impact of the compression on computational complexity 
- Don’t focus on PSNR and SSIM because they will likely be really bad 
    + I still think we could apply SSIM just to see 
