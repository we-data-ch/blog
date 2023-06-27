---
title: "Your first chat bot with python!"
author: "David Munoz Tord"
date: "2023-06-28"
categories: ["Python", "AI"]
tags: ["language models", "llm", "chatGPT"]
---



By [David Munoz Tord](https://twitter.com/tord_munoz)

**Goal**: Learn about *language models* and familiarize yourself with some of the basic functions of the {[languagemodels](https://github.com/jncraton/languagemodels)} to create your own chat bot.

{[languagemodels](https://github.com/jncraton/languagemodels)} is a python module designed to be as simple as possible for learners and educators exploring how large language models intersect with modern software development. The interfaces to this package are all simple functions using standard types. The complexity of large language models is hidden from view while providing free local inference using light-weight, open models. All included models are free for educational use, no API keys are required, and all inference is performed locally by default.

[Read more about it](https://github.com/jncraton/languagemodels)

You can morph between plot like this:




```python

import languagemodels as lm
lm.do("What color is the sky?")
## 'The color of the sky is blue.'
```
<br/>

To easy, let's try something a bit harder


```python
lm.do("If I have 7 apples then eat 5, how many apples do I have?")
## 'You have 8 apples.'
```

Aouch...

Indeed the model performance is quite low because the models used by this package are 1000x smaller than the largest models in use today. They are useful as learning tools, but if you are expecting ChatGPT or similar performance, you will be very disappointed...

The base model should work on any system with 512MB of memory, but this memory limit can be increased. Setting this value higher will require more memory and generate results more slowly, but the results should be superior. Let's try:


```python
lm.set_max_ram('4gb')
## 4.0
lm.do("If I have 7 apples then eat 5, how many apples do I have?")
## 'I have 2 apples left.'
```
Yeah, here we go little (4gb) buddy!

<br/>

Now that we got the basics, let's play with it!


```python

lm.chat('''
     System: Respond as a helpful assistant.

     User: What is relativity?

     Assistant:
     ''')
## 'Relativity is a theory of the universe that states that all objects in the universe are moving at the same rate and with the same acceleration. It was developed by Albert Einstein in 1887, and it describes how time and space are related to each other.'
```
<br/>



```python

lm.complete("She hid in her room until")
## ' the storm passed.'
```
<br/>



```python

lm.get_wiki("Physics")
## 'Physics is the natural science of matter, involving the study of matter, its fundamental constituents, its motion and behavior through space and time, and the related entities of energy and force. Physics is one of the most fundamental scientific disciplines, with its main goal being to understand how the universe behaves. A scientist who specializes in the field of physics is called a physicist.\nPhysics is one of the oldest academic disciplines and, through its inclusion of astronomy, perhaps the oldest. Over much of the past two millennia, physics, chemistry, biology, and certain branches of mathematics were a part of natural philosophy, but during the Scientific Revolution in the 17th century these natural sciences emerged as unique research endeavors in their own right. Physics intersects with many interdisciplinary areas of research, such as biophysics and quantum chemistry, and the boundaries of physics are not rigidly defined. New ideas in physics often explain the fundamental mechanisms studied by other sciences and suggest new avenues of research in these and other academic disciplines such as mathematics and philosophy.\nAdvances in physics often enable new technologies. For example, advances in the understanding of electromagnetism, solid-state physics, and nuclear physics led directly to the development of new products that have dramatically transformed modern-day society, such as television, computers, domestic appliances, and nuclear weapons; advances in thermodynamics led to the development of industrialization; and advances in mechanics inspired the development of calculus.'
```
<br/>
