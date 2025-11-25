# 👕 OutfitDiffuser

Este projeto é uma implementação de **Virtual Try-On (Provador Virtual)** utilizando modelos de Difusão Latente. O sistema permite que um usuário "vista" digitalmente uma peça de roupa de referência, preservando sua pose corporal e as características do tecido.

## Como Funciona

O pipeline combina três técnicas avançadas de Visão Computacional para gerar resultados fotorrealistas:

1.  **Segmentação Semântica (`SegFormer`):** Identifica e mascara automaticamente as roupas atuais da pessoa, sem necessidade de edição manual.
2.  **Preservação de Pose (`ControlNet OpenPose`):** Cria um "esqueleto" digital para garantir que a anatomia e a posição dos braços/pernas sejam mantidas na geração.
3.  **Transferência de Estilo (`IP-Adapter`):** Injeta as características visuais (textura, estampa, cor) da roupa de referência diretamente no mecanismo de atenção da UNet.

## Stack

* **Core:** Python, PyTorch, Diffusers (Hugging Face).
* **Modelos:**
    * [Stable Diffusion 1.5 Inpainting](https://huggingface.co/runwayml/stable-diffusion-inpainting) (Base)
    * [IP-Adapter](https://huggingface.co/h94/IP-Adapter) (Image Prompting)
    * [ControlNet v1.1](https://huggingface.co/lllyasviel/ControlNet) (OpenPose)
    * [SegFormer B2 Clothes](https://huggingface.co/mattmdjaga/segformer_b2_clothes) (Segmentação)

## Instalação e Uso

### Pré-requisitos
* Python 3.10+
* GPU com suporte a CUDA (Recomendado: 8GB+ VRAM ou Google Colab T4)

### Instalação das Dependências
```bash
pip install diffusers transformers accelerate controlnet_aux ip_adapter torch torchvision opencv-python-headless pillow
