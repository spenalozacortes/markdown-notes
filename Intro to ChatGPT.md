# Introduction to ChatGPT
## Introduction to ChatGPT

### What is ChatGPT?
ChatGPT is a **large language model** created by the company OpenAI. A large language model aims to understand and respond to text by training on a massive amount of data, typically millions or even billions of words. This training is part of a process called **machine learning**.

Machine learning enables computers to learn and improve their performance on a task over time. Machine learning is an umbrella term for a set of algorithms that analyze and find patterns from known historical information (“training data”) to make predictions on unknown/new information. Machine learning involves:

- Feeding data into an algorithm.
- Allowing the algorithm to “learn” from that data.
- Using that learning to make predictions or decisions about new data.

ChatGPT was built using a more complex form of machine learning called **deep learning**. Deep learning attempts to replicate the way the human brain works, learning and improving over time. The more data the model is trained on, the better it can learn these patterns and make accurate predictions.

The amount of data ChatGPT was trained on is massive, consisting of hundreds of billions of words. The dataset includes sources from:

- Websites
- Books
- Articles
- Social media posts
- News articles
- And more!

Through processing all of this data, ChatGPT has “_learned_” the way information tends to be presented, using this to string together text. It predicts how a human would respond to a question, a word, or group of words, at a time.

### Capabilities of ChatGPT

Through its ability to generate useful responses to questions in seconds, ChatGPT has a wide range of potential applications across various industries:

- Provide personalized customer service
- Assist with language translation and coding tasks
- Generate content for websites or social media
- Create chatbots and virtual assistants
- Analyze and summarize large amounts of text data


# Introduction to Generative AI
## Introduction to Generative AI

### Introduction
Generative AI refers to a type of artificial intelligence that is capable of creating new content based on its understanding of patterns and relationships in the data it has been trained on. It can generate content that resembles human-created work, making it a powerful tool for a wide range of applications.

In the case of ChatGPT, generative AI is used to create text-based responses to user input.

### Training Data
Generative AI is amazing at “learning”. AI doesn’t learn the same way humans do; it analyzes data and creates connections using math. The connections it makes depend on the sort of data the AI is given. Is it good data? Is it enough data? In order to create connections, it needs lots of good-quality data.

We call this data **training data**. Training data can be anything from text to images to websites! It depends what sort of final output we finally want our AI to create. The more diverse and high-quality the training data, the better our AI will become at understanding and creating new content.

### Encoding Training Data
To make sense of the training data, we need to translate it into a form that the AI can understand. This process is called **encoding**. We transform text, images, or other data into a series of vectors that the AI can process. These vectors are essentially lists upon lists of numbers.

### Creating a Probability Distribution
During **training**, the AI looks at the encoded data and learns the underlying structure of the data to be able to generate coherent data. For instance in the case of text-based models, the training phase involves learning about word associations and co-occurrence patterns. The AI calculates the likelihood of different outcomes to create a **probability distribution**.

The AI starts doing math to calculate, “What is the probability of `A` occurring given `B` has already occurred?” This is commonly represented by mathematical symbols like:

`P(A|B)`

Depending on the type of task the algorithm needs to perform, the AI might start doing more complex math and asking more complex questions. It might start calculating, “What is the probability of `A` occurring given `B`, `C`, and `D` have already occurred?”

The probability distribution provides a complete description of the probabilities of all possible occurrences and keeps track of the relative likelihoods of each possible outcome.

The probability distribution helps the AI generate new content by choosing the most likely options.

### Extra Learning and Filtering
AI can also be trained and “learn” in other ways. AI can benefit from feedback and unsupervised learning.

Initial versions of ChatGPT used **reinforcement learning** and **human feedback** to do additional training. Reinforcement learning is a method that involves a rubric that “rewards” or “penalizes” the algorithm depending on the correctness of the guess. By iterative training, the AI will eventually learn to generate the correct output for the relevant task. Sometimes, a human in the loop is needed to test the outputs too. Many of these models involve human feedback to make sure the content generated is coherent and free of errors.

It might also be necessary to remove harmful or incorrect connections the AI built from training data. It’s possible that the training data had harmful biases, incorrect data, or other issues. Humans can flag these issues and try to remove these associations so they don’t show up in the AI’s eventual output.

After enough human intervention, they might feel comfortable relying more on **unsupervised learning**. This allows the AI to create more connections on its own without human intervention. Later versions of GPT used this method.

### User Input
To generate content, ChatGPT needs our input. Once we provide a prompt or question, ChatGPT encodes our input just like it did with the training data.

This helps ChatGPT understand our request and generate a suitable response.

### Generating Content
With your input encoded, ChatGPT uses the powerful GPT-# architecture to generate content.

ChatGPT uses the knowledge it has gained from its training data to generate a response. It achieves this by predicting the most likely sequences of words, phrases, or sentences that would form a suitable reply. ChatGPT bases this on the patterns and relationships it has learned from the vast amount of text data it has been trained on.

Sometimes, ChatGPT might NOT form a suitable reply. Sometimes Generative AI can **hallucinate**, i.e, generate new but inaccurate content.

This can happen for a few reasons:

1. Ambiguity in the input: If the user input is vague or unclear, ChatGPT might struggle to generate a relevant response, causing it to create content that appears to be a hallucination.
2. Lack of specific knowledge: If ChatGPT hasn’t encountered enough relevant information about a specific topic, it might fill in gaps with incorrect or unrelated details.
3. Limitations of the model: Although GPT-# is a powerful AI model, it’s not perfect. It may not always generate accurate, factually correct, or contextually appropriate responses, leading to hallucinations in some cases.

ChatGPT is a powerful tool, but it’s important to remember that even it can make mistakes! We should always double-check any data it gives us.

### Decoding and Outputting Content
Once the generative model generates content, we need to transform it back into something the user can understand. This process is called **decoding**. The AI takes the encoded vectors and converts them into text, images, or other forms of output.

To the user, this whole process happens very quickly. This is because the generative model is created ahead of time, so the user only has to wait for:

1. Their input to be encoded
2. Content to be generated from an existing model
3. The output to be decoded and sent

### Review
1. Collect Training Data
2. Encode Training Data
3. Train and Create a Probability Distribution
4. Extra Learning & Filtering: Reinforcement Learning or Unsupervised Learning
5. Collect and Encode User Input
6. Generate Content
7. Decode and Output Generated Content


# Using ChatGPT in Everyday Life
## Using ChatGPT in Everyday Life

### ChatGPT for Answering Questions
ChatGPT has been known to sometimes produce inaccurate information. _ChatGPT should not be treated as an authority on a subject!_ Some of its errors can be difficult to notice because they are hidden in reasonable-sounding responses. Just because the answer sounds good doesn’t mean it’s correct! ChatGPT is a good place to start, but probably shouldn’t be where you end your research.

### ChatGPT for Summarizing Text
ChatGPT has the ability to “remember” previous prompts from the conversation. Once the text has been entered, we can ask follow-up questions.

### ChatGPT for Writing
One of the most valuable benefits of ChatGPT is its ability to provide feedback on written content. By submitting their work to the model, writers can receive suggestions and advice on how to improve their writing, such as identifying repetitive phrases or clunky sentence structures.

In addition to feedback, ChatGPT can also provide writers with prompts and inspiration to help them get started or overcome writer’s block. By inputting a topic or theme, the model can generate a range of ideas and starting points to kickstart the writing process.


# Ethics and AI
## Ethics and AI

### Introduction
1. Ethics of replacing human labor with automation
    
    Is it ethical to replace humans with AI? Is it _sometimes_ ethical to replace humans with AI? This is important in the context of jobs like customer service and content creation jobs.
    
2. Buying or selling AI-generated content
    
    Art, writing, music, and films all fall under content created in this category.
    
3. Using AI for decision-making.
    
    Can we trust AI to make good and accurate decisions? Examples of this include resume screening and risk assessment algorithms (eg TSA clearance, applications for benefits, risk assessment tools used by the police, etc).
    
4. Ethics of using autonomous machines
    
    This includes more than just autonomous driving and drones. This also includes facial recognition kiosks at airports or credit card machines.

### Automation
Automation, the process of replacing human labor with machines or software, has been around for centuries. The first spinning mill, replacing a part of the yarn-making process done by hand for thousands of years, was introduced in the late 1700s.

Over the last several centuries, machines have replaced millions of jobs traditionally done by people. Some of these machines are programmed, and many follow simple procedures, repeating one or several parts of a process.

In more recent years, AI is becoming powerful enough to be integrated into machines that do work. Consider some of the following modern uses of AI:

- Manufacturing: Inspecting goods for quality control, predicting when equipment will begin to fail
- Logistics: Optimizing delivery routes, supply chain management
- Customer Service: Answering common questions and resolving simple issues
- Healthcare: Image analysis and diagnosis

In many cases, AI has been found to do them faster, cheaper, and more accurately than a person. However, in each case, AI is replacing a part of the work done by people and sometimes replacing people’s jobs altogether. Is this tradeoff acceptable?

Consider the following scenario:

> A large shipping company spends millions of dollars on a complex AI-powered logistics system. It is able to route each piece of the shipping process more effectively, reducing shipping times by a third. Human drivers and operators on the new routes are expected to follow the routes exactly, in the time predicted, or face disciplinary action. The company is able to let go of hundreds of full-time logistic experts and hires more engineers to continue to build new tech. Outperforming their competition, the new process causes dozens of small competitors to go out of business. These programs make the company the leader in its space.

Proponents of automation argue this is all a part of doing business and possibly beneficial to those involved. People displaced from jobs might receive training and be placed in different positions! (Unfortunately, this is often not the case.) Customers might receive benefits such as lower prices, lower wait times, or other improved outcomes.

Others might say that the use of proprietary AI systems is an unfair advantage. How is a small business supposed to compete and create its own system? Automation may lead to a loss of human skills and knowledge. As machines and software take over more tasks, fewer humans can perform these tasks, resulting in a loss of expertise and knowledge that is difficult to regain.

The use of AI and automation in business is a complex topic that has caused debate for hundreds of years. It has the potential to displace hundreds of millions of jobs but has also historically caused huge advancements in the way we, or at least some of us, live. Whether it is worth it or not is often left up to the individual to decide.

### Resume Screening and Discrimination
People tend to have biases that impact the decisions they make. With a machine in charge, will all decisions be fair?

Unfortunately, AI systems are subject to many of the same biases that humans are. The primary issue is that AIs are trained and programmed by biased humans.

AI will perpetuate bias and discrimination when the data used to train the algorithms is not diverse and representative of the population as a whole.

These biases can be difficult to detect because the AI systems do not explain their decision-making process, and they simply assign a score. This raises questions about how to ensure that AI systems are transparent and explainable, and how to ensure that they are not perpetuating bias and discrimination.

_Creating AIs that avoid bias is an unsolved and difficult problem_. Many of our datasets, such as the internet and literature, contain many harmful biases when broad patterns are applied to groups of people. Researchers continue to find ways to try and account for bias through practices such as using diverse datasets and thorough testing.

### Autonomous Driving
The first issue is accountability: when something goes wrong in an autonomous system and someone gets hurt, who is held accountable? Autonomous cars rely on machine learning algorithms to make decisions and operate on the road. However, in the event of an accident, it can be difficult to assign responsibility to the car or its manufacturer. Do laws punishing dangerous drivers still apply to an artificial system?

Those who drive for a living will also be affected by autonomous cars. Truck drivers, delivery drivers, taxi drivers, and more could see their careers disrupted by the use of autonomous vehicles. Like other forms of automation, self-driving cars could eliminate jobs and make smaller companies unable to compete.

Autonomous cars also raise concerns about privacy. Autonomous cars generate large amounts of data, including location data, driving behavior, and personal information about passengers. It is important to ensure that this data is collected, used, and shared in an ethical and responsible manner.

### Autonomous Weapons
Autonomous weapons use artificial intelligence to identify and engage targets without human control. Drones in combat today typically have a remote pilot controlling it. An autonomous version of this would have no human pilot, controlled solely by the AI. Completely autonomous weapons are in development but not confirmed to be in use yet (though there have been reports of their use).

Supporters of AI-powered weapon systems feel that they will be able to more accurately identify and kill a combatant than a human. They believe the use of these weapons could actually lower casualties of war.

However, having completely AI-controlled weapons is deeply controversial due to issues such as:

- Legality
- Accountability
- Safety

Who is accountable when an autonomous weapon makes a mistake and kills a civilian? Is it the company, the government, or the engineer who wrote the code? Without a person making the decision to fire, accountability becomes more complicated. Who should be held responsible, and what should the consequences be?

It’s important to remember that AI aren’t human, and they make decisions based on their code and training - it can be difficult for them to understand nuance, human emotion, and international relations. It’s difficult to create laws to protect us from the dangers of AI.

### Review
1. Ethics of replacing human labor with automation: _Is it ethical to replace humans with AI?_
2. Buying or selling AI-generated content: _Is it ethical to buy or sell AI-generated content trained on works created by humans?_
3. Using AI for decision-making: _Can we trust AI to make ethical and accurate decisions?_
4. Ethics of using autonomous machines: _Can we trust AI machines to safely replace humans?_

A big unanswered question in AI is: If things go wrong, who do we hold responsible? The user? The creator? The AI itself?


# Risks and Limitations of ChatGPT
## Risks and Limitations of ChatGPT

### Introduction
Though ChatGPT has been trained on massive quantities of data, it is far from perfect. It does not truly think about the words it is producing because it’s a trained language model, not a person. While people have the ability to judge and think about what words we write, ChatGPT merely follows its language model.

Misinformation, offensive content, and data breaches are serious threats to people relying on ChatGPT for content.

### ChatGPT and Misinformation
While ChatGPT can be a valuable tool for answering questions and generating text, it also has the potential to spread **misinformation**, things that aren’t true. ChatGPT does not always provide accurate or truthful responses to certain prompts.

While the internet houses much of the world’s information, _not all of that information is true_. A language model learning from internet data can quickly pick up inaccuracies, and due to the vast amount of information that is out there, it is not easy to correct all of the false information that ChatGPT “learned”. Any information coming from ChatGPT should be verified before being relied on.

Remember, ChatGPT doesn’t actually understand the information it is writing! ChatGPT isn’t able to understand the nuances of discussions, debates, or even the meaning of words and phrases. It generates the next word it thinks is the most likely to appear after what it has written so far. It does not understand whether the text it is generating is “true”.

While some of ChatGPT’s content may be incorrect due to incorrect training data, sometimes AI will literally _make up information_. The tendency for large language models like ChatGPT to confidently assert false information in this way is known as **hallucination**. These made-up statements often occur when ChatGPT is asked to produce very specific information. Lacking nuanced knowledge, it simply produces a response that it deems likely to occur next, regardless of whether that response makes sense.

### ChatGPT and Disinformation
ChatGPT can sometimes produce wrong information on its own, but it can also be used to produce false information on purpose.

ChatGPT’s ability to quickly produce information makes it a prime target for creating **disinformation** intended to mislead people. There are people who might intentionally try to get ChatGPT to produce propaganda to support their own causes. Using ChatGPT, people are able to quickly produce massive amounts of information and put it onto the internet. Consider people using ChatGPT to:

- Create many fraudulent positive or negative reviews
- Write many different articles all repeating the same false narrative
- Post many variants of the same comments on people’s videos

By placing overwhelming amounts of content all saying the same thing, people using ChatGPT have the chance to control the narrative around topics of their choosing. Fraudulent content produced by ChatGPT would outpace true content produced by real people.

They can take advantage of people who may believe that ChatGPT is smarter than people because, after all, ChatGPT knows the whole internet.

Researchers are trying to correct these problems within ChatGPT. Over time, ChatGPT has been programmed to limit its ability to generate false or misleading information. However, this remains an unsolved problem.

### ChatGPT and Bias
There are many situations in which these biases can show in ChatGPT responses. Asking ChatGPT to produce descriptions of people in certain fields, or with certain traits can result in stereotypical responses. Many people have found different ways to get ChatGPT to produce biased responses towards certain demographics, including racist, sexist, and bigoted statements.

### ChatGPT and Data Security
As people use ChatGPT, it collects information from the prompts being used and the people that write them. Where is this data going, how is it being used, and is it secure?

### Review
- **Misinformation**: The tendency for ChatGPT to produce incorrect information
- **Disinformation**: The ability for ChatGPT to be used to produce information intended to mislead people
- **Bias**: ChatGPT presenting biases based on the training data it has received
- **Data Security**: The security and privacy issues stemming from the data ChatGPT is collecting


# Prompt Engineering with ChatGPT
## Prompt Engineering with ChatGPT

### Introduction
The tips discussed in this lesson include:

- Use **clear** language
- Define the **purpose** of the prompt
- Include important **context**
- Provide **examples**

### Use Clear Language
When writing a prompt for ChatGPT, aim for a **specific** and **simple** prompt that is **free from spelling and grammatical errors**. While being specific increases the size of the prompt, we should get rid of unnecessary information, jargon, confusing phrases, or mistakes, any of which can lead the AI down the wrong path.

For example, instead of:

`My team is interested in X, tell me about that`

Consider:

`Provide a summary of X, including its history, features, and configuration.`

### Every Prompt has a Purpose
Think about factors like:

- **Tone**: How do you want the output to sound? Funny? Professional?
- **Format**: How do you want the output structured? Bullet list? Paragraph? An essay?
- **Audience**: Who is this for? Do you want something for children? Beginners? Experts?

Consider a prompt like the following:

`Write about artificial intelligence`

As opposed to:

`Write structure for a brief presentation on the use of artificial intelligence for a manufacturing business. The tone should be professional and aimed at business executives.`

### Include Important Context
Include any details that are essential to understanding your request, such as historical context or related concepts.

Instead of:

```
My code is throwing an error
```

Consider:

```
This line of code: 
X 

Is throwing the exception 

Y
```

If there are specific limitations or requirements, make them clear in your prompt. While context is important, avoid providing too much information, as it may confuse the AI or cause it to focus on less important aspects of your request.

For example, instead of:

```
Explain how to use a computer program
```

Using our previous strategies, we’d have:

```
Explain how to use a photo editing software, such as Adobe Photoshop, for beginners who have never worked with image editing tools. 
```

Using our new tips, we’d add:

```
Focus on basic functions like cropping, resizing, and adjusting color levels.
```

### Provide Examples
Adding examples to your prompt can clarify what you mean and give the AI a baseline to work off of. If there are some similar examples to what you are looking for, provide them.

Consider a prompt like:

```
Create three quiz questions for my workshop on Networking using gRPC. The audience for the workshop will be junior engineers in a business setting. Questions should be at a high level and not involve implementation details. I want questions similar to: 

X
Y
Z 
```

### Review
- Use **clear** language: Get rid of unnecessary information, jargon, confusing phrases, or mistakes.
- Define the **purpose** of the prompt using concepts like:
    - **Tone**: How do you want the output to sound? Funny? Professional?
    - **Format**: How do you want the output structured? Bullet list? Paragraph? An essay?
    - **Audience**: Who is this for? Do you want something for children? Beginners? Experts?
- Include important **context**: If there are specific limitations or requirements, make them clear in your prompt.
- Provide **examples**




