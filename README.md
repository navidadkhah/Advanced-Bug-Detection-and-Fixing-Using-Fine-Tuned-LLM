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
