---
description: >-
  Before you get started adding your clickable regions, you have to make sure we
  can call the Einstein API.
---

# Enable Azure OCR in your Remote Site settings & Metadata

{% embed url="https://app.tango.us/app/embed/2cf3b148-a65c-448e-8234-6966d7c81189" %}

## [Using Microsoft Azure Portal for Managing Keys and APIs for Azure AI Services](https://app.tango.us/app/workflow/2cf3b148-a65c-448e-8234-6966d7c81189?utm_source=magicCopy\&utm_medium=magicCopy\&utm_campaign=workflow%20export%20links)

Creation Date: May 24, 2024Created By: Erik Pilgrim[View most recent version](https://app.tango.us/app/workflow/2cf3b148-a65c-448e-8234-6966d7c81189?utm_source=magicCopy\&utm_medium=magicCopy\&utm_campaign=workflow%20export%20links)​

***

​

### [# Microsoft Azure portal (PWA)](https://portal.azure.com/#home)

#### 1. Click on your OCR resource, if one does not exist Create a new Document Intelligence Resource

Create a resource at [https://portal.azure.com/#create/Microsoft.CognitiveServicesFormRecognizer](https://portal.azure.com/#create/Microsoft.CognitiveServicesFormRecognizer)

![Click on your OCR resource, if one does not exist Create a new Document Intelligence Resource](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/03037b37-7b88-47a1-a047-67ed41352cfd/58d5b09c-4114-4585-9199-1e22a092e7b2.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.1216\&fp-y=0.6498\&fp-z=2.5048\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=216\&mark-y=436\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0yOTgmaD04NSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 2. Click on Copy to clipboard the value for Endpoint for this demo, ours is https://rdcentralocr.cognitiveservices.azure.com/

![Click on Copy to clipboard the value for Endpoint for this demo, ours is https://rdcentralocr.cognitiveservices.azure.com/](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/3c3ef17c-7ade-4346-b331-cec4582742af/6f391ded-b955-432e-b831-7ee5c337b290.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.9651\&fp-y=0.4378\&fp-z=2.9089\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=1017\&mark-y=417\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0xMjImaD0xMjImZml0PWNyb3AmY29ybmVyLXJhZGl1cz0xMA%3D%3D)

### # Salesforce

#### 3. Click on Quick Find

![Click on Quick Find](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/05958837-5253-49d7-bb37-57a10c1d0ba8/c79a3ac9-69e7-486b-9deb-f3ec8be67ec8.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.0938\&fp-y=0.2168\&fp-z=2.1175\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=19\&mark-y=260\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz00MzgmaD05NSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 4. Click on Trusted URLs

![Click on Trusted URLs](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/4be2602e-9bdb-4d95-9e3d-ed593c8948d1/c2a6c907-86ed-4d40-ad6f-cf5c35818822.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.0724\&fp-y=0.7141\&fp-z=2.7130\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=124\&mark-y=300\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0yMjMmaD02OSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 5. Click on New Trusted URL

![Click on New Trusted URL](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/0fd2a067-8089-4537-bbdc-0df4661345c4/2c0b1037-1036-49ce-8f65-9bd1067dbbe4.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.5957\&fp-y=0.7647\&fp-z=2.6526\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=477\&mark-y=298\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0yNDUmaD03MyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 6. Type "renderdrawocr"

![Type "renderdrawocr"](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/62bff4fd-afde-40ed-ad20-866b2f37158e/293469f9-9cca-4da1-b3a6-97dc61f1c75f.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.4688\&fp-y=0.6450\&fp-z=1.9249\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=346\&mark-y=309\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz01MDcmaD01MSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 7. Type your OCR endpoint, ours is "https://rdcentralocr.cognitiveservices.azure.com"

![Type your OCR endpoint, ours is "https://rdcentralocr.cognitiveservices.azure.com"](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/773e4ca0-98f8-4bc3-93d5-b48365b3d65d/ec9f72fa-150b-4739-a56c-43d756b71308.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.5705\&fp-y=0.6806\&fp-z=1.5600\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=204\&mark-y=315\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz03OTImaD00MSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 8. Check connect-src (scripts)

![Check connect-src (scripts)](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/0d22d48e-b161-4beb-9556-0f1e0f605cde/55e29129-fd26-4b7c-9a6b-42bd5ef33637.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.3700\&fp-y=0.6847\&fp-z=3.0420\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=571\&mark-y=305\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz01OCZoPTU4JmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D)

#### 9. Check frame-src (iframe content)

![Check frame-src (iframe content)](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/6dd7da66-eafe-48ae-ab85-9638f302bd66/e313821a-2fac-4f6b-8ed0-0c7bbbe1f2ec.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.3700\&fp-y=0.7531\&fp-z=3.1645\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=570\&mark-y=304\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz02MSZoPTYxJmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D)

#### 10. Click on Save

![Click on  Save](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/f02e3e62-1766-42d4-93e9-b0abdd2cc46a/9707cf1b-c47a-44c2-bb3d-5e7422b30c58.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.4573\&fp-y=0.9453\&fp-z=2.9845\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=537\&mark-y=518\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0xMjYmaD04MiZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

### [# Go back to your Microsoft Azure portal](https://portal.azure.com/#@erikpilgrimrenderdraw.onmicrosoft.com/resource/subscriptions/1d597bcb-347c-44b7-b5f8-a1f21b9ee35c/resourceGroups/CVRetailMFG/providers/Microsoft.CognitiveServices/accounts/RDCentralOCR/overview)

#### 11. Click on Click here to manage keys

![Click on Click here to manage keys](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/03457a21-aa2a-4e76-97c1-a04f164152c3/72ca7e97-d106-4696-937b-31cd3eda8d77.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.7470\&fp-y=0.4090\&fp-z=2.9800\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=385\&mark-y=299\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz00MzEmaD03MSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 12. Click on These keys are used to access your Azure AI services API. Do not share your keys. Store them securely– for example, using Azure Key Vault. We also recommend regenerating these keys regularly. Only one key is necessary to make an API call. When regenerating the first key,…

![Click on These keys are used to access your Azure AI services API. Do not share your keys. Store them securely– for example, using Azure Key Vault. We also recommend regenerating these keys regularly. Only one key is necessary to make an API call. When regenerating the first key,…](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/32c71d10-27c8-4212-b50e-1cce8e1ec813/a96b77b7-11d7-4361-95bf-c4f32e154ccc.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.7374\&fp-y=0.5335\&fp-z=2.9089\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=559\&mark-y=292\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz04MiZoPTg1JmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D)

#### 13. Go back to your Salesforce Instance. We need to add an OCR Metadata entry for RenderDraw

#### 14. Type "custom metadata"

![Type "custom metadata"](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/3a66439f-c354-44bd-805c-661b41506a71/8b69929f-760c-4ffa-a780-4cde8872d812.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.0938\&fp-y=0.2168\&fp-z=2.1175\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=19\&mark-y=260\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz00MzgmaD05NSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 15. Click on Custom Metadata Types

![Click on Custom Metadata Types](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/26bf927d-2970-4403-8caf-158130c39ba7/a165ba0f-2b7d-4fd5-af64-62286efa2dcd.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.0972\&fp-y=0.3256\&fp-z=2.3915\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=109\&mark-y=304\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0zMzkmaD02MSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 16. Navigate to RenderDraw OCR Setting

![Click on Del | Manage Records](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/a394cc1d-382b-4867-8084-562a1de585c6/ee5d9086-0209-4e2a-8688-7586cf8926da.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.2626\&fp-y=0.8386\&fp-z=2.5010\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=450\&mark-y=348\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0zMDAmaD0xMDEmZml0PWNyb3AmY29ybmVyLXJhZGl1cz0xMA%3D%3D)

#### 17. Click on Manage Records

![Click on Manage Records](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/290bd097-7675-44aa-878b-7926fdc57f9d/d3994c94-712c-4c7e-841c-f2a897b7fa07.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.2725\&fp-y=0.8406\&fp-z=2.6852\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=483\&mark-y=357\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0yMzMmaD01MiZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 18. Click on New

![Click on  New](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/bd4189a1-2616-4732-b295-f46a31106edc/55825c7f-6889-402d-9627-b000e2ae5b0c.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.5941\&fp-y=0.4514\&fp-z=2.9322\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=542\&mark-y=294\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0xMTUmaD04MCZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 19. Paste your key into the API Key text area

![Paste your key into the API Key text area](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/9d7ec398-fec9-400d-92eb-c0c0590142e2/fe6bf458-d436-4d34-ae06-dbbc0680460d.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.4573\&fp-y=0.6084\&fp-z=2.0135\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=362\&mark-y=283\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz00NzUmaD0xMDImZml0PWNyb3AmY29ybmVyLXJhZGl1cz0xMA%3D%3D)

### [# Microsoft Azure portal (PWA)](https://portal.azure.com/#@erikpilgrimrenderdraw.onmicrosoft.com/resource/subscriptions/1d597bcb-347c-44b7-b5f8-a1f21b9ee35c/resourceGroups/CVRetailMFG/providers/Microsoft.CognitiveServices/accounts/RDCentralOCR/cskeys)

#### 20. Click on These keys are used to access your Azure AI services API. Do not share your keys. Store them securely– for example, using Azure Key Vault. We also recommend regenerating these keys regularly. Only one key is necessary to make an API call. When regenerating the first key,…

![Click on These keys are used to access your Azure AI services API. Do not share your keys. Store them securely– for example, using Azure Key Vault. We also recommend regenerating these keys regularly. Only one key is necessary to make an API call. When regenerating the first key,…](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/05db515c-8bf0-4e04-af04-78a662148b00/6c8b7d61-7e05-489a-8f1f-6051e09bc746.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.7256\&fp-y=0.7811\&fp-z=3.4987\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=552\&mark-y=289\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz05NiZoPTkwJmZpdD1jcm9wJmNvcm5lci1yYWRpdXM9MTA%3D)

### # Salesforce

#### 21. Paste "https://rdcentralocr.cognitiveservices.azure.com/" into input

![Paste "https://rdcentralocr.cognitiveservices.azure.com/" into input](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/25eadba2-918f-47d3-a6da-6f0f8d547855/2f641281-6414-4e5c-956b-72d021bd52f7.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.4181\&fp-y=0.6631\&fp-z=2.3915\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=430\&mark-y=302\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0zMzkmaD02NSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 22. Type "AzureOCR"

![Type "AzureOCR"](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/b38e1fb8-ffec-4f8d-ac2b-0f9412aa7cd2/799625c6-8942-4a41-8bf6-6d3684eb1a5f.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.4181\&fp-y=0.5181\&fp-z=2.3915\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=430\&mark-y=302\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0zMzkmaD02NSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 23. Click on Save

![Click on  Save](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/59ba3373-1f8b-4842-8ca4-4bb035a56cb9/e2164e6a-a1f5-43d7-b3ff-f7c68e898dc4.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.4573\&fp-y=0.7671\&fp-z=2.9845\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=537\&mark-y=293\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0xMjYmaD04MyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 24. Type "remote"

![Type "remote"](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/40247752-42c3-4278-b472-c5e6be5b4733/c800d516-d45c-4f53-8ec4-10beaef9846d.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.0938\&fp-y=0.2168\&fp-z=2.1175\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=19\&mark-y=260\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz00MzgmaD05NSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 25. Click on Remote Site Settings

![Click on Remote Site Settings](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/b7ac5160-d189-445e-a125-987efc84f5e9/c99cfa01-ca7c-4e09-8402-93a6875f2e84.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.0896\&fp-y=0.4118\&fp-z=2.4820\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=114\&mark-y=303\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0zMDYmaD02NCZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 26. Click on New Remote Site

![Click on New Remote Site](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/6cbf003b-cd48-422c-9b8e-85ffb708d93e/38cb662a-f6cf-42c2-932d-0959564fa525.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.5957\&fp-y=0.5212\&fp-z=2.6634\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=479\&mark-y=298\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0yNDEmaD03MyZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 27. Type "Azure\_OCR"

![Type "Azure\_OCR"](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/f262ff50-b108-496e-a4e4-c1e5f23e5bc4/58baab1d-537f-49fb-b243-c660fd76edfc.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.4688\&fp-y=0.5192\&fp-z=1.9249\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=346\&mark-y=309\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz01MDcmaD01MSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 28. Paste "https://rdcentralocr.cognitiveservices.azure.com/" into input

![Paste "https://rdcentralocr.cognitiveservices.azure.com/" into input](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/54ca624d-ff2e-4cb9-9f98-8d04d590f2a2/3618a008-e416-4035-8480-7a834a9404e1.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.5705\&fp-y=0.5547\&fp-z=1.5600\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=204\&mark-y=314\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz03OTImaD00MSZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 29. Click on Save

![Click on  Save](https://images.tango.us/workflows/2cf3b148-a65c-448e-8234-6966d7c81189/steps/d5299248-68fd-48b0-ad2a-f4ffc6032a6e/afccb0d7-e257-4a0c-a517-1e5e9e8b1c75.png?fm=png\&crop=focalpoint\&fit=crop\&fp-x=0.4573\&fp-y=0.7839\&fp-z=2.9845\&w=1200\&border=2%2CF4F2F7\&border-radius=8%2C8%2C8%2C8\&border-radius-inner=8%2C8%2C8%2C8\&mark-x=537\&mark-y=293\&m64=aHR0cHM6Ly9pbWFnZXMudGFuZ28udXMvc3RhdGljL2JsYW5rLnBuZz9tYXNrPWNvcm5lcnMmYm9yZGVyPTYlMkNGRjc0NDImdz0xMjYmaD04MiZmaXQ9Y3JvcCZjb3JuZXItcmFkaXVzPTEw)

#### 30. Now your Salesforce instance is setup for OCR with Azure + RenderDraw
