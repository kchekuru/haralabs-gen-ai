paradigms ( prompt,tools,interfaces ) with large langueage driven applications

"hallunication-checking"
prompts.py , eval.py , metrics.py [ confidence-targeted abstention, based on the paper arXiv:2509.04664 ]

def build_conf_prompt(question: str, t: float) -> str:
    pen = round(t / (1.0 - t), 3) if t < 1 else "infinite"
    t_disp = f"{t:.2f}".rstrip("0").rstrip(".")
    return (
        f"{question}\n\n"
        f"Answer only if you are > {t_disp} confident.\n"
        f"Scoring: correct = +1, incorrect = -{pen}, 'IDK' = 0.\n"
        f"If you are not > {t_disp} confident, reply EXACTLY 'IDK'.\n"
        "Output only the final answer (or 'IDK')."
    )

other ways for checking/minimizing hallucination is with 'post training' - SFT, LoRA

"grounding"
grounding_with_vais.ipynb
grounded with vertex ai search
intro-grounding-gemini.ipynb
grounded with s3/relational data/data lake entries

"prompt engineering"
chain_of_thought_react.ipynb
reasoning and actions
intro_prompt_design.ipynb
/Users/kchekuru/src/gen-ai/generative-ai/gemini/prompts/prompt_optimizer
vapo_lib.py
vertex ai prompt optimization library / interface

reasoning-style prompts and ReAct.
system instructions and few-shot prompting.
prompt optimization - including custom metrics, long prompts, multimodal prompts, and tool usage.

utilities for validating prompt templates and datasets.

 "function-calling patterns"
 /Users/kchekuru/src/gen-ai/generative-ai/gemini/function-calling
pattern # 1 declare tool, let genAI based trained model intelligently choose tool (AUTO)
pattern # 2 force genAI based trained model to choose a 'specific' tool (ANY)
pattern # 3 genAI model handles parallel function calls

"structured output design"
/Users/kchekuru/src/gen-ai/generative-ai/gemini/controlled-generation/intro_controlled_generation.ipynb
output from genAI model is not 'free text langueage' but structured ( what better then JSON output [insted of xml] these days schema for structure)

"authorization"
Use server-side authorization, narrow tool permissions, and human confirmation for sensitive actions.
pattern #1 treat user prompts and retrieved free text data as untrusted, hence enforcing access control / authorization in application layer
for example: say model suggests refund - don't let model execute refund flow, rather enforce refund flow in application layer
pattern #2 narrower tool permissions, human confirmation for sensitive action should be handled in application layer

"genAI infused application security"
gemini_prompt_attacks_mitigation_examples.ipynb
