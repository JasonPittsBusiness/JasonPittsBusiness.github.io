---
layout: inner
title: ZenNest Chatbot
permalink: /ZenNest Chatbot/
ZenNest_project: 'ZenNestChatbot'
---
<h1 style="text-align: center;">ZenNest Chatbot Assistant</h1>
<br>
## Overview
<div>
{% if page.ZenNest_project != '' %}
    <a href="https://github.com/{{ site.github_username }}/{{ page.ZenNest_project }}" class="btn btn-default btn-lg"><i class="fa fa-square-github fa-lg"></i> GitHub Code</a>
{% endif %}
</div>
<br>
Welcome to the ZenNest Chatbot assistant overview! This project leverages OpenAI's API to create a customer service chatbot for the ZenNest home system. The ZenNest home system is a futuristic home automation system that integrates with a chatbot assistant that aims to solve user issues quickly and efficiently. This chatbot was trained using Python, JSON training data, and integrated with Weights and Biases to record training results. Following along with this project, you will gain a basic understanding of working with LLMs, specifically OpenAI's API, to achieve desired results.
<br>
<br>
### Things you will need
Note: Training GPT models is not free, though it is relatively [inexpensive](https://openai.com/api/pricing/). (gpt-3.5-turbo for this project)
<br>
1. A rudimentary understanding of [Python](https://www.python.org/)
2. An [OpenAI](https://platform.openai.com/docs/overview) account for access to the API
3. 1-2 USD to pay for the model training
4. [Weights & Biases](https://wandb.ai/site) account to visualize your training results
5. An [IDE](https://www.codecademy.com/article/what-is-an-ide) (e.g., [VSCode](https://code.visualstudio.com/), [PyCharm](https://www.jetbrains.com/pycharm/)) and a [Python environment](https://www.python.org/downloads/)
6. [Training data](https://www.cloudfactory.com/training-data-guide) (Inlcuded for this project)

# Table of Contents
1. [Introduction](#introduction)
2. [Project Structure](#project-structure)
3. [Data Preparation](#data-preparation)
4. [Training Process](#training-process)
5. [Validation and Results](#validation-and-results)
6. [Comparative Analysis](#comparative-analysis)
7. [Integration with ZenNest](#integration-with-zennest)
8. [Usage Instructions](#usage-instructions)
9. [Screenshots](#screenshots)
10. [Conclusion](#conclusion)
<br>