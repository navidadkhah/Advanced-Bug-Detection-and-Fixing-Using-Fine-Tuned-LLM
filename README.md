# Prompt Engineering and Fine Tuning LLMs for bug prediction
# LLMs
# Prompt Engineering
# Fine Tuning
# Methods & metrics
# Dataset
The Dataset is used for bug evaluation and the exact location of the fault has occurred. It has five columns:
 - original_code
 - modified_code
 - changed_line
 - number_of_line
 - mutation_type

You can access to the dataset with this [LINk](#)
   
In the Dataset Folder, I Collected and split datasets to train/test/validate. It has two columns containing ```buggy code``` and ```fixed code```.
<br>
The number of rows for each file is as follows:
<table style="width:100%">
 <tr>
    <th><a href="https://github.com/navidadkhah/Fine-Tuning-LLMs/blob/main/Dataset/train.csv">Train.csv</a></th>
    <th>52.4k rows</th>
  </tr>
   <tr>
     <th> <a href="https://github.com/navidadkhah/Fine-Tuning-LLMs/blob/main/Dataset/test.csv">Test.csv</a></th>
    <th>6.55k rows</th>
  </tr>
   <tr>
    <th><a href="https://github.com/navidadkhah/Fine-Tuning-LLMs/blob/main/Dataset/validation.csv">Validation.csv</a></th>
    <th>6.55k rows</th>
  </tr>
</table>



# Feasibility of Bug Detection and Bug Fixing Using Prompt Engineering and Fine-Tuning in Large Language Models

## Overview
This repository hosts the project dedicated to evaluating the feasibility of detecting and fixing bugs using prompt engineering and fine-tuning techniques in large language models (LLMs). The project utilizes a custom dataset and innovative methods to enhance the LLM's capabilities in understanding and correcting code errors.

## Dataset Description
The dataset, named `bug_evaluation_dataset`, is meticulously crafted to train and test LLMs specifically for bug detection and correction tasks. It comprises 25,793 rows, each containing:
- `original_code`: The buggy code snippet.
- `modified_code`: The corrected code snippet.
- `changed_line`: The specific line in the code where the bug was fixed.
- `number_of_line`: Line number of the corrected code.
- `mutation_type`: Type of bug introduced; includes Operation, Decision, Value, and Statement mutations.

This dataset was generated using Mutation Testing techniques to systematically introduce bugs into existing clean code. The types of mutations are designed to simulate common logical and syntactic errors developers might encounter.

**For a visual representation of the dataset structure and mutation types, see Figures 2 and 16.**

## Creation Process
The dataset was curated through a semi-automated process:
1. **Code Extraction**: Clean code snippets were extracted from open-source repositories.
2. **Mutation Injection**: Bugs were introduced into the clean code using predefined mutation rules to alter specific parts of the code logically.
3. **Data Compilation**: Each entry in the dataset includes the bugged code, the fix, the location of the fix, and the type of mutation, prepared for LLM training and evaluation.

## Prompt Engineering and Fine-Tuning Techniques
### Prompt Engineering
Prompt engineering involves crafting and testing prompts that effectively guide LLMs to recognize and fix code errors. The process is detailed in the `Prompt_Engineering.ipynb` notebook, where different prompt formats and their impact on the LLM’s performance are explored.

### Fine-Tuning
Fine-tuning is conducted using the state-of-the-art LLM, detailed in the `Unsloth_Llama_3_1_8B.ipynb`. This process adjusts the model's weights based on our dataset to specialize its ability in the coding domain, focusing particularly on bug detection and resolution.

**Fine-tuning processes and prompt engineering illustrations are shown in Figures 4, 9, 10, and 11.**

## Model Description
The backbone of our fine-tuning experiments is the Unsloth Meta-Llama 3.1-8B model, renowned for its high performance in natural language understanding and generation tasks, including code generation and debugging. This model's capabilities make it ideally suited for addressing complex tasks involved in software debugging.

**A detailed view of the model’s architecture can be seen in Figure 1.**

## Evaluation Metrics
To assess the effectiveness of the model post-training, several metrics are employed:
- **Exact Match**: Measures the percentage of instances where the model’s output matches the expected corrected code exactly.
- **CodeBLEU**: Assesses code similarity considering syntax and semantic correctness.
- **ROUGE**: Evaluates the overlap of n-grams between the model’s output and the target code.
- **SAS**: A syntax-aware semantic evaluation metric focusing on logical correctness of the code.

**Results of these metrics are illustrated in Figures 30, 31, 32, and 33.**

## Conclusion
This project pushes the boundaries of what LLMs can achieve in software engineering contexts, providing tools and methodologies to enhance coding efficiency and accuracy through advanced AI techniques.

## How to Use
To replicate the experiments or utilize the methodologies:
1. Clone the repository.
2. Ensure you have the required computing resources and dependencies installed.
3. Follow the instructions in each notebook to train or evaluate the model.

For further details, refer to each notebook's documentation within the repository.
