# GCP-Machine-Learning-Engineer-Notes

Course https://partner.cloudskillsboost.google/paths/84

### Responsible AI 
- Responsible AI refers to the development and use of artificial intelligence systems in a way that prioritizes ethical considerations, fairness, accountability, safety, and transparency.

#### Zero-Shot Prompting
- Definition: Zero-shot prompting is when you give the model only an instruction or a question, without providing any examples.Zero-shot prompting output

#### Few-Shot Prompting
- Definition: Few-shot prompting is when you provide the model with a few task-specific examples before giving it a new, similar task.

##### An Example Few-Shot Prompting:
- Policy Number: POL77521
- Claimant Name: John Sterling
- Date of Loss: May 10th, 2025
- Time of Loss: Night
- Type of Loss: Water damage
- Brief Description of Damage: Pipe burst in ceiling, stockroom flooded, some damage to inventory.
- Estimated Loss Amount: $5,000 - $10,000
- Injuries Reported: No


### Zero-shot prompting vs Few-Shot prompting outpot
- Zero-Shot Prompting output
<img width="708" height="275" alt="Screenshot 2025-07-20 at 15 13 54" src="https://github.com/user-attachments/assets/e353dc28-6f39-42ce-b990-4f35ffac3cbe" />

- Few-Shot prompting outpot
<img width="700" height="287" alt="Screenshot 2025-07-20 at 15 08 58" src="https://github.com/user-attachments/assets/fedd03bb-82b2-4b5f-adfe-bc15143836e4" />


### Design effective prompts

- Experimenting with prompt configurations (Temperature: 0.2, Top-P: 1)
<img width="654" height="189" alt="temperature 0 2" src="https://github.com/user-attachments/assets/c2b6f521-1639-424c-b19e-6423659bd7d0" />

- Experimenting with prompt configurations (Temperature: 1.9, Top-P: 1)
<img width="655" height="195" alt="temperature 1 9" src="https://github.com/user-attachments/assets/486c2d08-77a7-4ac5-8289-7417b0682dc5" />

- Experimenting with prompt configurations (Temperature: 1.5, Top-P: 0.12)
<img width="799" height="178" alt="Screenshot 2025-07-20 at 16 22 15" src="https://github.com/user-attachments/assets/81f32f6e-2285-443a-ab92-44b26767dbd4" />

- Experimenting with prompt configurations (Temperature: 1.5, Top-P: 1)
<img width="792" height="170" alt="Screenshot 2025-07-20 at 16 23 02" src="https://github.com/user-attachments/assets/acb1ec8d-ca32-4585-8af4-2990ec62e44c" />


### In Practice: Temperature vs Top-P
| Feature                  | **Temperature**                                   | **Top-p (Nucleus Sampling)**                                   |
| ------------------------ | ------------------------------------------------- | -------------------------------------------------------------- |
| **What it does**         | Controls how *random* the next token selection is | Filters the token pool to a top % of probability mass          |
| **Value Range**          | Typically `0.0` to `2.0`                          | Typically `0.0` to `1.0`                                       |
| **How it works**         | Scales the logits before applying softmax         | Only considers the top tokens whose combined probabilities ≥ p |
| **Effect of low value**  | More deterministic (e.g., `temperature=0.1`)      | Fewer tokens considered (e.g., `top_p=0.1`)                    |
| **Effect of high value** | More random and diverse                           | Includes more tokens, more diversity                           |
| **Common default**       | 0.7 or 1.0                                        | 0.9                                                            |
| **Best for**             | Global randomness control                         | Local dynamic filtering based on probability                   |


- Use **Temperature** to control "how creative" you want the generation to be.

- Use **top-p** to restrict sampling to only the most likely, relevant choices.

- For reliable outputs, lower both.

- For brainstorming or poetry, increase both.

#### Best Practice - You can combine both for more nuanced control:

- For creative writing: temperature = 0.9, top_p = 0.95

- For precise tasks: temperature = 0.2, top_p = 0.8

- For deterministic output: temperature = 0.0 (top-p has no effect)



