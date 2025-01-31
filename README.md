# Feasibility of Bug Detection and Bug Fixing Using Prompt Engineering and Fine-Tuning in Large Language Models

## Overview
This repository hosts the project dedicated to evaluating the feasibility of detecting and fixing bugs using prompt engineering and fine-tuning techniques in large language models (LLMs). The project utilizes a custom dataset and innovative methods to enhance the LLM's capabilities in understanding and correcting code errors. Here are the topics in this project:
- [Dataset Description](#dataset-description)
- [Dataset Creation Process](#dataset-creation-process)
- [Model Description](#model-description)
- [Prompt Engineering](#prompt-engineering)
- [Fine-Tuning](#fine-tuning)
- [Evaluation Metrics](#evaluation-metrics)
- [Conclusion](#conclusion)
- [How to Use](#how-to-use)


## Dataset Description
The dataset, named `bug_evaluation_dataset`, is meticulously crafted to train and test LLMs specifically for bug detection and correction tasks. It comprises 25,793 rows, each containing:
- `original_code`: The buggy code snippet.
- `modified_code`: The corrected code snippet.
- `changed_line`: The specific line in the code where the bug was fixed.
- `number_of_line`: The line number of the corrected code.
- `mutation_type`: Type of bug introduced; includes Operation, Decision, Value, and Statement mutations.

This dataset was generated using Mutation Testing techniques to systematically introduce bugs into existing clean code. The types of mutations are designed to simulate common logical and syntactic errors developers might encounter.

**For a visual representation of the dataset structure and mutation types, see Figures 2 and 16.**

## Dataset Creation Process
The dataset was curated through a semi-automated process:
1. **Code Extraction**: Clean code snippets were extracted from open-source repositories.
2. **Mutation Injection**: Bugs were introduced into the clean code using predefined mutation rules to alter specific parts of the code logically.
3. **Data Compilation**: Each entry in the dataset includes the bugged code, the fix, the location of the fix, and the type of mutation, prepared for LLM training and evaluation.

## Model Description
The backbone of our fine-tuning experiments is the [Unsloth Meta-Llama 3.1-8B](https://github.com/unslothai/unsloth) model, renowned for its high performance in natural language understanding and generation tasks, including code generation and debugging. This model's capabilities make it ideally suited for addressing complex tasks involved in software debugging.

**A detailed view of the model’s architecture can be seen in Figure 1.**

## Prompt Engineering
Prompt engineering involves crafting and testing prompts that effectively guide LLMs to recognize and fix code errors. The process is detailed in the `Prompt_Engineering.ipynb` notebook, where different prompt formats and their impact on the LLM’s performance are explored. We introduced the `6` type of prompt that are used in the model. 

<table>
 
  <thead>
    <tr>
      <th>
          **Prompts**
      </th>
      <th>
          **Explanations**
      </th>
    </tr>
  </thead>
  
  <tbody>
    <tr>
      <td>
            `
           P1: Direct Instruction Prompts
            `
      </td>
      <td >
            These prompts explicitly instruct the model to identify and fix errors in the code, using clear and direct language to guide the model's response.
      </td>
    </tr>
  </tbody>
  
  <tbody>
    <tr>
      <td>
           ```
           P2: Contextual Prompts
           ```
      </td>
      <td>
           These prompts provide additional context about the purpose or functionality of the code, helping the model understand the intended behavior and identify discrepancies.
      </td>
    </tr>

  </tbody>
  <tbody>
    <tr>
      <td>
```
P3: Error Description Prompts
```
      </td>
      <td>
These involve describing a known error within the code and asking the model to correct it, which helps in scenarios where specific bug types are targeted.
      </td>
    </tr>


  </thead>
  <tbody>
    <tr>
      <td>
```
P4: Comparative Prompts
```
      </td>
      <td>
These prompts involve comparing the buggy code to a similar, but correct, code snippet to guide the model in understanding the corrections needed.
      </td>
    </tr>

  </thead>
  <tbody>
    <tr>
      <td>
```
P5: Test Case Prompts
```
      </td>
      <td>
Involving test cases that the code must pass, these prompts help the model focus on producing a valid output that meets specified conditions, enhancing its debugging capabilities.
      </td>
    </tr>


  </thead>
  <tbody>
    <tr>
      <td>
```
P6: Iterative Refinement Prompts
```
      </td>
      <td>
These prompts ask the model to iteratively refine the code based on feedback or errors identified in previous attempts, encouraging a more detailed focus on incremental improvements.
      </td>
    </tr>

  </tbody>
</table>

## Fine-Tuning
Fine-tuning is conducted using the state-of-the-art LLM, detailed in the `Unsloth_Llama_3_1_8B.ipynb`. This process adjusts the model's weights based on our dataset to specialize its ability in the coding domain, focusing particularly on bug detection and resolution.

**Fine-tuning processes and prompt engineering illustrations are shown in Figures 4, 9, 10, and 11.**


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
