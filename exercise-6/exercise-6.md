# Exercise 6 - OpenAI

> [!NOTE]
> Timebox: 30 minutes
> 
> [Back to Agenda](./../README.md#agenda) | [Back to Exercise 5](./../exercise-5/exercise-5.md) | [Up next extra exercises](../exercise-extra/extra.md)
>

# Exercise 6 - Enrich the data with GenAI

In this exercise, you will work with text data consisting of reviews of taxi trips. You will use Fabric notebooks to join it with previous tables, and then prebuilt AI models to utilize GenAI possibilities within Fabric. The prebuilt solutions will allow you to translate text, analyze sentiment, and use OpenAI models without any configuration outside Fabric. The main goal of the exercise is to generate responses to the reviews with OpenAI.

Firstly, we need to access taxi trip review data. To do so, we need to follow the steps below:

1. Download the file with reviews to your local machine. [Download Reviews Data](exercise-6/reviews.parquet).
2. Upload the additional data to your Bronze Lakehouse, just like during exercise 2:
* Go to the `Files` section in your Bronze Lakehouse. 
* Click on the three dots to access additional options and select the `Upload` button. 
* Choose `Upload Files` from the menu.
The file should upload within a few seconds. 

After obtaining the data you are ready to start the exercise:

1. **Download the Exercise Notebook**:
   - Download the provided Jupyter notebook, [Exercise 6 - Enrich the data with GenAI](exercise-6/Exercise-6.ipynb), to your local computer. This notebook contains the steps you will follow to complete the task. 

2. **Import the Notebook into Fabric Workspace**:
   - Navigate to your Fabric workspace, either in the Data Engineering or Data Science section.
   - Import the downloaded notebook by following the instructions provided in [Exercise 2 - Importing Notebooks](../exercise-2/exercise-2.md#1-importing-the-notebook). This involves selecting the option to import existing notebooks and choosing the downloaded .ipynb file from your local computer.

3. **Follow Notebook Instructions**:
   - Once the notebook is imported into your Fabric workspace, open it.
   - Follow the detailed steps outlined within the notebook.

4. **Complete the Exercise**:
   - Work through each step in the notebook, executing code cells and noting any insights or observations.
   - Make sure to save your progress as you work through the notebook.
