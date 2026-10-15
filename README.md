# Uncensored AI Video Generator in ComfyUI

A plain-English guide to running unrestricted ("spicy") AI video models inside ComfyUI, on a laptop with no graphics card.

ComfyUI is a free app where you build AI workflows by connecting boxes (called nodes) with wires. Normally video models need a powerful graphics card. The Muapi nodes work differently: ComfyUI stays on your computer, the node sends your request to a server, the server runs the model, and the finished video comes back into your ComfyUI output folder. That is why almost any computer can do it, including one with no GPU.

> **Video walkthrough:** TODO: add the YouTube link here once the video is published.

## Start here: the node pack

**All the nodes and example workflows live in one repo: [SamurAIGPT/muapi-comfyui](https://github.com/SamurAIGPT/muapi-comfyui).** This repo is the guide, that repo is the code.

1. Open your ComfyUI folder and clone the node pack into `custom_nodes`:
   ```bash
   cd ComfyUI/custom_nodes
   git clone https://github.com/SamurAIGPT/muapi-comfyui
   pip install -r muapi-comfyui/requirements.txt
   ```
2. Restart ComfyUI.
3. Get an API key from [muapi.ai](https://muapi.ai) and paste it into the **MuAPI API Key** node (or the `api_key` field on any generation node).
4. Load an example: **File → Load**, then pick one of the files from the `workflows/` folder of the node pack (for example `MuAPI_TextToVideo_Seedance.json` or `MuAPI_ImageToVideo_Seedance.json`).
5. On the generation node, open the **`model`** dropdown and pick a spicy model from the list below. If a model is not in the dropdown yet, choose `custom` in the dropdown and type its endpoint name in the **`custom_endpoint`** field.

Use **MuAPI Text-to-Video** for models that start from words, and **MuAPI Image-to-Video** for models that start from a picture.

## The spicy video models

These are the same underlying models with much lighter content filtering than the big mainstream tools. The platform's basic rules still apply (see [Limits](#honest-limits)).

| Model | Starts from | Endpoint name to pick | Resolutions |
|---|---|---|---|
| Seedance 2.5 Spicy | Text, picture | `seedance-2.5-spicy-text-to-video` / `seedance-2.5-spicy-image-to-video` | 480p, 720p, 1080p, 4K (the 480p/1080p/4K endpoints are separate dropdown entries) |
| Wan 3.0 Spicy | Text, picture | `wan3.0-spicy-text-to-video` / `wan3.0-spicy-image-to-video` | 480p, 720p, 1080p, sound toggle |
| Seedance 2 Spicy (also a fast version) | Text, picture | `seedance-2-spicy-text-to-video` (+ `-fast`) / `seedance-2-spicy-image-to-video` (+ `-fast`) | 720p, 1080p, 4K |
| Seedance 2 Mini Spicy | Text, picture | `seedance-2-mini-spicy-text-to-video` / `seedance-2-mini-spicy-image-to-video` | 480p, 720p |
| MiniMax H3 Spicy | Picture | `minimax-h3-image-to-video-spicy` | 480p, 768p, 3 to 15 seconds |
| Wan 2.7 Spicy | Picture | `wan2.7-image-to-video-spicy` | 720p, 1080p |
| Wan 2.6 Spicy | Picture | `wan2.6-image-to-video-spicy` | 720p, 1080p |
| Wan 2.2 Spicy | Picture | `wan2.2-spicy-image-to-video` | 480p, 720p, 5 or 8 seconds |

Resolutions are from Muapi's endpoint definitions as of October 2026. See [MODELS.md](MODELS.md) for a short "which one should I pick" guide, and the live Muapi pages for current pricing.

## A note on settings

The generic **MuAPI Text-to-Video** and **Image-to-Video** nodes always send `aspect_ratio`, `quality` and `duration`. The spicy models do not have a `quality` setting, and the server ignores fields a model does not use, so you can leave `quality` alone. Model-specific settings go in the node's **`extra_params_json`** field as JSON, for example:

```json
{"resolution": "1080p", "enable_audio": true}
```

Pick values from the table above: for example Wan 3.0 Spicy accepts `480p`, `720p` or `1080p`, and does not accept the `21:9` aspect ratio that appears in the node's dropdown.

## Honest limits

- **It is pay as you go.** The node pack and these guides are free to download and use. Each video you generate is billed by Muapi, so there are no free generations.
- **No graphics card needed, but ComfyUI still runs locally.** Your computer runs ComfyUI; the video model runs on a server. You need an internet connection and a Muapi API key.
- **Baseline platform rules still apply.** These models filter much less than mainstream tools, but they are not rule-free. Use them responsibly and follow the law and the platform terms.
- **Not every spicy model has a dedicated dropdown entry for every resolution.** If you do not see one, use `custom` and type the endpoint name.

## Related Projects

- [muapi-comfyui](https://github.com/SamurAIGPT/muapi-comfyui): the node pack and example workflows used in this guide.
- [wan-3.0-comfyui](https://github.com/Anil-matcha/wan-3.0-comfyui): focused ComfyUI nodes for Wan 3.0, including the spicy tier.
- [seedance2.5-comfyui](https://github.com/Anil-matcha/seedance2.5-comfyui): focused ComfyUI nodes for Seedance 2.5, including spicy text and image to video.
- [awesome-uncensored-ai-video-models](https://github.com/Anil-matcha/awesome-uncensored-ai-video-models): a community catalog of open, low-filter and community-reported AI video models.
- [Muapi](https://muapi.ai): the API behind the nodes. See the [spicy video generator page](https://muapi.ai/ai-spicy-video-generator), [Seedance 2.5 Spicy](https://muapi.ai/seedance-2.5-spicy), [Wan Spicy](https://muapi.ai/wan-spicy), [MiniMax H3 Spicy](https://muapi.ai/minimax-h3-spicy), and the [ComfyUI docs](https://muapi.ai/docs/comfyui).

## License

[MIT](LICENSE)
