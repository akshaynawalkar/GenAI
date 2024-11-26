---
tags:
- text-to-image
- lora
- diffusers
- template:diffusion-lora
- flux
- meme
widget:
- text: >-
    meme, A medium-sized painting of a white T-rex in the middle of a dark,
    stormy night. The t-rex is facing towards the left side of the frame, its
    head turned towards the right. Its mouth is open, revealing its sharp teeth.
    A rooster is standing in the foreground of the painting, with a red cap on
    its head. The roosters head is turned to the right, and the word "Remember
    who you are" is written in white text above it. The background is a deep
    blue, with dark gray clouds and a crescent moon in the upper left corner of
    the image. There are mountains in the background, and a few other animals
    can be seen in the lower right corner.
  output:
    url: images/M1.png
- text: >-
    meme, A cartoon drawing of a brown cat and a white sheep. The sheep is
    facing each other and the cat is facing towards the left side of the image.
    The brown cat has a black nose and a black mouth. The white sheep has a
    white body and black legs. The background is a light peach color. There is a
    text bubble above the brown cat that says "If you feel sad I can eat you".
  output:
    url: images/M3.png
- text: >-
    meme, A cartoon drawing of two zebras facing each other. The zebra on the
    left is facing the right. The horse on the right is facing to the left. The
    zebrab is facing towards the right and has a black mane on its head. The
    mane is black and white. The sky is light blue and there are birds flying in
    the sky. There is a text bubble above the zebras head that says "UPGRADE
    MAN!"
  output:
    url: images/M4.png
base_model: black-forest-labs/FLUX.1-dev
instance_prompt: meme
license: creativeml-openrail-m
---
# F-Meme.FLUX.1-Dev

<Gallery />

**The model is still in the training phase. This is not the final version and may contain artifacts and perform poorly in some cases.**

## Model description 

**prithivMLmods/F-Meme**

Image Processing Parameters 

| Parameter                 | Value  | Parameter                 | Value  |
|---------------------------|--------|---------------------------|--------|
| LR Scheduler              | constant | Noise Offset              | 0.03   |
| Optimizer                 | AdamW  | Multires Noise Discount   | 0.1    |
| Network Dim               | 64     | Multires Noise Iterations | 10     |
| Network Alpha             | 32     | Repeat & Steps           | 20 & 2200 |
| Epoch                     | 10   | Save Every N Epochs       | 1     |

    Labeling: florence2-en(natural language & English)
    
    Total Images Used for Training : 10

## Best Dimensions

- 768 x 1024 (Best)
- 1024 x 1024 (Default)
    
## Setting Up
```python
import torch
from pipelines import DiffusionPipeline

base_model = "black-forest-labs/FLUX.1-dev"
pipe = DiffusionPipeline.from_pretrained(base_model, torch_dtype=torch.bfloat16)

lora_repo = "prithivMLmods/F-Meme"
trigger_word = "meme"  
pipe.load_lora_weights(lora_repo)

device = torch.device("cuda")
pipe.to(device)
```
## Trigger words

You should use `meme` to trigger the image generation.

## Download model

Weights for this model are available in Safetensors format.

[Download](/prithivMLmods/F-Meme/tree/main) them in the Files & versions tab.