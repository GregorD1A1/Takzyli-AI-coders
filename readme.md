# Clean Coder AI framework

Clean Coder is an AI code writer developed with special attention to providing a clean context to Large Language Models (LLMs). This enhances the quality of LLM responses and reduces costs.

Work of a programmer is often about making minor alterations to existing applications and expanding their capabilities, rather than building a whole new app from scratch. Unlike other AI coding frameworks, Clean Coder specializes in implementing changes within existing applications.

# How to work with Clean Coder

## Setup

Change name of '.env.template' file to '.env' and open it with text editor. Provide your OpenAI api key and path to project directory you will be working on.

## Working process

Check out the demonstration video:

<iframe width="560" height="315" src="https://youtu.be/d5qbX-v4qwM" frameborder="0" allowfullscreen></iframe>

1. Define Task

In 'clean_coder_pipeline.py', modify the task variable. Describe your task in detail. It is advisable to provide "unit" tasks - smaller ones and run the program multiple times rather than asking it to perform a complex task all at once. Specify which files to edit and, if creating a frontend, which design templates to use.

2. Researcher Agent

Launch the app. The first agent to begin work is the Researcher - its job is to examine files in the project directory and identify only the necessary files to work on. Additionally, it can locate image graphics as templates for frontend coding (you need to store designs somewhere in the project dir.).

Once the research is complete, the Researcher will display the suggested files to work on. Type 'ok' and press enter if you agree with his research or provide your feedback if you want it to add/remove some files.

3. Planner Agent

The Planner is the most responsible agent - it drafts the plan for code modifications. It's recommended to thoroughly review the plan it proposes and request it to make changes until the plan it outputs is satisfactory. Then, type 'ok' to proceed to the executor. Only the last planner message is provided to the executor, so ensure that it provides the complete plan in it.

4. Executor Agent

This is where the actual magic happens. The Executor will implement the planned changes to your project files. It will call tools in sequence, which will either modify files or create new ones. For tools that interact with the project, a safety mechanism is introduced - you need to confirm the tool execution by pressing enter. It's recommended to first check what change it intends to make and provide feedback if you think it might break something. After all changes are implemented, it will check the log file (if you set it up) and make further changes if there are issues with the logs. Next, it will ask you to confirm if everything is done as intended - provide feedback if you want it to improve something or type 'ok' to end the pipeline.