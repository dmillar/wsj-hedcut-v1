---
license: creativeml-openrail-m
tags:
  - stable-diffusion
  - stable-diffusion-diffusers
  - text-to-image
inference: true
---
### Wall Street Journal Hedcut Style for Stable Diffusion
Readers of the Wall Street Journal (WSJ) are familiar with the distinctive style used to create portaits of their writers and subjects. This is a fine-tuned stable
diffusion model that can be used to create hedcut-styled images using the prompt **_wsj hedcut of \<subject\>_**. This model can also be used in a DreamBooth environment
to train a face or other subject for custom and unique hedcuts.

```python
#!pip install diffusers transformers scipy torch
from diffusers import StableDiffusionPipeline
import torch
model_id = "dmillar/wsj-hedcut-v1"
pipe = StableDiffusionPipeline.from_pretrained(model_id, torch_dtype=torch.float16)
pipe = pipe.to("cuda")
prompt = "wsj hedcut of a woman"
image = pipe(prompt).images[0]
image.save("./woman_hedcut.png")
```
