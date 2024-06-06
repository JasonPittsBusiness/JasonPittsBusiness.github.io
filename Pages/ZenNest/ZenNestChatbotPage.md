---
layout: inner
title: ZenNest Chatbot
permalink: /ZenNest Chatbot/
ZenNest_project: 'ZenNestChatbot'
---
<h1 style="text-align: center;">ZenNest Chatbot Assistant</h1>
<h4 style="text-align: center;">By Jason Pitts</h4>
<br>
## Overview
<br>
<div>
{% if page.ZenNest_project != '' %}
    <a href="https://github.com/{{ site.github_username }}/{{ page.ZenNest_project }}" class="btn btn-default btn-lg"><i class="fa fa-square-github fa-lg"></i> GitHub</a>
{% endif %}
</div>
<br>
Welcome to the ZenNest Chatbot assistant! This project leverages OpenAI's API to create a customer service chatbot for the ZenNest home system. The ZenNest home system is a futuristic home automation system that integrates with a chatbot assistant that aims to solve user issues quickly and efficiently. This chatbot was trained using Python, JSON training data, and integrated with Weights and Biases to record training results. Following along with this project, you will gain a basic understanding of working with LLMs, specifically OpenAI's API, to achieve desired results. For detailed instructions check out the [readme](https://github.com/JasonPittsBusiness/ZenNestChatbot/blob/main/README.md) on [GitHub](https://github.com/JasonPittsBusiness/ZenNestChatbot).

<br>

![ZenNest Mockup](\img\posts\01_ZenNestMockUp-1130x864-2x.png)
*I'm no artist but I enjoyed making this mockup*

<br>

## Where to start?

<br>

This project started out as a relatively simple idea, create a customer service chatbot. The fun comes in finding a key objective to focus on as an LLM such as OpenAI's ChatGPT already has a robust foundation to work with. For this purpose I devised a home automation company ZenNest with a chatbot Sarah that can assist customers with almost anything.

<br>

The first place to start is training the model based on that idea so I started grinding away creating training data to cover several basic objectives that the chatbot should begin to cover.

- Main Objective - The purpose and identity statements of the bot
- Knowledge Base Integration - Real world knowledge of the product
- Contextual Understanding - The base model is strong but our product is specific with related jargon
- User Interaction Design - How users are expected to interact with the bot
- Multi-turn Dialogue Handling - How the bot will respond in extended conversations
- Error Handling - Unexpected user inputs can cause unexpected responses that we must account for

<br>

```
json
{
    "messages": [
        {
            "role": "system",
            "content": "Sarah is a chatbot that assists customers having trouble with their ZenNest home system."
        },
        {
            "role": "user",
            "content": "What is a ZenNest home system?"
        },
        {
            "role": "assistant",
            "content": "ZenNest is a smart home system blending technology with Zen principles for serene living. It offers security, energy management, and personalized settings for a harmonious home environment."
        }
    ]
}
```
*An example of Main Objective training*

## What were the results?

<br>

With my first set of training data I split it into 80% training to 20% validation data. The validation data is crucial as we hold it back from the bot to see how it will perform on unseen conversations. The initial results looked very promising even though we are mainly working with qualitative data.

<br>

Training loss<br>
0.8562<br>
Validation loss<br>
0.7708<br>
Full validation loss<br>
0.7356<br>

<br>

Our training loss at a value of .8562 is a good indicator that our first training is performing moderately ok with only 80 lines of training. OpenAI typically sees large sizeable improvements with 50-100 interactions trained. The validation loss coming in lower at .7708 is a great indicator that we are also not overfitting. Finally the full validation loss is even lower indicating that our intial objectives are being met. So what does it look like?
