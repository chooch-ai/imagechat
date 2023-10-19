
[![ImageChat](https://www.chooch.com/wp-content/uploads/2023/10/ImageChatLogo.png)](https://www.chooch.com/) 
# ImageChat-3 API Documentation
#### _Created by Chooch Intelligence Technologies Co._


ImageChat is Chooch’s latest cutting-edge model that provides more detailed insights into visual images with staggering accuracy. Our new ensemble model combines computer vision and large language models to provide you with the best possible results. ImageChat-3 has over 11 billion parameters and a 5x image database improvement compared to previous versions. This enables improved conversations, multi-language support, and better image analysis. For more information on the release and an example use case, [read more on ImageChat][bloglink].

## Examples
Please see the Jupyter Notebooks Examples in _api\_examples/_ for information on how to use the ImageChat-3 API. Below we will describe the functionality and expected results. 

## Functionality
There are 5 core component features of ImageChat-3 API that enable everything from Image analysis to multi-language conversation. See below:
- [Image Prediction](#image-prediction-prompting)
- [Text Prediction](#text-prediction-prompting)
- [Document Prediction (Beta)](#document-prediction-prompting---beta)
- [Workflow Prediction](#workflow-prediction)
- [Vision Prediction](#vision-prediction)

## Post Request to ImageChat-3
Analyzing an image, document, text, etc. with ImageChat-3 is easy and allows for customizable parameters with each api call. Each post request includes a set of parameters in a JSON payload, in addition with the file you want to analyze, and your Chooch API Key. In each example in _api\_examples/_ you will see a corresponding post request that includes these 3 parameters and the ImageChat-3 url. 

### Parameters
- `prompt`: The prompt for analysis, by default it is "Describe this image in detail"
- `lang`: _Optional_ Language to provide results in, see bottom of documentation for options
- `max_new_tokens`: _Optional_ Maximum new tokens setting
- `source_id`: Reference to include to continue a conversation from a previous prompt


This is the example parameters and reference to file path, model_id, and api key. Please see the examples for proper usage. 
```python
# set parameters
parameters = {}

# Set the automated prompt for the image
prompt = "Describe this image in detail"
parameters["prompt"] = prompt


# Optional language parameter 
# parameters["lang"] = "es"

# Optional maximum new tokens setting
#parameters["max_new_tokens"] = 512
```
Usage in python takes the provided parameters and builds a post request with the necessary information for the ImageChat-3 API. 

```
# Path to your file
file_path = "files/recognize-man.jpg"

# Set Model as ImageChat-3
model_id = "chooch-image-chat-3"

# Place your API Key Here
api_key = "xxxxx-xxxx-xxxx-xxx-xxxxxxxx"

# Build the ImageChat-3 URL
host_name = "https://chat-api.chooch.ai"
url = "{}/predict?api_key={}".format(host_name, api_key)

payload = {
      "parameters": parameters
    }

file = {'file': open(file_path, 'rb')}
response = requests.post(url, data=payload, files=file)
```
Get your API Key by siging up to a free account at [https://app.chooch.ai/](https://app.chooch.ai/)

## Expected Results

```js
{'model_title': 'Chooch-ImageChat-3', 'model_id': 'Chooch-ImageChat-3', 'prediction': 'La imagen muestra a un hombre con un chaleco de seguridad y un casco acostado en el suelo junto a un conjunto de escaleras. El hombre parece herido o angustiado, ya que sostiene su cabeza en sus manos. Las escaleras están hechas de metal y se encuentran en un gran almacén o en un entorno industrial.', 'prediction_type': 'Chooch-ImageChat-3-Image', 'prompt': 'Describe this image in detail', 'source_id': '2dbe8831-eb66-4769-9df4-0478c54c14f0.jpg', 'source_type': 'image', 'status': 'Successful Prediction'
```
Each result is a JSON object that includes:
- `prediction` _This will be the verbal analysis in the requested language_

Additional included results:
- `model_title` 
- `model_id`
- `prediction_type`
- `source_id`
- `source_type`
- `status`


Please check api_examples for all Api Examples and Code.

# Image Prediction (Prompting):
Image Prompting allows users to upload an image and receive an AI-generated prediction regarding its content. Users can engage in a conversation with the AI about the image's content, making it an interactive experience. Supported image formats for this functionality are: `.jpg`, `.jpeg`, and `.png`.

# Text Prediction (Prompting):
Text Prediction is designed for those who wish to initiate a dialogue directly with the AI without the need for an image. Simply input your text, and the AI will generate a response, facilitating a seamless conversational experience. 

# Document Prediction (Prompting) - Beta:
Document Prediction enables users to upload text-based files, which the AI will generate a prediction about the document's content. Not only does this offer insights into the document, but users can also chat with the AI about the content, enhancing understanding and clarity. The supported formats for this feature are `.txt`, `.pdf`, `.doc`, `.docx`, `.ppt`, `.pptx`, `.csv`, `.xls`, and `.xlsx`.

# Workflow Prediction:
The Workflow Prediction offers an advanced fusion of object detection models with ImageChat capabilities. Users have the flexibility to combine the ImageChat LLM Vision Model with Chooch's ReadyNow Models or even integrate their own Custom Object Detection models. This ensures detailed and specific results.  For instance, you can create a Workflow by writing  the prompt "is there any person with a backpack?", followed by integrating Chooch's General Object Detection 4.0 (80) model with the "person" class.  The AI will first identify the "person" and then direct the prompt question exclusively to that identified person cut out.

# Vision Prediction:
This section provides a standalone API designed for those who have existing custom object detection models or are utilizing Chooch's ReadyNow models. It serves as a dedicated platform to execute and analyze predictions derived from these models.


## Behind ImageChat-3

ImageChat  was developed by Chooch beginning in 2022 to use innovative and novel methods of machine learning to analyze images and video content. The rising use of Generative AI and Transformers had yet to showcase useful functionality on visual content. ImageChat changes that, and with the 3rd iteration, ImageChat-3, Chooch has built a robust, multi-modal offering that can answer questions with increased accuracy, in mulitple languages, and a multitude of different file types including images, documents, and more. Chooch enables additional computer vision functionality on the Chooch AI Vision Studio Solution available at [Chooch.com](https://chooch.com/).

[![ImageChat](https://www.chooch.com/wp-content/uploads/2023/09/Chooch-logo.png)](https://www.chooch.com/) 

## Python Libraries

ImageChat-3 API calls work best in python when using these libraries:

| Python Library | Function |
| ------ | ------ |
| requests | Facilitates Put Requests to send to ImageChat-3 Server |
| json | Easy usage and manipulation of the returned JSON object |
| PIL | Pillow allows you to easy alter and convert images for best results when sending to ImageChat-3 |

## Languages

`af` ("Afrikaans"), `ak` ("Akan"), `sq` ("Albanian"), `am` ("Amharic"), `ar` ("Arabic"), `hy` ("Armenian"), `as` ("Assamese"), `ay` ("Aymara"), `az` ("Azerbaijani"), `bn` ("Bangla"), `eu` ("Basque"), `be` ("Belarusian"), `bho` ("Bhojpuri"), `bs` ("Bosnian"), `bg` ("Bulgarian"), `my` ("Burmese"), `ca` ("Catalan"), `ceb` ("Cebuano"), `zh` ("Chinese"), `co` ("Corsican"), `hr` ("Croatian"), `cs` ("Czech"), `da` ("Danish"), `dv` ("Divehi"), `nl` ("Dutch"), `en` ("English"), `eo` ("Esperanto"), `et` ("Estonian"), `ee` ("Ewe"), `fil` ("Filipino"), `fi` ("Finnish"), `fr` ("French"), `gl` ("Galician"), `lg` ("Ganda"), `ka` ("Georgian"), `de` ("German"), `el` ("Greek"), `gn` ("Guarani"), `gu` ("Gujarati"), `ht` ("Haitian Creole"), `ha` ("Hausa"), `haw` ("Hawaiian"), `iw` ("Hebrew"), `hi` ("Hindi"), `hmn` ("Hmong"), `hu` ("Hungarian"), `is` ("Icelandic"), `ig` ("Igbo"), `id` ("Indonesian"), `ga` ("Irish"), `it` ("Italian"), `ja` ("Japanese"), `jv` ("Javanese"), `kn` ("Kannada"), `kk` ("Kazakh"), `km` ("Khmer"), `rw` ("Kinyarwanda"), `ko` ("Korean"), `kri` ("Krio"), `ku` ("Kurdish"), `ky` ("Kyrgyz"), `lo` ("Lao"), `la` ("Latin"), `lv` ("Latvian"), `ln` ("Lingala"), `lt` ("Lithuanian"), `lb` ("Luxembourgish"), `mk` ("Macedonian"), `mg` ("Malagasy"), `ms` ("Malay"), `ml` ("Malayalam"), `mt` ("Maltese"), `mi` ("Māori"), `mr` ("Marathi"), `mn` ("Mongolian"), `ne` ("Nepali"), `nso` ("Northern Sotho"), `no` ("Norwegian"), `ny` ("Nyanja"), `or` ("Odia"), `om` ("Oromo"), `ps` ("Pashto"), `fa` ("Persian"), `pl` ("Polish"), `pt` ("Portuguese"), `pa` ("Punjabi"), `qu` ("Quechua"), `ro` ("Romanian"), `ru` ("Russian"), `sm` ("Samoan"), `sa` ("Sanskrit"), `gd` ("Scottish Gaelic"), `sr` ("Serbian"), `sn` ("Shona"), `sd` ("Sindhi"), `si` ("Sinhala"), `sk` ("Slovak"), `sl` ("Slovenian"), `so` ("Somali"), `st` ("Southern Sotho"), `es` ("Spanish"), `su` ("Sundanese"), `sw` ("Swahili"), `sv` ("Swedish"), `tg` ("Tajik"), `ta` ("Tamil"), `tt` ("Tatar"), `te` ("Telugu"), `th` ("Thai"), `ti` ("Tigrinya"), `ts` ("Tsonga"), `tr` ("Turkish"), `tk` ("Turkmen"), `uk` ("Ukrainian"), `ur` ("Urdu"), `ug` ("Uyghur"), `uz` ("Uzbek"), `vi` ("Vietnamese"), `cy` ("Welsh"), `fy` ("Western Frisian"), `xh` ("Xhosa"), `yi` ("Yiddish"), `yo` ("Yoruba"), `zu` ("Zulu")

## License

Usage of ImageChat is subject to the Chooch terms & conditions and user agreement. All models and example code belong to Chooch Intelligence Technologies Co (C) 2023.

**Make the world a better place with AI**

[//]: # (Reference Links)
