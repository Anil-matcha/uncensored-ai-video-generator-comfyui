# FAQ

**Do I need a graphics card?** No. ComfyUI runs on your computer, but the video model runs on a server through the Muapi nodes. Almost any computer that can run ComfyUI will work.

**Is it free?** The node pack and this guide are free. Generating videos is pay as you go on Muapi, so each clip has a cost.

**Where are the workflows?** In the `workflows/` folder of [SamurAIGPT/muapi-comfyui](https://github.com/SamurAIGPT/muapi-comfyui). Load one with File, then Load in ComfyUI, and choose a spicy model from the `model` dropdown.

**The model I want is not in the dropdown.** Choose `custom` in the `model` dropdown and type the endpoint name (for example `wan3.0-spicy-text-to-video`) in the `custom_endpoint` field.

**What does "spicy" mean here?** The same underlying model with much lighter content filtering than the big mainstream tools. Baseline platform rules still apply, so use it responsibly.

**Where do I set resolution or sound?** In the node's `extra_params_json` field, for example `{"resolution": "1080p", "enable_audio": true}`. See the model table in the [README](README.md) for what each model accepts.
