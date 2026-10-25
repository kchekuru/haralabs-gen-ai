paradigms with large langueage driven applications

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

"grounding"
grounding_with_vais.ipynb
intro-grounding-gemini.ipynb

"prompt engineering"
chain_of_thought_react.ipynb
intro_prompt_design.ipynb
/Users/kchekuru/src/gen-ai/generative-ai/gemini/prompts/prompt_optimizer
vapo_lib.py

reasoning-style prompts and ReAct.
system instructions and few-shot prompting.
prompt optimization - including custom metrics, long prompts, multimodal prompts, and tool usage.
utilities for validating prompt templates and datasets.
