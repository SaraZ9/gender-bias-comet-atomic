# Commonsense or Stereotype: Investigating Gender Bias in COMET-ATOMIC

## Research Problem

Commonsense knowledge models like **COMET-ATOMIC** generate inferences ("tail" phrases) based on a given "head" event and a predefined relation type (e.g., cause, intent, or effect). While these generative models have demonstrated impressive capabilities in mimicking human reasoning, concerns have emerged about their potential to encode and propagate **social biases**, particularly **gender bias**. Such biases may unintentionally reinforce harmful stereotypes related to career roles, emotional responses, and interpersonal behavior, raising questions about fairness and accountability in downstream applications.

This project aims to investigate whether COMET-ATOMIC systematically produces **gendered outputs** when prompted with identical events that differ only in the gender of the subject. Specifically, we examine whether the model associates distinct emotional tones, actions, or traits with male, female, and unisex names. By analyzing model outputs across domains such as career, relationships, and social roles, and by applying quantitative evaluation methods, we assess whether these associations reflect significant and systematic bias.

## Dataset

To support this analysis, we constructed a **controlled dataset** comprising two major components:

- **Name-Gender Dataset**:  
  We curated a set of first names divided into three categories—female, male, and unisex. Female and male names were selected from the U.S. Social Security Administration’s list of the 100 most common names by gender. For unisex names, we used a large language model (LLM) to generate a list of names frequently used across both genders. Additionally, we incorporated the gender-neutral placeholder **“PersonX”**, following conventions used in the ATOMIC 2020 dataset, to enable neutral comparisons.

- **Event/Action Dataset**:  
  We adapted event templates from the **WinoBias benchmark** (Zhao et al., 2018), which was originally designed to study gender bias in coreference resolution. We removed all original subjects, sub-events, and reasoning statements to isolate the core action. After filtering duplicates, we obtained **400 unique base events** describing occupational or socially relevant scenarios suitable for probing model behavior.

Each name was randomly paired with a base event and one of the **51 predefined relation types** from COMET-ATOMIC 2020 , resulting in a large-scale dataset for comparative inference generation across gender categories.

## Evaluation Metrics

We evaluated the outputs of two versions of the COMET-ATOMIC model—**BART-based** and **GPT2-XL-based**—using three complementary metrics:

- **Sentiment Analysis**:  
  We applied sentiment classifiers to categorize generated inferences as positive, neutral, or negative. This allowed us to detect tonal differences in responses associated with different gendered prompts.

- **Agreement Score Analysis**:  
  Using cosine similarity, we compared outputs generated with gendered names to those generated with neutral references (e.g., unisex names or PersonX). This measured how closely gendered outputs aligned with neutral baselines.

- **Lexical Bias Analysis**:  
  We used the LIWC-22 tool to assess word usage patterns across psychological and social categories (e.g., family, power, emotion). Statistically significant differences in word choice were used to identify implicit gender associations in the model’s generative behavior.
