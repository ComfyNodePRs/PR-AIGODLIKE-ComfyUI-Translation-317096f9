# AIGODLIKE-COMFYUI-TRANSLATION
A plugin for multilingual translation of [ComfyUI](https://github.com/comfyanonymous/ComfyUI)，This plugin implements translation of resident menu bar/search bar/right-click context menu/node, etc
## ComfyUI users in other languages, I need your help
I hope ComfyUI can support more languages besides Chinese and English, such as French, German, Japanese, Korean, etc. However, I believe that translation should be done by native speakers of each language. So I need your help, let's go fight for ComfyUI together!
## Language supported
1. 简体中文
2. English
## Function
1. Translate all UI of ComfyUI
![image](https://github.com/AIGODLIKE/AIGODLIKE-COMFYUI-TRANSLATION/assets/116185401/323f3f84-e9c0-421e-9089-470e5a5ac350)
![image](https://github.com/AIGODLIKE/AIGODLIKE-COMFYUI-TRANSLATION/assets/116185401/620d274a-3fb5-430e-8584-2705e9fbeb4c)
![image](https://github.com/AIGODLIKE/AIGODLIKE-COMFYUI-TRANSLATION/assets/116185401/ab711245-c4f0-43ec-b22b-7191bbd66e40)
2. Direct language switching (limitation: custom names will be removed)
https://github.com/AIGODLIKE/AIGODLIKE-COMFYUI-TRANSLATION/assets/116185401/e43182b7-8932-4358-bc65-ade7bddf27c5
3. Support for adding other languages
4. Support translation custom nodes
## How to install
AIGODLIKE-COMFYUI-TRANSLATION is equivalent to a custom node, you can use any method you like, just put it in folder custom_nodes
Then run:
```sh
cd ComfyUI/custom_nodes
git clone https://github.com/AIGODLIKE/AIGODLIKE-COMFYUI-TRANSLATION.git
```
![image](https://github.com/AIGODLIKE/AIGODLIKE-COMFYUI-TRANSLATION/assets/116185401/44de967d-2611-4f07-a795-9b28169d51f5)
## How to use
Launch ComfyUI and open the menu. Click on the language option to switch languages.
![image](https://github.com/AIGODLIKE/AIGODLIKE-COMFYUI-TRANSLATION/assets/116185401/74d184ac-e7ef-4059-bd5e-dfb6fd4a64ac)

## How to add other languages（translator）
1. Create a new 'Language Name' folder in the plugin directory (e.g. example folder)
![image](https://github.com/AIGODLIKE/AIGODLIKE-COMFYUI-TRANSLATION/assets/116185401/1288e2ca-aef2-4810-a718-2458261d9153)

2. Find the LocaleMap.js file and add the language code with the same name as the first step folder in it
![image](https://github.com/AIGODLIKE/AIGODLIKE-COMFYUI-TRANSLATION/assets/116185401/443f36f7-aeaf-4359-b55c-a6287d3ad1ef)
    ```js
    export const LOCALES = {
        "zh-CN": {
            "nativeName": "中文",
            "englishName": "Chinese Simplified"
        },
        "en-US": {
            "nativeName": "English (US)",
            "englishName": "English (US)"                    
        },
        "example": {
            "nativeName": "exampleDisplayName",
            "englishName": "enName"
        },
    }
    ```
3. After completing the above two steps, restart the ComfyUI service to find the 'exampleDisplayName' language type in the 'AGLTranslation language' settings bar
![image](https://github.com/AIGODLIKE/AIGODLIKE-COMFYUI-TRANSLATION/assets/116185401/f3ea8ab6-8626-4470-a6e0-d8eee50358aa)

## How to add custom node translations（translator）
1. Translation files are currently divided into three types
    1. Node information translation (including node name, node connector, node component) corresponding translation file `Your language folder/Nodes/somenode.json`
    2. Node classification information (used for right-click the new node menu) corresponds to the translation file `Your language folder/NodeCategory.json`
    2. Menu information (including resident menu, settings panel, right-click context menu, search menu, etc.) corresponds to translated files `Your language folder/Menu.json`
2. Node information translation can be placed in multiple JSON files under 'Your language folder/Nodes/' based on different nodes
3. All translation files are in JSON format, please fill in strictly according to the JSON file format

### Translation examples
1. Node Translation Format
    ```json
    {
        "KSampler": {
            "title": "KSampler[example translation]",
            "inputs": {
                "model": "模型",
                "positive": "正向提示词",
                "negative": "反向提示词",
                "latent_image": "潜空间"
            },
            "widgets": {
                "seed": "随机种",
                "control_after_generate": "运行后操作",
                "steps": "步数",
                "cfg": "CFG",
                "sampler_name": "采样器",
                "scheduler": "调度器",
                "denoise": "降噪"
            },
            "outputs": {
                "LATENT": "潜空间",
            }
        },
        "Load VAE": {}
    }
    ```
2. Node classification translation format
    ```json
    {
        "Add Node": "Add Node[example]",
        "Add Group": "Add Group[example]",
        "Search": "Search[example]",
        "Queue size:": "Queue size[example]:",
        "Queue Prompt": "Queue Prompt[example]",
        "Extra options": "Extra options[example]"
    }
    ```
3. Menu information translation format
    ```json
    {
        "conditioning": "conditioning[example]",
        "latent": "latent[example]",
        "loaders": "loaders[example]",
        "image": "image[example]"
    }
    ```

## Limitations
1 Supports direct switching of any language node to the target language, but will lose custom names
2 A small portion of options that use Enum type data cannot be translated
![image](https://github.com/AIGODLIKE/AIGODLIKE-COMFYUI-TRANSLATION/assets/116185401/75e00657-7777-482e-8144-9b13ed91f4ea)

