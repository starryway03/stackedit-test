# Json RAG LLM


## Response 
### Chatbot Output Message JSON
- Facebook Document
  > https://developers.facebook.com/docs/whatsapp/on-premises/guides/messages
- Facebook API  
  > https://www.postman.com/meta/workspace/whatsapp-business-platform/overview
- Facebook Cloud API Media Limitation
  > https://developers.facebook.com/docs/whatsapp/cloud-api/reference/media

### **Text Message**

1. Text
    ```
    Chatbot
    {
        "recipient_id":"test",
        "text":"user message"
    }
    ```

### **Media Message**

Builder Ready (Mas Faqih): Image, Document, Video, Audio

2. Image
    ```
    Chatbot
    {
        "recipient_id":"test",
        "attachment":{
            "image": {
                "link": "http(s)://the-url",
                "caption": "your-image-caption"
            }
        }
    }
    ```

3. Document
    ```
    Chatbot
    {
        "recipient_id":"test",
        "attachment":{
            "document": {
                "link": "http(s)://the-url.pdf",
                "caption": "your-document-caption"
            }
        }
    }
    ```

4. Video
    ```
    Chatbot
    {
        "recipient_id":"test",
        "attachment":{
            "video": {
                "link": "http(s)://the-url.pdf",
                "caption": "your-document-caption"
            }
        }
    }
    ```

5. Audio
    ```
    Chatbot - Audio has no Caption key
    {
        "recipient_id":"test",
        "attachment":{
            "audio": {
                "link": "http(s)://the-url.pdf",
            }
        }
    }
    ```

### **Interactive Message**

6. Interactive Button
    ```
    Chatbot - Audio has no Caption key
    {
        "recipient_id":"test",
        "attachment":{
            "interactive": {
                "type": "button",
                "header": { # optional
                    "type": "text" | "image" | "video" | "document",
                    "text": "your text"
                    # OR
                    "image": {
                        "link": "http(s)://the-url",
                    }
                    # OR
                    "video": {
                        "link": "the-provider-name/protocol://the-url",
                    }
                    # OR
                    "document": {
                        "link": "the-provider-name/protocol://the-url",
                    },
                }, 
                # end header
                "body": {
                    "text": "your-text-body-content"
                },
                "footer": { # optional
                    "text": "your-text-footer-content"
                },
                "action": {
                    "buttons": [
                        {
                            "type": "reply",
                            "reply": {
                              "id": "unique-postback-id",
                              "title": "First Button’s Title" 
                            }
                        },
                        {
                            "type": "reply",
                            "reply": {
                              "id": "unique-postback-id",
                              "title": "Second Button’s Title" 
                            }
                        },
                        ...
                    ] 
                } 
                # end action   
            }    
            # end interactive
        }
    }
    ```

7. Interactive List
    ```
    {
        "recipient_id":"test",
        "attachment":{
            "interactive": {
                "type": "List",
                "header": { # optional
                    "type": "text" | "image" | "video" | "document",
                    "text": "your text"
                    # OR
                    "image": {
                        "link": "http(s)://the-url",
                    }
                    # OR
                    "video": {
                        "link": "the-provider-name/protocol://the-url",
                    }
                    # OR
                    "document": {
                        "link": "the-provider-name/protocol://the-url",
                    },
                }, 
                # end header
                "body": {
                    "text": "your-text-body-content"
                },
                "footer": { # optional
                    "text": "your-text-footer-content"
                },
                "action": {
                    "button": "cta-button-content"
                    "sections":[
                        {
                          "title":"your-section-title-content",
                          "rows": [
                            {
                              "id":"unique-row-identifier",
                              "title": "row-title-content",
                              "description": "row-description-content",           
                            }
                          ]
                        },
                        {
                          "title":"your-section-title-content",
                          "rows": [
                            {
                              "id":"unique-row-identifier",
                              "title": "row-title-content",
                              "description": "row-description-content",           
                            }
                          ]
                        },
                        ...
                    ]
                } 
                # end action   
            }    
            # end interactive
        }
    }
    ```

### Special Case (Aidyl Bagus Nggak Perlu)

8. Is Helpdesk
    ```
    {
        "recipient_id":"test",
        "attachment":{
            "type": "is_helpdesk",
            "division_id": "your-division-id"
            "text": "Anda akan segera dihubungkan dengan agent"
        }
    }
    ```

9. Is Fallback
    ```
    {
        "recipient_id":"test",
        "attachment":{
            "type": "is_fallback",
            "text": "Maaf saya tidak paham"
        }
    }
    ```
   
10. Is GPT
    ```
    {
    "recipient_id": "rasa user",
    "attachment": {
        "text": "OJK adalah singkatan dari Otoritas Jasa Keuangan.",
        "type": "is_gpt",
        "metadata": {
            "openai-api": {
                "id": "chatcmpl-jatis-1708081238.9068205-1c793d68-1538-422d-9940-917fab536ead",
                "object": "chat.completion",
                "created": 1708081238,
                "model": "gpt-3.5-turbo-instruct",
                "usage": {
                    "prompt_tokens": 538,
                    "completion_tokens": 16,
                    "total_tokens": 554,
                    "total_cost": 0.0008390000000000001
                }
            }
        }
    }
    }
    ```
11. IS Sentiment

## New Model LLM (22 Nov 
### Text
`
`

### Media
Response for image/document/audio/video based on WA with format:
```json
[
    [
        {
            "attachment": {
                "image": {
                    "caption": "",
                    "link": ""
                },
                "reminder": true,
                "reminder_time_delta": 120
            },
            "metadata": {},
            "recipient_id": "12345"
        }
    ]
]
```
**Image**
```json
[
    [
        {
            "attachment": {
                "image": {
                    "caption": "Sirkuit Mandalika menjadi ikon baru Nusa Tenggara Barat dan dunia otomotif Indonesia yang terletak di Kawasan Ekonomi Khusus (KEK) Mandalika, Kuta, Lombok Tengah. Sirkuit ini terkenal di dunia internasional yang diresmikan pada tahun 2021 dan menjadi destinasi unggulan. Sirkuit Mandalika juga menjadi tuan rumah dari berbagai event internasional seperti MotoGP Indonesian Grand Prix dan World Superbike. Link maps: https://maps.app.goo.gl/PuB7aYAeXDULjwGw6",
                    "link": "https://studio.ngobrol.ai/llm/files/f79faefd-ef17-447d-a6e1-39920efd556d.png"
                },
                "reminder": true,
                "reminder_time_delta": 120
            },
            "metadata": {
                "llm-api": {
                    "created": 1732242192,
                    "id": "chatcmpl-jatis-1732242192.9297051-d6218579-1cbb-4dff-9113-bc5f25a4a5e5",
                    "model": "gpt-3.5-turbo-instruct",
                    "object": "chat.completion",
                    "source_documents": [
                        {
                            "docs_id": "673ede675d799a29486836a8",
                            "docs_name": "DinPar Prov NTB AI Knowledge.pdf"
                        },
                        {
                            "docs_id": "673ede675d799a29486836a8",
                            "docs_name": "DinPar Prov NTB AI Knowledge.pdf"
                        },
                        {
                            "docs_id": "673ede675d799a29486836a8",
                            "docs_name": "DinPar Prov NTB AI Knowledge.pdf"
                        },
                        {
                            "docs_id": "673ede675d799a29486836a8",
                            "docs_name": "DinPar Prov NTB AI Knowledge.pdf"
                        }
                    ],
                    "usage": {
                        "completion_tokens": 143,
                        "inbound_tokens": 8,
                        "prompt_tokens": 2407,
                        "total_cost": 0.009998549999999998,
                        "total_tokens": 2550
                    }
                }
            },
            "recipient_id": "12345"
        }
    ]
]
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY3MTU1Njc0NywtMzA0ODE1MTc2LC0xNj
g2NzkzMjc0LC0zMzI0NTUzNjNdfQ==
-->