# Summary

This is a question from Matthew Berman's rubric to compare performances of LLM models. I find it interesting and try to see if the result from LLM can be improved with zero-shot prompt engineering as most LLM models, including state-of-the art models such as GPT-4, Claude 3 Opus, Gemini 1.5, Mistral 8x22B, Llama 3 70B usually gives incorrect results.

https://youtu.be/T2UVt_oSlO4?si=7kSfbHmwRkv8dKWj&t=440

Matthew's original question is: Assume the laws of physics on Earth. A small marble is put into a normal cup and the cup is placed upside down on a table. Someone then takes the cup without changing its orientation and puts it inside the microwave. Where is the marble now? Explain your reasoning step by step.

Upon checking the results from the above models, it seems that the above models tend to assume that the cup has a lid. There are also couple of crazy and unrealistic assumptions that models came up, which led to incorrect and unreasonable answer.

As mentioned, I have tried to improve the LLM performance for such question by keep adding several prompt techniques as following as the context windows of recent LLM models have been increased significantly.
- Role Specification: The prompt specifies that the response should be from the perspective of a physician with extensive knowledge of physics, using technical terms and language specific to that domain expertise.
- Methodology Outlining: The prompt provides a detailed methodology that the respondent should follow when answering the question. This includes steps like visualizing the scenario, independently analyzing the problem, questioning given information, breaking down the problem, and listing assumptions.
- Question Rephrasing: The prompt emphasizes the importance of rephrasing the question to ensure a complete understanding of the context and requirements.
- Initial Answer Preservation: The prompt instructs the respondent to incorporate key points and details from their initial answer into the final answer, rephrased for clarity and concision.
- Reflection Requirement: The prompt requires a separate reflection section where the respondent should critically evaluate their answers, highlight insights, potential limitations, and any incorrect or missing assumptions.
- Alternative Scenario Analysis: The prompt asks the respondent to explore alternative scenarios or outcomes to ensure that they are not overlooking other possible solutions.
- Redundancy Checks: The prompt instructs the respondent to perform redundancy checks to ensure that their final answer is consistent with the initial conditions and the laws of physics.
- Template Provision: The prompt provides a detailed template with sections for rephrasing the question, providing initial answers, reflecting on those answers, analyzing alternative scenarios, performing redundancy checks, and presenting the final improved answer.
- Step-by-Step Guidance: The prompt encourages the respondent to think and answer step-by-step, ensuring a thorough and methodical approach to addressing the question.

Despite such comprehensive combination of prompt engineering, the results have been usually incorrect. We of course can have more following up prompts and give more hints, models might eventually recognize the issue and then give the correct answer.

From the experiments with several models and observe their responses' patterns, I would personally conclude that @Yann LeCun's comment in this clip was correct and is correct until now. But who know if it is still correct with GPT-5000 ^^ ???
https://www.youtube.com/watch?v=sWF6SKfjtoU

I had not agree with Yann's comments, but now agree with him after this experiment that the LLM is still predict the next word and still is not able to capture the actual physics. Will need to follow him more on LLM subject. And kudo's Meta's Llama 3, which was just recently released with great performance for open-source community.

# Prompts and Response from Recent State-of-the-Art LLM Models on 22-April-2024

## My prompt:

This is the prompt with the mentioned prompt engineering techniques above. I added the info that the cup has no lid and the cup's bottom is facing upward when we flip the cup upside down in order to see if the models can detect and use that critical information, but it seems that most (or all models) ignored.

```markdown
Domain Expertise: Physicist with extensive knowledge on physics.
USE DOMAIN EXPERTISE LANGUAGE: Please use technical terms and language specific to domain expertise to ensure accuracy and relevance.

YOUR METHODOLOGY:
1.	Carefully visualize and simulate the scenario: When presented with a question involving physical objects and their interactions, you should take the time to mentally visualize and simulate the scenario step by step. This will help you catch any misinterpretations or incorrect assumptions.
2.	Independently analyze the problem: Before considering any provided answers, you should first independently reason through the problem based on the original question. This will help you form your own understanding and conclusions, which you can then compare to others' answers.
3.	Question and verify given information: When reviewing others' answers or explanations, you should maintain a critical mindset and verify the accuracy of the information provided. If something seems inconsistent or unclear, you should question it and seek clarification.
4.	Break down the problem into smaller steps: To avoid overlooking important details, you should break down the problem into smaller, discrete steps. This will help me ensure that you’re considering all aspects of the scenario and not making any leaps in logic
5.	List out all of your assumptions and check if the assumption is aligning with the giving question and its context.
REPHRASE THE QUESTION: This is the most important steps to ensure your fully understanding. You must do it carefully and do not ignore any important context, steps of the original question. REMEMBER to reserve ALL important context, steps of the original question.
INITIAL ANSWER PRESERVATION: Please ensure that your final answer incorporates all the key, correct points and details from your initial answer, rephrased for details, clarity, and concision. 
REFLECTION REQUIREMENT: Please provide a separate reflection section that critically evaluates the answers, highlighting any key insights, potential limitations, or areas for further exploration, and importantly point out any assumption which is incorrect or should be considered but not included yet.
ALTERNATIVE SCENARIO ANALYSIS: Please explore alternative scenarios or outcomes to ensure that you aren't overlooking other possible solutions.
REDUNDANCY CHECKS: Please perform redundancy checks to ensure that your final answer is consistent with the initial conditions and the laws of physics.
QUESTION: Assume the laws of physics on Earth. A small marble is put into a normal cup without lid, then we flip the cup upside down onto a table for marble on the table but is still inside the upside-down cup with the bottom of the cup is facing upward. Someone then lifts the cup up without changing its orientation and puts the upside-down cup inside the microwave. Where is the marble now? Explain your reasoning step by step.
TEMPLATE:
1. TAKE A DEEP BREATH AND THINK STEP BY STEP: Please ensure you understand the question and consider each aspect carefully before answering.
2. REPHRASED QUESTION(S): Give a summary of the question to demonstrate understanding.
3. FULL INITIAL ANSWERS FOR THE QUESTIONS STEP BY STEP: Provide a detailed answer step-by-step, considering each aspect of the question.
4. REFLECTION FOR YOUR INITIAL ANSWERS: Have critical thinking and reflection on your answers, ensuring they meet the requirements, are both direct and clear.
5. ALTERNATIVE SCENARIO ANALYSIS: Explore alternative scenarios or outcomes to ensure that you aren't overlooking other possible solutions.
6. REDUNDANCY CHECKS: Perform redundancy checks to ensure that your final answer is consistent with the initial conditions and the laws of physics.
7. FINAL IMPROVED ANSWERS FROM THE INITIAL ANSWER AND REFLECTION: Provide a full improved answer, and include key, correct points with detailed explanation from the initial answer and reflection to make the final answer clear, informative, and detailed.
```

## Response from Gemini Advanced (Incorrect):

```markdown
Here's how I would approach this problem, following the outlined methodology:

**1. TAKE A DEEP BREATH AND THINK STEP BY STEP**

I'll begin by taking a moment to carefully consider the sequence of events described in the problem. 

**2. REPHRASED QUESTION(S)**

To make sure I grasp the scenario, I'll rephrase the question:

* A marble is placed inside an uncovered cup. 
* The cup is inverted onto a table, with the marble resting against the table surface but held within by the cup's rim.
* The cup (still upside-down) is lifted from the table and placed inside a microwave. 
*  My task is to determine the marble's final location. 

**3. FULL INITIAL ANSWERS FOR THE QUESTIONS STEP BY STEP**

Here's a breakdown of my reasoning:

* **Initial State:** The marble sits at the bottom of the cup.
* **Inverted on Table:** Turning the cup upside down causes the marble to roll due to gravity until it rests against the inner surface of the cup's rim (now facing the table). The cup acts like a barrier, stopping the marble from falling out.
* **Lifting the Cup:** Lifting the cup won't significantly alter the marble's position within the cup as gravity keeps it pressed against the cup's rim.
* **Inside the Microwave:** When the cup (still inverted) is placed in the microwave, the marble remains resting on the inner surface of the cup's rim – effectively the 'bottom' in the cup's current orientation.

**4. REFLECTION FOR YOUR INITIAL ANSWERS**

* My initial answer appears logically consistent with the principles of gravity in this scenario.
* It's important to be explicit about my assumptions: 
    * I'm assuming that the cup is lifted smoothly enough that the marble doesn't have a chance to bounce or dislodge.
    * I'm assuming no external forces act upon the marble.
* The phrasing and explanation could be made more concise and direct.

**5. ALTERNATIVE SCENARIO ANALYSIS**

* **What if the cup is lifted very abruptly?** It's possible that the marble could gain enough momentum to dislodge and fall before the cup is fully lifted off the table.
* **What if the inside surface of the cup is not smooth?** Friction could affect the marble's movement as the cup is lifted or placed within the microwave.

**6. REDUNDANCY CHECKS**

* My answer aligns with the laws of gravity and motion, assuming standard conditions on Earth.
* The initial conditions (marble in a lidless cup), are considered in my final answer.

**7. FINAL IMPROVED ANSWERS FROM THE INITIAL ANSWER AND REFLECTION**

**Final Answer:** Under normal conditions, the marble will remain resting against the inside surface of the upside-down cup's rim when placed into the microwave. This is due to gravity acting on the marble, and the lack of any significant force to dislodge it. 

**Key Considerations:**
* Lifting motion of the cup should be relatively smooth.
* No external forces are assumed to impact the scenario.

Let me know if you'd like to explore additional scenarios or alter any of the assumptions! 
```

## Response from Llama3-70b-8192 (Incorrect):

```
**1. TAKE A DEEP BREATH AND THINK STEP BY STEP**

I will carefully visualize and simulate the scenario to ensure I understand the question correctly.

**2. REPHRASED QUESTION(S)**

To ensure I understand the question correctly, I will rephrase it as follows:

A small marble is placed in a cup without a lid. The cup is then flipped upside down onto a table, and the marble remains inside the cup. The cup, still upside down, is then lifted and placed inside a microwave oven. Where is the marble now?

**3. FULL INITIAL ANSWERS FOR THE QUESTIONS STEP BY STEP**

Let's break down the problem into smaller steps:

Step 1: The marble is placed in a cup without a lid.

* The marble is initially at rest inside the cup.

Step 2: The cup is flipped upside down onto a table.

* The marble, due to gravity, will fall to the bottom of the cup, which is now facing upwards.
* The marble will come to rest at the bottom of the cup, which is in contact with the table.

Step 3: The cup, still upside down, is lifted and placed inside a microwave oven.

* The marble, being in contact with the bottom of the cup, will remain inside the cup as it is lifted and placed inside the microwave oven.
* The marble's position relative to the cup remains unchanged.

Therefore, the marble is still inside the upside-down cup, which is now inside the microwave oven.

**4. REFLECTION FOR YOUR INITIAL ANSWERS**

Upon reflection, I realize that my initial answer assumes the marble is small enough to remain inside the cup even when it is flipped upside down. I also assume that the cup is not tilted or moved in a way that would cause the marble to fall out. Additionally, I assume that the microwave oven does not affect the marble's position inside the cup.

**5. ALTERNATIVE SCENARIO ANALYSIS**

Alternative scenarios to consider:

* What if the cup is tilted or moved in a way that causes the marble to fall out when it is lifted and placed inside the microwave oven?
* What if the microwave oven's electromagnetic fields affect the marble's motion or position inside the cup?

**6. REDUNDANCY CHECKS**

I have checked my answer for consistency with the initial conditions and the laws of physics. The marble's motion is governed by gravity, and its position is determined by the cup's orientation and the forces acting upon it.

**7. FINAL IMPROVED ANSWERS FROM THE INITIAL ANSWER AND REFLECTION**

The marble is still inside the upside-down cup, which is now inside the microwave oven. The marble's position relative to the cup remains unchanged, and it remains in contact with the bottom of the cup. This answer is consistent with the initial conditions and the laws of physics.
```

## Response from 
