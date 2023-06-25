# text-to-image-generation
Generate Images from text prompt using Stable Diffusion Model

In the Stable Diffusion model or the  “Latent Diffusion Model” (LDM) the diffusion process happens in the latent space. This makes the denoising process faster. We used a pre-train variational autoencoder (vae: has an encoder and decoder) to compress the image data into lower-dimensional representations.

* encoder E: encode the full-sized image into lower dimensional latent data (compressed data).
* decoder D: decode the latent data back into an image

After this, forward and reverse diffusion processes are done in the latent space.
* Forward Diffusion Process: add Gaussian noise to the latent data.
* Reverse Diffusion Process: remove noise from the latent data.

To generate images from text prompts, stable diffusion models are fed conditioning inputs. This was done by  introducing a cross-attention mechanism to the denoising U-Net. The cross-attention mechanism allows the model to attend to different parts of the image and conditioning information, selectively incorporating relevant features. By incorporating the conditioning information during the generation process, the model was able to produce images that aligned with the provided conditions (text prompts). The conditioning input, text prompts were first converted into embeddings using a language model (CLIP), and then they were mapped into the U-Net via the multi-head attention layer.

References: [How and why stable diffusion works for text to image generation](https://www.paepper.com/blog/posts/how-and-why-stable-diffusion-works-for-text-to-image-generation/)
