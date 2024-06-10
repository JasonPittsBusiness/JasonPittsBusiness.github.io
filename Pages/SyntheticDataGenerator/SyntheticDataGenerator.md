---
layout: inner
title: Synthetic Data Generator
permalink: /Synthetic Data Generator/
SyntheticData_project: 'SyntheticDataGenerator'
---
<h1 style="text-align: center;">Synthetic Data Generator</h1>
<h4 style="text-align: center;">By Jason Pitts</h4>


# Overview
<div>
{% if page.ZenNest_project != '' %}
    <a href="https://github.com/{{ site.github_username }}/{{ page.SyntheticData_project }}" class="btn btn-default btn-lg"><i class="fa fa-square-github fa-lg"></i> GitHub</a>
{% endif %}
</div>

Are you looking to protect personally identifiable information (PII) in your datasets while complying with stringent privacy regulations like GDPR? This project introduces the foundational techniques for generating synthetic data—data created by AI models trained on real-world datasets. The primary goal is to replicate the statistical distribution of original data, thereby eliminating any possibility of identifying the individuals involved.
<br>

## Who is this for?
<br>
This guide is designed for data scientists, software engineers, and privacy officers who are looking to enhance data privacy without compromising on data utility. An intermediate understanding of Python and data manipulation techniques is essential to grasp the concepts discussed.
<br>
## What will you learn?
<br>
You will learn advanced data manipulation techniques using Generative Adversarial Networks (GANs) to produce synthetic datasets. These datasets maintain the integrity of the original data distributions while ensuring complete anonymity of the data subjects.
<br>
## Why is this important?
<br>
Creating synthetic data is crucial for organizations that need to use sensitive data for analytics and machine learning training without violating privacy laws. By the end of this project, you will be able to generate synthetic datasets that are safe to use for research and development, free from privacy concerns.

<br>
The dataset can be found [here on Kaggle](https://www.kaggle.com/datasets/denisadutca/customer-behaviour?resource=download) and the [python code here](https://github.com/JasonPittsBusiness/SyntheticDataGenerator/blob/main/GenerateSyntheticData.py). Libraries used are pandas, sdv (synthesizer), matplotlib, sdmetrics, and seaborn.
<br>

## Case: Customer Dataset
<br>
The dataset in question is a customer database that contains 400 clients who either bought a product or did not. Their age demographic as well as their income is included. Combining any number of these simple statistics would allow for identification of a client. This data could be incredibly insightful for understanding customer behaviours and with more columns we could learn even more. Our business objective in this case would be to obscure the identity of the clients completely for their protection and our compliance. In an age where data leaks are constant and the effects are drastic we can remediate this with synthetic data.

## Handling the dataset
<br>
The chosen dataset was used because of the relevant small number of entries (400) which gives us an interesting set of problems to look at. With a smaller dataset we are bound (though not required) to have outliers that will cause inconsistencies in the generation of synthetic data. 

![SampleDataPreview](\Pages\SyntheticDataGenerator\DataPreview-1130.png)
*Preview of our data*

<br>

Only one column stands out here as problematic which is the User ID. The User ID serves no purpose as a key identifier in this case so we'll remove it before processing the data. Once that has been removed we are ready to use the [CTGANSynthesizer](https://docs.sdv.dev/sdv/single-table-data/modeling/synthesizers/ctgansynthesizer). This model was chosen because it is a good entry level model to synthesizing data due to quick results and feedback allowing constant iteration on your data for correlation.

```
def synthesize_data(metadata, data, filepath):
    synthesizer = CTGANSynthesizer(metadata, enforce_rounding=False, epochs=200, verbose=True, cuda=True)
    synthesizer.fit(data)
    synthetic_data = synthesizer.sample(num_rows=len(data), batch_size=400, max_tries_per_batch=100)
    synthetic_data.to_csv(filepath, index=False)
    return synthesizer, synthetic_data
```
*Function to create synthesized data parameterized.* [Learn More](https://docs.sdv.dev/sdv/single-table-data/modeling/synthesizers/ctgansynthesizer)

<br>

## Synthesis
<br>
Upon running the script you'll find that it runs you through a number of steps, lets review them.
<br>

- Metadata setup
- Data Synthesis
- Plot data loss
- Review data quality reports
- Plot correlation matrix

<br>

Assuming your dataset loads properly you can move onto creating the metadata for the synthesis process. It should look something like this.
<br>

![SampleMetaData](\Pages\SyntheticDataGenerator\my_metadata-1130.png)
*For our simple dataset the metadata is quite simple*

<br>
Moving onto the synthesis of the data you'll need to review the dataloss from the discriminator and the generator. The generator is responsible for creating data while the discriminators job is to differentiate between the synthesized and the real. Ideally we will deceive the discriminator as much as possible.
<br>

![DiscriminatorVSGenerator](\Pages\SyntheticDataGenerator\DiscriminatorVSGenerator.png)
*Discriminator and Generator converging at ~300 epochs*

<br>

# Validity and quality
<br>
Review the distributional comparisons of validity and struct as they must come back at 100% or your synthetic data is not being created properly. This could be due to formatting issues in the metadata or the original dataset.
<br>
After this a return of quality will determine the functional result of your data. The column shape dictates the distribution likeness while the pair trends speak to the relationships of the datasets. Effectively you should aim for at least 80% on both scores to have a functional synthesis.

<br>

Finally you will be prompted for a correlation matrix which will help you compare correlations in the original data to the synthesis data. Your initial results should look something like this with the base tuning.
<br>

![CorrelationMatrix](\Pages\SyntheticDataGenerator\SyntheticCorrelationMatrix-1130x864-2x.png)
*Further iterations required, try adjusting the epochs!*

# Conclusion
Synthesizing data has a low barrier to entry but a high ceiling for excellence. In order to use your synthesis data effectively you will need to continue to iterate on your model until it is learning at an appropriate rate to no longer be able to discriminate between real and synth data. Outliers in small datasets will cause issues and may be a consideration of exclusion. You're now equipped to start synthesizing, what are you waiting for?
