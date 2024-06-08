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
Welcome to the ZenNest Chatbot assistant! This project leverages OpenAI's API to create a customer service chatbot for the ZenNest home system. The ZenNest home system is a futuristic home automation system that integrates with a chatbot assistant that aims to solve user issues quickly and efficiently. This chatbot was trained using Python, JSON training data, and integrated with Weights and Biases to record training results. Following along with this project, you will gain a basic understanding of working with LLMs, specifically OpenAI's API, to achieve desired results. For detailed instructions, check out the [readme](https://github.com/JasonPittsBusiness/ZenNestChatbot/blob/main/README.md) on [GitHub](https://github.com/JasonPittsBusiness/ZenNestChatbot).

<br>

![ZenNest Mockup](\img\posts\02_ZenNestMockUp-1130x864-2x.png)
*I'm no artist, but I enjoyed making this mockup*

<br>

## Where to Start?

<br>

This project started out as a relatively simple idea: create a customer service chatbot. The fun comes in finding a key objective to focus on as an LLM such as OpenAI's ChatGPT already has a robust foundation to work with. For this purpose, I devised a home automation company, ZenNest, with a chatbot, Sarah, that can assist customers with almost anything.

<br>

The first place to start is training the model based on that idea so I started grinding away, creating training data to cover several basic objectives that the chatbot should begin to cover.

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

With my first set of training data, I split it into 80% training and 20% validation data. The validation data is crucial as we hold it back from the bot to see how it will perform on unseen conversations. The initial results looked very promising even though we are mainly working with qualitative data.

<br>

Training loss<br>
0.8562<br>
Validation loss<br>
0.7708<br>
Full validation loss<br>
0.7356<br>

<br>

Our training loss of 0.8562 is a good indicator that our first training is performing moderately well with only 80 lines of training. OpenAI typically sees large sizeable improvements with 50-100 interactions trained. The validation loss coming in lower at .7708 is a great indicator that we are also not overfitting. Finally, the full validation loss is even lower, indicating that our initial objectives are being met. So what does it look like?

<br>

![TrainingRound2](\Pages\ZenNest\ZenNestRound1x2.png)
*Base GPT Model on the left; Trained Model on the right.*

<br>

## Trouble in Paradise

<br>

So the first response looks great, with the system message set to our training message the model is already integrating into our ZenNest home system and "instantly" solving problems. However, a few common problems are arising.

<br>

![TrainingRound3](\Pages\ZenNest\ZenNestRound1x3.png)
*The bot is incredibly easy to get off topic*

<br>

## Further Fine-Tuning

<br>

So how do we fix this? Well, more training. I returned to the drawing board knowing my first attempt wouldn't be perfect as it never is. Almost doubling the training data to account for common pitfalls of LLM chatbots I started the second set of training. The second set of results started to look miles better after hours of prompt engineering.

<br>

Training loss<br>
0.5983<br>
Full validation loss<br>
0.8023<br>

<br>

As a bonus, more than common pitfalls, industry 'Zen Jargon' were trained, as well as a myriad of situations and longer conversations. Our second round of training starts off with an incredible looking .5983 training loss indicating that our model is trending towards reasonably well performance. The full validation loss of .8023 is a bit higher but this can be expected as the LLM learns more and begins to cover a wide variety of subjects. You’ll also notice that we are missing validation loss, which is due to the number of epochs compared to the data amount. Given a greater spread of epochs (3 were used in this training pass) our validation data will be more stable. We have increased the model's performance and knowledge base at the cost of possible outlier answers. So how is Sarah doing?

<br>

![TrainingRound4](\Pages\ZenNest\ZenNestRound1x4.png)
*The latest and greatest model staying on task; new Sarah to the right*

<br>

## Conclusion and Considerations

<br>

Training a custom chatbot, especially one that is an expert in a specialized industry, is a large undertaking. Training the ZenNest Chatbot to completely reach a tranquil level of understanding is out of the scope of the project, but you are now equipped with the tools necessary to fully train your own chatbot.

<br>

View the full project on [GitHub](https://github.com/JasonPittsBusiness/ZenNestChatbot).