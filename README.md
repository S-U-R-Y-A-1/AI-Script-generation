# AI-Script-generation
Fine tuned latest Microsoft phi 3 model loaded from unsloth platform.
# Microsoft-phi-3-fine-tuning
AI Social Media Script Generator with LoRA Fine-tuning
This repository contains code for a web interface that leverages a LoRA fine-tuned model to generate creative social media post scripts.
Features:

● Generates scripts based on a provided topic and optional details for Hook, Build Up, and Body sections.

● Uses the microsoft-phi-3 pre-trained model (replace with your own if desired).

● Offers user interface:

○ Gradio interface for a user-friendly web interface.

Requirements:

● Python 3.7+

● Unsloth

● Accelerator

● Gradio (pip install gradio)

● Transformers (pip install transformers)

Installation:

1. Download the colab notebook.
2. Install the required libraries.
3. Download the microsoft-phi-3 model checkpoint and tokenizer files (or use your own model). Place them in a suitable directory (modify paths in the code if
needed).
4. Apply the LoRA adapters, with bias as “none” and stabilized script generation.
5. From the dataset uploaded with addition of including topic labelling for better understanding of relationships between user input and script generation.
6. Give the prompt template:
   
Below is a Topic for a social media post. Generate the script like
given in the Hook,Build Up,Body.
### Topic:
{}
### Script:
{}

7. Load the dataset which was uploaded in huggingface_hub:

https://huggingface.co/datasets/Surya1523/data_man

8. Train the model with specified parameters:

args = TrainingArguments(
per_device_train_batch_size = 2,
gradient_accumulation_steps = 4,
warmup_steps = 5,
max_steps = 60,
learning_rate = 2e-4,
fp16 = not torch.cuda.is_bf16_supported(),
bf16 = torch.cuda.is_bf16_supported(),
logging_steps = 1,
optim = "adamw_8bit",
weight_decay = 0.01,
lr_scheduler_type = "linear",
seed = 3407,
output_dir = "outputs",
),

9. Test the model

Running the App (Gradio)(If local):

1. Open a terminal, navigate to the project directory.

2. Run python social_media_script_gradio.py (or the appropriate filename).

3. The Gradio interface will launch in your web browser, typically at

http://127.0.0.1:7861.

Running the App (Gradio)(If Colab):

1. Run the selected gradio cell.

2. Follow the given link to access the application.

Evaluation:

Evaluating the quality and relevance of generated scripts involves:

● Human Evaluation: Experts assess scripts based on criteria like coherence, informativeness, and engagement.
● ROUGE Score: Measures overlap between generated text and reference scripts
(automated metric).

Inference : Human Evaluation is executed with the application deployment. ROUGE Score is evaluated on the reference with the dataset.

Further Enhancements:

● Explore different pre-trained models and fine-tuning techniques for potentially
better results.

● Implement functionalities to control generation style (e.g., formality, tone).

● Integrate the model into a social media management platform for seamless workflow.

https://github.com/S-U-R-Y-A-1/Microsoft-phi-3-fine-tuning/assets/126397104/81bf988c-6349-46ca-a6f0-5e2e3e9dae81
