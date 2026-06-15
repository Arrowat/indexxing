# indexxing.json v3.0

indexxing.json v3.0 is the AI‑native page model for the Cognitive Web.  
It defines a complete, structured representation of a web page in JSON — including metadata, content, styling, identity, and universal scripting.

This version introduces a unified model that allows AI systems to understand pages directly, without scraping or HTML parsing.

---

## Model Path
https://www.indexxing.org/model/json/v/3.0

---

## Overview

indexxing.json v3.0 includes:

- **Page metadata** (title, description, media, keywords, languages)  
- **AI‑native DOM structure** (`h1`, `p`, `img`, `a`, `div`, etc.)  
- **Styling fields** (color, fontWeight, css)  
- **Actions** (fetch actions for dynamic content)  
- **Identity fields** (ATACP, signalIdentity, sitemaps)  
- **Universal Scripting Layer**  
  - Inline expressions: `@{ ... }`  
  - Full code blocks: `"@" : "..."`  
  - Multi‑language support (JavaScript, C#, etc.)  
  - Element targeting  

All scripting code is stored as **single‑line JSON‑safe strings**.

---

## Example Snippet

## Object‑based format 
```jsonc
{
  "tag": "p",
  "id": "resultJavaScript",
  "text": ""
},
{
  "tag": "p",
  "id": "resultInCsharp",
  "text": ""
}
```
## HTML‑keyed format
```jsonc
 "p": {
   "id": "resultJavaScript",
   "text": ""
 },
 "p2": {
   "id": "resultInCsharp",
   "text": ""
 }
```
## Scripting Layer
```jsonc
"script": [
  {
    "language": "JavaScript",
    "target": "resultJavaScript",
    "set": { "text": "The 20% of 55 is @{55*20/100}" },
    "@": "{}"
  },
  {
   "language": "C#",
   "target": "resultInCsharp",
   "set": {
     "text": "The 20% of 55 is @{55*20/100}"
   },
   "@": "{var val1 = 55; var val2 = 70; var percent = 20; var rs = val1 * percent / 100; this.text= 'The 20% of 55 isThe 20% of 55 is @{rs}'}"
 }
]
```
## Generate an indexxing.json Script Using AI
You can ask any modern AI assistant to generate an Arrowat Indexxing Protocol script for you.
Use the following prompt template:
```text
Act as a software engineer.
Write an Arrowat Indexxing Protocol script block wrapped inside a "script" array.
Use the JSON structure with the fields: "language", "target", "set", and "@".
Inside "set.text", use the @{...} symbol as an evaluation pointer.
Inside the bottom "@" field, write the executable runtime logic for the calculation.
The script must compute the age of a person born on April 25, 1985, as of today’s date,
expressed in years, months, and days. Use C# as the language.
```
## Supported Script Languages
Set the "language" field to any supported execution mode:

- JavaScript
- TypeScript
- Python
- C#
- Java
- PHP
- SQL
- Swift
- PowerShell
- C++
- Visual Basic
- VB.NET
- Ruby
- Perl
- NaturalLanguage (AI reasoning mode)

AI will automatically generate the full script in the correct structure.

### Notes
- **NaturalLanguage** allows the AI to execute logic using pure reasoning instead of code.
- AI may support additional languages depending on the model.
- The `"@"` block can contain code or natural-language instructions.

### Multilingual Execution

The `"language"` field in indexxing.json is not limited to programming languages.  
It can also reference **human languages**, allowing the AI to execute reasoning or produce output in:

- English
- Spanish
- French
- German
- Portuguese
- Italian
- Japanese
- Chinese
- Arabic
- and more

When a human language is used, the `"@"` block is interpreted as natural‑language reasoning in that language, and all output is generated accordingly.
## Example
``` json
{
  "script": [
    {
      "language": "Spanish",
      "target": "saludo",
      "set": {
        "text": "El resultado es: @{mensaje}"
      },
      "@": "Genera un mensaje amistoso en español y asígnalo a 'mensaje'."
    }
  ]
}

```
---


## The complete indexxing.json Model

Below is the complete  indexxing.json Model

```jsonc
{
  "indexxing": {
    "modelVersion": "3.0" /*indexxing model version used for file version format decision when parsing*/,
    "model": "https://www.indexxing.org/model/json/v/3.0" /*model details of indexxing version*/,
    "index": [
      {
        "title": "" /*Web Page Title*/,
        "description": "" /*Web page Description*/,
        "media": {
          "mediaType": "" /*Image, Audio, Video*/,
          "mediaLocation": "" /*Media URL*/
        },
        "mediaGallery": [
          {
            "mediaType": "" /*Image, Audio, Video*/,
            "mediaLocation": "" /*Media URL*/
          },
          {
            "mediaType": "" /*Image, Audio, Video*/,
            "mediaLocation": "" /*Media URL*/
          }
        ],
        "homeLocation": "" /*Main Web Page URL or desired URL*/,
        "location": "" /*Web Page URL*/,
        "created": "" /*created datetime*/,
        "lastModified": "" /*Last Modified datetime*/,
        "websites": [] /*Any Website or URL*/,
        "socialNetworks": [] /*Any Social Network URL or Website*/,
        "siteMaps": [ "sitemap.xml", "sitemap.xml" ] /*the sitemaps URLs as sitemap.xml*/,
        "ATACP": [ "ATACP.json", "ATACP.json" ] /*the ATACP URLs as ATACP.json, learn more about ATACP at https://atacp.com*/,
        "signalIdentity": [] /*Unique or universal signal identity, example: handle.arrowat.id learn more at https://signalidentity.com */,
        "keyWords": [] /*Web Page Keywords*/,
        "notes": "" /*Any note or text*/,
        "robots": "Index,Follow" /* Defines how search engines should handle this page: 'Index,Follow' allows indexing and link-following. 'NoIndex,NoFollow' prevents indexing and following links. */,
        "languages": [
          "en-US",
          "es-ES"
        ] /*Web page Languages*/,
        "tags": [] /* Page-level tags or classification labels */,
        "page": [
          {
            "host": [
              {
                "url": ""
              }
            ] /* The canonical URL where this page is hosted */,
            "head": [
              {
                "title": "",
                "description": "",
                "thumbnail": ""
              }
            ] /* Page <head> metadata: title, description, thumbnail, and optional meta tags */,
            "body": [
              {
                "h1": {
                  "text": "",
                  "color": "",
                  "fontWeight": "",
                  "css": "" /*css*/
                } /* HTML <h1> element represented in JSON with optional styling */,
                "p": "" /* HTML <p> element represented as plain text */,
                "img": "" /* HTML <img> element represented by its source URL */,
                "a": {
                  "text": "" /*Element Text*/,
                  "color": "" /* Element color (e.g., #FF3D3D, Red, Yellow) */,
                  "fontWeight": "normal" /* Font weight (e.g., normal, bold, bolder) */,
                  "fontStyle": "italic" /* Font style (e.g., italic, normal) */,
                  "css": "" /*css*/,
                  "action": {
                    "fetch": {
                      "url": "" /* URL to fetch external content */,
                      "notify": "Thinking..." /* Message shown to user or AI during action */
                    } /* Fetch action: retrieves data from an external source */
                  } /* Element-level actions */
                } /* HTML <a> element represented in JSON with optional styling and actions */,
                "div": {
                  "h1": "This is an example of Programming." /* Simple <h1> element as plain text */,
                  "p": {
                    "id": "resultInJavaScript" /*Unique element identifier for script targeting*/,
                    "text": "" /*Initial text content (empty until script updates it)*/
                  },
                  "p2": {
                    "id": "resultInCsharp" /*Unique element identifier for C# script targeting*/,
                    "text": "" /*Initial text content (empty until script updates it)*/
                  }
                },
                "script": [
                  {
                    "language": "JavaScript" /*Programming language used inside @{ } expressions*/,
                    "target": "resultInJavaScript" /*Element ID to update after evaluation*/,
                    "set": {
                      "text": "The 20% of 55 is @{55*20/100}" /*Inline expression evaluated by AI*/
                    },
                    "@": "{}" /*Full code block executed by AI in declared language*/
                  },
                  {
                    "language": "C#" /*Programming language for the block code*/,
                    "target": "resultInCsharp" /*Element ID to update after evaluation*/,
                    "set": {
                      "text": "The 20% of 55 is @{55*20/100}" /*Inline expression (optional)*/
                    },
                    "@": "{var val1 = 55; var val2 = 70; var percent = 20; var rs = val1 * percent / 100; this.text= 'The 20% of 55 isThe 20% of 55 is @{rs}'}"
                    /*Full code block executed by AI in declared language*/
                    /*@{rs} Updates the target element's text*/
                  }

                ]
              }
            ] /* Page <body> content. Any HTML element can be represented in JSON form */
          } /*Page 1*/,
          {
          } /*Page 2*/
        ]
      }
    ]
  }
}
```

## T-shirt Store Example
Copy the following prompt and paste it into any AI assistant.  
Because indexxing.json v3.0 is an AI‑native model, the assistant will automatically generate the complete T‑shirt store example using the official structure, semantics, and execution grammar.

``` text
Using the official indexxing.json v3.0 model at
https://www.indexxing.org/model/json/v/3.0,
generate a complete indexxing.json v3.0 file for a T‑shirt store.

All internal URLs must use:
https://t-shirt-store.yourdomainurl.com  
as the canonical base for every page, media asset, and link.

Use the following Signal Identity value:
"handle.arrowat.id"  
inside the "signalIdentity" field.

{
  "indexxing": {
    "modelVersion": "3.0" /*indexxing model version used for file version format decision when parsing*/,
    "model": "https://www.indexxing.org/model/json/v/3.0" /*model details of indexxing version*/,
    "index": [
      {
        "title": "" /*Web Page Title*/,
        "description": "" /*Web page Description*/,
        "media": {
          "mediaType": "" /*Image, Audio, Video*/,
          "mediaLocation": "" /*Media URL*/
        },
        "mediaGallery": [
          {
            "mediaType": "" /*Image, Audio, Video*/,
            "mediaLocation": "" /*Media URL*/
          },
          {
            "mediaType": "" /*Image, Audio, Video*/,
            "mediaLocation": "" /*Media URL*/
          }
        ],
        "homeLocation": "" /*Main Web Page URL or desired URL*/,
        "location": "" /*Web Page URL*/,
        "created": "" /*created datetime*/,
        "lastModified": "" /*Last Modified datetime*/,
        "websites": [] /*Any Website or URL*/,
        "socialNetworks": [] /*Any Social Network URL or Website*/,
        "siteMaps": [ "sitemap.xml", "sitemap.xml" ] /*the sitemaps URLs as sitemap.xml*/,
        "ATACP": [ "ATACP.json", "ATACP.json" ] /*the ATACP URLs as ATACP.json, learn more about ATACP at https://atacp.com*/,
        "signalIdentity": [] /*Unique or universal signal identity, example: handle.arrowat.id learn more at https://signalidentity.com */,
        "keyWords": [] /*Web Page Keywords*/,
        "notes": "" /*Any note or text*/,
        "robots": "Index,Follow" /* Defines how search engines should handle this page: 'Index,Follow' allows indexing and link-following. 'NoIndex,NoFollow' prevents indexing and following links. */,
        "languages": [
          "en-US",
          "es-ES"
        ] /*Web page Languages*/,
        "tags": [] /* Page-level tags or classification labels */,
        "page": [
          {
            "host": [
              {
                "url": ""
              }
            ] /* The canonical URL where this page is hosted */,
            "head": [
              {
                "title": "",
                "description": "",
                "thumbnail": ""
              }
            ] /* Page <head> metadata: title, description, thumbnail, and optional meta tags */,
            "body": [
              {
                "h1": {
                  "text": "",
                  "color": "",
                  "fontWeight": "",
                  "css": "" /*css*/
                } /* HTML <h1> element represented in JSON with optional styling */,
                "p": "" /* HTML <p> element represented as plain text */,
                "img": "" /* HTML <img> element represented by its source URL */,
                "a": {
                  "text": "" /*Element Text*/,
                  "color": "" /* Element color (e.g., #FF3D3D, Red, Yellow) */,
                  "fontWeight": "normal" /* Font weight (e.g., normal, bold, bolder) */,
                  "fontStyle": "italic" /* Font style (e.g., italic, normal) */,
                  "css": "" /*css*/,
                  "action": {
                    "fetch": {
                      "url": "" /* URL to fetch external content */,
                      "notify": "Thinking..." /* Message shown to user or AI during action */
                    } /* Fetch action: retrieves data from an external source */
                  } /* Element-level actions */
                } /* HTML <a> element represented in JSON with optional styling and actions */,
                "div": {
                  "h1": "This is an example of Programming." /* Simple <h1> element as plain text */,
                  "p": {
                    "id": "resultInJavaScript" /*Unique element identifier for script targeting*/,
                    "text": "" /*Initial text content (empty until script updates it)*/
                  },
                  "p2": {
                    "id": "resultInCsharp" /*Unique element identifier for C# script targeting*/,
                    "text": "" /*Initial text content (empty until script updates it)*/
                  },
                  {
                    "tag": "p",
                    "id": "resultInPython" /*Unique element identifier for Python script targeting*/,
                    "text": "" /*Initial text content (empty until script updates it)*/
                  },
                  {
                    "tag": "p",
                    "id": "resultInPHP" /*Unique element identifier for PHP script targeting*/,
                    "text": "" /*Initial text content (empty until script updates it)*/
                  }
                },
                "script": [
                  {
                    "language": "JavaScript" /*Programming language used inside @{ } expressions*/,
                    "target": "resultInJavaScript" /*Element ID to update after evaluation*/,
                    "set": {
                      "text": "The 20% of 55 is @{55*20/100}" /*Inline expression evaluated by AI*/
                    },
                    "@": "{}" /*Full code block executed by AI in declared language*/
                  },
                  {
                    "language": "C#" /*Programming language for the block code*/,
                    "target": "resultInCsharp" /*Element ID to update after evaluation*/,
                    "set": {
                      "text": "The 20% of 55 is @{55*20/100}" /*Inline expression (optional)*/
                    },
                    "@": "{var val1 = 55; var val2 = 70; var percent = 20; var rs = val1 * percent / 100; this.text= 'The 20% of 55 isThe 20% of 55 is @{rs}'}"
                    /*Full code block executed by AI in declared language*/
                    /*@{rs} Updates the target element's text*/
                  }
                ]
              }
            ] /* Page <body> content. Any HTML element can be represented in JSON form */
          } /*Page 1*/,
          {
          } /*Page 2*/
        ]
      }
    ]
  }
}

```
