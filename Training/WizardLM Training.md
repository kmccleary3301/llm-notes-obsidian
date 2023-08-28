 > [!info]- Basic Fine-Tune Execution WizardMath
 > [Instructions Available Here](https://github.com/nlpxucan/WizardLM/blob/main/WizardMath/README.md)
 > Install venv
 > loggin to huggingface-cli via command line.
 > ```python
 > deepspeed train_wizardmath.py \
 > --model_name_or_path "/your/path/to/llama-2-13b" \
 > --data_path  "/your/path/to/math_instruction_data.json"\
 > --output_dir  "/your/path/to/save_ckpt"\
 > --num_train_epochs 3 \
 > --model_max_length 2048 \
 > --per_device_train_batch_size 16 \
 > --per_device_eval_batch_size 1 \
 > --gradient_accumulation_steps 1 \
 > --evaluation_strategy "no" \
 > --save_strategy "steps" \
 > --save_steps 50 \
 > --save_total_limit 50 \
 > --learning_rate 2e-5 \
 > --warmup_steps 10 \
 > --logging_steps 2 \
 > --lr_scheduler_type "cosine" \
 > --report_to "tensorboard" \
 > --gradient_checkpointing True \
 > --deepspeed config/deepspeed_config.json \
 > --fp16 True \
 > ```



