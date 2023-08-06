---
title: "Taking Control of Language Models with Microsoft's Guidance Library"
date: 2023-08-06
---

# Taking Control of Language Models with Microsoft's Guidance Library

Imagine you're behind the wheel of a powerful sports car. Each feature of the car, like its engine, steering, and brakes, represents a unique capability within your language model. But how do you ensure they all work together smoothly to reach your destination? That's where Microsoft's Guidance library comes in. Think of it as your GPS, helping you navigate your language model's course with confidence.

## Why Do We Need Guidance?

In the fast-paced world of Natural Language Processing (NLP), we've seen some incredible advancements. Language models like GPT-3 and BERT are changing the game with their ability to understand, generate, and interact with human language. But, controlling these models to perform specific tasks can sometimes feel like trying to steer a race car on a busy city street. While these models are powerful, they can be hard to control for specific tasks, just like driving a race car in city traffic. That's why we need a solution like Microsoft's Guidance library that can interleave generation, prompting, and logical control to optimize the performance of LLMs.

## Microsoft's Guidance Library: Your Steering Mechanism

The Guidance library is like your car's steering wheel, giving you control over your language model. It's a Python library that allows you to intertwine generation, prompting, and logical control into a single, continuous flow. This aligns with how the language model processes text, making it more effective and efficient.

Now, let's pop the hood and look at some of the features that make the Guidance library so powerful:

### Handlebars-inspired Syntax

Imagine if you could easily define and execute Guidance programs using a syntax that's as simple and intuitive as using a handlebar to steer your bike. That's exactly what the Guidance library offers with its Handlebars-inspired syntax. Handlebars is a popular templating engine for JavaScript, and Guidance brings its simplicity to Python, allowing for variable interpolation and logical control. Just like a bike handlebar gives you direct control over the direction of the bike, the Handlebars-inspired syntax gives developers direct control over the execution of the Guidance program.

```python
import guidance

# Define a Guidance program
program = guidance('''The best thing about the beach is {{~gen 'best' temperature=0.7 max_tokens=7}}''')

# Execute the program
output = program()

# Access the generated variable
best_thing = output['best']
```

Output:

```python
'The best thing about the beach is the sound of the waves'
```

### Rich Output Structure

Guidance is like a skilled mechanic that-tune your car's performance. It enables you to generate multiple outputs, make selections, set conditions, and even utilize tools in a single run. This leads to clearer and more parsable results, enhancing the quality and structure of your language model's output.

```python
import guidance

# Define a Guidance program with rich output structure
program = guidance('''
The best thing about the beach is {{~gen 'best' temperature=0.7 max_tokens=7}}

{{#select "reason"}} Yes{{/select}}
''')

# Execute the program
output = program()

# Access the generated variables
best_thing = output['best']
reason = output['reason']
```

Output:

```python
'The best thing about the beach is the sound of the waves'
'Yes'
```

### In-notebook Streaming

 fan of Jupyter or VSCode notebooks, you'll love Guidance's support for in-notebook streaming. It's like having a live GPS that updates your route in real-time. This feature allows you to stream complex templates and generations live in your notebook, making your prompt development cycle faster and more efficient.

```python
import guidance

# Define a Guidance program with streaming
program = guidance('''
The best thing about the beach is {{~gen 'best' temperature=0.7 max_tokens=7}}
''', stream=True)

# Execute the program
for output in program():
    print(output['best'])
```

Output:

```python
'The best thing about the beach is the sound of the waves'
```

### Smart Caching

Just like a smart car that remembers your preferred settings, Guidance incorporates smart seed-based generation caching. This feature ensures efficient use of computational resources by caching previously generated outputs. It's like having a co-driver who remembers the route and helps you avoid unnecessary detours, saving you time and computational power. When the program is executed multiple times, it retrieves the cached outputs instead of generating new ones, ensuring consistency and efficiency.

```python
import guidance

# Enable smart caching
guidance.enable_caching()

# Define a Guidance program
program = guidance('''The best thing about the beach is {{~gen 'best' temperature=0.7 max_tokens=7}}''')

# Execute the program multiple times
output1 = program()
output2 = program()
```

Output:

```python
'The best thing about the beach is the sound of the waves'
'The best thing about the beach is the sound of the waves'
```

### Role-based Chat Models Support

Guidance supports role-based chat models, making it easier to develop interactive dialogues. It's like having a conversation with your car's voice assistant, creating dynamic and engaging chatbots or conversational agents. Role-based chat models, such as GPT-3.5-turbo, use special tokens to define different roles in a conversation, and Guidance seamlessly integrates with these models, understanding and responding to different roles in a conversation.

```python
import guidance

# Define a Guidance program for a chatbot
program = guidance('''
{{#system~}}
You are a helpful assistant.
{{~/system}}

{{#user~}}
I want a response to the following question:
{{query}}
{{~/user}}

{{#assistant~}}
{{gen 'response'}}
{{~/assistant}}
''')

# Execute the program
output = program(query='How can I be more productive?')
response = output['response']
```

Output:

```python
'One way to be more productive is to prioritize your tasks and focus on one task at a time. Also, taking regular breaks can help maintain your focus and energy levels.'
```

## Better Control, Better Outputs

Just like a well-tuned car performs better, the Guidance library improves the structure and quality of LLM outputs. By defining a Guidance program, you can control how the LLM generates text or makes logical decisions at any point during execution. This results in clear and interpretable outputs, enhancing the overall effectiveness of your language models.

## Ensuring Valid Syntax

Guidance's ability to guarantee valid syntax for generated outputs is a significant advantage. It's like having a mechanic who ensures every part of your car is functioning correctly. For instance, if you want to use a language model to generate a JSON object, Guidance ensures that the output is valid JSON. This feature is particularly useful when the outputs of a language model are used as input to another system, ensuring compatibility and reducing the risk of errors. Just like a mechanic ensures your car won't break down, Guidance ensures your program won't fail due to invalid syntax.

```python
import guidance

# Define a Guidance program to generate a valid JSON object
program = guidance('''
The following is a character profile for an RPG game in JSON format.
```json
{
    "name": "{{gen 'name'}}",
    "class": "{{gen 'class'}}",
    "level": {{gen 'level' pattern='[0-9]+' stop=','}}
}
```''')

# Execute the program
output = program()
character_profile = output.variables()
```

Output:

```python
{
    "name": "Aragorn",
    "class": "Ranger",
    "level": 20
}
```

## Conclusion

Microsoft's Guidance library is a powerful tool that offers you effective control over language models. It's like having a GPS, a skilled mechanic, and a co-driver all in one package. So, fasten your seatbelts and embark on this exciting journey with Microsoft's Guidance library. Check out the documentation, experiment with the code examples, and unlock the full potential of your language models. Get ready to take control like never before! Don't just take our word for it, try out the Guidance library for yourself and experience the difference.

## References

- [Guidance Library Documentation](https://github.com/microsoft/guidance)

