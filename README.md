Evaluate LLM models using evalplus - https://github.com/evalplus/evalplus

The following models were evaluated using evalplus: \
CodeT5 2B \
Llama 7B 

Running the python notebook Evaluate_LLM.ipynb will generate files codet5_2b_samples.jsonl and llama_7b_hf_samples.jsonl which contains the code snippets for prompts mentioned in HumanEval dataset. These code snippets will be evaluated using evalplus framework. 

#### Evaluate CodeT5 with pass@k = 1: 
(Below command is ran on Macbook Air M1, hence --platform linux/amd64 option is included)\
docker run --platform linux/amd64 -v $(pwd):/app ganler/evalplus:latest --dataset humaneval --samples codet5_2b_samples.jsonl 
```
Computing expected output...
Expected outputs computed in 215.67s
Reading samples...
164it [00:00, 489.66it/s]
100%|██████████| 164/164 [00:32<00:00,  5.01it/s]
Base
{'pass@1': 0.25} - 
Base + Extra
{'pass@1': 0.21341463414634146}
```
This means that out of 164 problems, it is correctly able to give solution for 35-40 problems\
A file with codet5_2b_samples_eval_results.jsonl will also be generated with the results 

#### Evaluate Llama with pass@k = 1:
docker run --platform linux/amd64 -v $(pwd):/app ganler/evalplus:latest --dataset humaneval --samples llama_7b_hf_samples.jsonl
```
Downloading HumanEvalPlus dataset...
Computing expected output...
Expected outputs computed in 219.98s
Reading samples...
164it [00:00, 592.20it/s]
100%|██████████| 164/164 [00:32<00:00,  5.10it/s]
Base
{'pass@1': 0.11585365853658537}
Base + Extra
{'pass@1': 0.0975609756097561}
```
This means that out of 164 problems, it is correctly able to  give solution for 15-20 problems\
A file with llama_7b_hf_samples_eval_results.jsonl will also be generated with the results 

