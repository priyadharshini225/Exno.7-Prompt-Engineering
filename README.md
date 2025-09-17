# Exno.7-Prompt-Engineering
# Date: 17/09/25
# Register no: 212223240129
# Aim: 
To Develop a prompt-based application tailored to their personal needs, fostering creativity and practical problem-solving skills while leveraging the capabilities of large language models.



# Algorithm: 
Develop a prompt-based application using ChatGPT - To demonstrate how to create a prompt-based application to organize daily tasks, showing the progression from simple to more advanced prompt designs and their corresponding outputs.
# Procedure / Algorithm

Step 1: Define the Use Case

Use Case: Daily Agenda Optimization.

Whenever scheduled tasks are canceled, the AI should reorganize the agenda and suggest:

New task order for efficiency

Urgent priorities

Opportunities for rest or productive fillers

Step 2: Set Up AI API Access

```python
import os
import openai

OPENAI_API_KEY = os.getenv("OPENAI_API_KEY")
```
Step 3: Write a Function to Prompt the AI

```python
def optimize_schedule(remaining_tasks, canceled_tasks):
    openai.api_key = OPENAI_API_KEY
    
    prompt = f"""
    I had a couple of scheduled tasks canceled today. 
    Here are my remaining tasks: {remaining_tasks}. 
    The following tasks were canceled: {canceled_tasks}. 
    
    Please reorganize my day to optimize time and energy. Consider:
    1. Adjusting task order for efficiency
    2. Highlighting urgent priorities
    3. Suggesting breaks/rest
    4. Recommending new productive tasks if possible
    Return the updated schedule in a clear, time-blocked format.
    """
    
    response = openai.ChatCompletion.create(
        model="gpt-4",
        messages=[{"role": "user", "content": prompt}]
    )
    return response['choices'][0]['message']['content']

```
Step 4: Provide Sample Input
```python
remaining = [
    "Finish SQL assignment (due tomorrow, ~2 hrs)",
    "Team call (3:00–3:30 PM)",
    "Gym workout (~1 hr)",
    "Revise notes for exam (~1.5 hrs)"
]

canceled = [
    "12:00–1:00 PM client meeting",
    "5:00–6:00 PM project review"
]

print(optimize_schedule(remaining, canceled))
```
Step 5: Sample Output (AI Response)

Updated Agenda:
12:00–12:30 → Quick lunch + relaxation
12:30–2:30 → SQL assignment (priority: deadline tomorrow)
3:00–3:30 → Team call (fixed)
3:30–4:30 → Exam revision (fresh focus after call)
4:30–5:30 → Gym workout (energy boost)
5:30–6:00 → Review SQL briefly / check emails

# Observation Table:

| **Input (Remaining Tasks)**                                                                                                                    | **Input (Canceled Tasks)**                                      | **AI Generated Optimized Schedule**                                                                                                                                                                                                         |
| ---------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| - Finish SQL assignment (due tomorrow, \~2 hrs)<br>- Team call (3:00–3:30 PM)<br>- Gym workout (\~1 hr)<br>- Revise notes for exam (\~1.5 hrs) | - 12:00–1:00 PM client meeting<br>- 5:00–6:00 PM project review | - 12:00–12:30 → Quick lunch + relaxation<br>- 12:30–2:30 → SQL assignment (priority: deadline tomorrow)<br>- 3:00–3:30 → Team call (fixed)<br>- 3:30–4:30 → Exam revision<br>- 4:30–5:30 → Gym workout<br>- 5:30–6:00 → Review SQL / emails |



# Result: 
The Python code successfully:

Accepted input of remaining and canceled tasks.

Connected with AI to reorganize the schedule.

Generated an optimized, time-blocked daily agenda.

Suggested both productive use of time and opportunities for rest.
The Prompt is executed successfully


