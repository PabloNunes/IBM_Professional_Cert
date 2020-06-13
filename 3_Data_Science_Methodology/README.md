# Data Science Methodology - Summary

## Made by Pablo Nunes

----

## Methodology(s)

- Definition: Is a system of methods used in a particular area of study
- This course has the objective to share the methodology that can be used in data science, to ensure that the data used in problem solving is relevant and correctly manipulated to address the questions
- The Data Science methodology has 10 questions based from the experience of John Rollins (IBM):
  - **Problem to approach**:
    1. What is the problem that you are trying to solve?
    2. How can you use data to answer the question?
  - **Working with the data**:
     1. What data you need to answer the question?
     2. Where is the data coming from? How will you get it?
     3. Is the data representative of the problem?
     4. What additional work is required to manipulate and work with the data?
  - **Delivering the answer**:
    1. In what way can the data be visualized to get to the answer that is requires?
    2. Does the model used answer the initial question?
    3. Can you put the model in practice?
    4. Can you get constructive feedback into answering the question?
- In this course uses another methodology called CRISP-DM.
- CRISP-DM is a methodology which take specific case scenarios and general behaviors to make them domain neutral.
- CRISP-DM is comprised of 6 steps:
  - Business Understanding: The intention of the project is outlined
  - Data Understanding: Data is collected and what data is collected.
  - Data preparation: Checking data for consistency and transforming the data.
  - Modeling: The data must create a model capable of create insights and revealing patterns and structures within the data.
  - Evaluation: The model is tested.
  - Deployment: The model is used on new data and can initiate revision of the process.

## Bussiness Understanding

- To understand the business is important in Data Science, because it allows you to determine which data will be used to answer the core question.
- To clarify the core question is important, to establish the question, we must know the goal!
- Next, we must know what objectives are in support of the goal.

## Analytic Approach

- To approach the question, we need to know in identifying what types of patterns will be needed to address the question most effectively.
- Can be summed in: How can you use data to answer the question?
- If is a question about probabilities: Use a Predictive model
- Show Relationships: Descriptive model
- Yes/No: Classification model

## Data Requirements

- The data scientist must know to solve the core question which kind of data is required, how to source it, how to understand or work with it, and prepare the data.
- Summed: What are the data requirements? What occurs during data collection?

## Data Collection

- We must analyze the data, and notice if it is enough and makes sense or is insufficient for our needs.
- If it isn't enough, we must gather and fill the gaps needed. Collect and know the sources.
- Summed: What are the data Requirements?

## Data Understanding

- Summed: Is the data you collected representative of the problem to be solved?

## Data Preparation

- It is the most time consuming step in the project. 70% to 90%
- Summed: It is the clean and transformation data step. Determining the timespan and the variables used for the models.
- Take your time to prepare your data and try to automate as much you can.

## Modeling

- In what way can the data be visualized to get the answer that is required?
- Descriptive Analytics vs Predictive Analytics
- Training/Test Sets
- To properly model, we need:
  - Understand the question at hand
  - Select an analytic approach or method to solve the problem
  - Obtain, understand, prepare, and model the data
- Was the question answered?

## Evaluation

- Does this model really answer the initial question? Or needs adjustments?
- To evaluate we can use diagnostics measures and Statistical significance
- To evaluate different models, we use the ROC curve. True-Positive Rate vs. False-Positive Rate

## Deployment

- Are stakeholders familiar with the new tool?
- The scientist must be confident it will work before deploying the solution.

## Feedback

- The feedback of the users is used to refine the model!
