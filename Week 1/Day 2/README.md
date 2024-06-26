---
title: BeyondChatGPT Demo
emoji: 📉
colorFrom: pink
colorTo: yellow
sdk: docker
pinned: false
app_port: 7860
---

# 🏗️ Build 

> If you need an introduction to `git`, or information on how to set up API keys for the tools we'll be using in this repository - check out our [Interactive Dev Environment for LLM Development](https://github.com/AI-Maker-Space/Interactive-Dev-Environment-for-LLM-Development/tree/main) which has everything you'd need to get started in this repository!

In this repository, we'll walk you through the steps to create a Large Language Model (LLM) application using Chainlit, then containerize it using Docker, and finally deploy it on Huggingface Spaces.

- 🤝 Breakout Room #1:
  1. Getting Started
  2. Setting Environment Variables
  3. Using the OpenAI Python Library
  4. Prompt Engineering Principles
  5. Testing Your Prompt

Complete the notebook in this repository, or head to [this notebook](https://colab.research.google.com/drive/1ol4Q9u-L5SZJdDlFYGWsq1JWJ-LFKc5u?usp=sharing) and follow along with the instructions!


- 🤝 Breakout Room #2:
  1. 🏗️ Building Your First LLM App
  3. 🐳 Containerizing our App
  4. 🚀 Deploying Your First LLM App

<details>
  <summary>🏗️ Building Your First LLM App</summary>

1. Clone [this](https://github.com/AI-Maker-Space/Beyond-ChatGPT/tree/main) repo.

     ``` bash
     git clone https://github.com/AI-Maker-Space/Beyond-ChatGPT.git
     ```

2. Navigate inside this repo
     ``` bash
     cd Beyond-ChatGPT
     ```

3. Install the packages required for this python envirnoment in `requirements.txt`.
     ``` bash
     pip install -r requirements.txt
     ``` 

4. Open your `.env` file. Replace the `###` in your `.env` file with your OpenAI Key and save the file.
     ``` bash
     OPENAI_API_KEY=sk-###
     ```

5. Let's try deploying it locally. Make sure you're in the python environment where you installed Chainlit and OpenAI. Run the app using Chainlit. This may take a minute to run.
     ``` bash
     chainlit run app.py -w
     ```

<p align = "center" draggable=”false”>
<img src="https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/54bcccf9-12e2-4cef-ab53-585c1e2b0fb5"> 
</p>

Great work! Let's see if we can interact with our chatbot.

<p align = "center" draggable=”false”>
<img src="https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/854e4435-1dee-438a-9146-7174b39f7c61"> 
</p> 

Awesome! Time to throw it into a docker container and prepare it for shipping!
</details>



<details>
  <summary>🐳 Containerizing our App</summary>

1. Let's build the Docker image. We'll tag our image as `llm-app` using the `-t` parameter. The `.` at the end means we want all of the files in our current directory to be added to our image.
     
     ``` bash
     docker build -t llm-app .
     ```

2. Run and test the Docker image locally using the `run` command. The `-p`parameter connects our **host port #** to the left of the `:` to our **container port #** on the right.
    
     ``` bash
     docker run -p 7860:7860 llm-app
     ```

3. Visit http://localhost:7860 in your browser to see if the app runs correctly.

<p align = "center" draggable=”false”>
<img src="https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/2c764f25-09a0-431b-8d28-32246e0ca1b7"> 
</p>

Great! Time to ship!
</details>

## 🚢 Ship 

### Deploying Your First LLM App

<details>
  <summary>🚀 Deploying Your First LLM App</summary>

1. Let's create a new Huggingface Space. Navigate to [Huggingface](https://huggingface.co) and click on your profile picture on the top right. Then click on `New Space`.

<p align = "center" draggable=”false”>
<img src="https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/f0656408-28b8-4876-9887-8f0c4b882bae"> 
</p>

2. Setup your space as shown below:
   
- Owner: Your username
- Space Name: `llm-app`
- License: `Openrail`
- Select the Space SDK: `Docker`
- Docker Template: `Blank`
- Space Hardware: `CPU basic - 2 vCPU - 16 GB - Free`
- Repo type: `Public`

<p align = "center" draggable=”false”>
<img src="https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/8f16afd1-6b46-4d9f-b642-8fefe355c5c9"> 
</p>

3. You should see something like this. We're now ready to send our files to our Huggingface Space. After cloning, move your files to this repo and push it along with your docker file. You DO NOT need to create a Dockerfile. Make sure NOT TO push your `.env` file. This should automatically be ignored.

<p align = "center" draggable=”false”>
<img src="https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/cbf366e2-7613-4223-932a-72c67a73f9c6"> 
</p>

4. After pushing all files, navigate to the settings in the top right to add your OpenAI API key.

<p align = "center" draggable=”false”>
<img src="https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/a1123a6f-abdd-4f76-bea4-39acf9928762"> 
</p>

5. Scroll down to `Variables and secrets` and click on `New secret` on the top right.

<p align = "center" draggable=”false”>
<img src="https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/a8a4a25d-752b-4036-b572-93381370c2db"> 
</p>

6. Set the name to `OPENAI_API_KEY` and add your OpenAI key under `Value`. Click save.

<p align = "center" draggable=”false”>
<img src="https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/0a897538-1779-48ff-bcb4-486af30f7a14"> 
</p>

7. To ensure your key is being used, we recommend you `Restart this Space`.

<p align = "center" draggable=”false”>
<img src="https://github.com/AI-Maker-Space/LLMOps-Dev-101/assets/37101144/fb1d83af-6ebe-4676-8bf5-b6d88f07c583"> 
</p>

</details>

### Assignment Submission

- Make your App public on Hugging Face and submit the link to your App for this assignment!
- Provide a URL to a loom video walkthrough (<5 min) of how it works
- For more on loom video best-practices, check out [this video](https://www.loom.com/share/70774f915c014da7b001e2e639f8fbb5?sid=861df19d-402e-47f1-85b4-048f8a9a8fad).

Submit [your assignment form](https://docs.google.com/forms/d/e/1FAIpQLSf7KsJ5swKvDeTV1H9u-vM_hOelK5m8DZ4Qtax87c5lBexD4w/viewform)!

## 🚀 Share

Share 🚀
- Share 3 lessons learned 
- Share 3 lessons not yet learned
- Share about your experience in a LinkedIn or X post, or in the Discord! 

> NOTE: Details on "How We Share" are available [here](https://www.loom.com/share/67b308aae47a402bbe5b26f8ef41f550?sid=b668369e-7eb1-4a5b-9a4d-9f62f3ddb299)


