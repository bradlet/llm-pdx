# RD7
[Chain-of-Thought Prompting Elicits Reasoning in Large Language Models, Wei et al., 2022](https://proceedings.neurips.cc/paper_files/paper/2022/file/9d5609613524ecf4f15af0f7b31abca4-Paper-Conference.pdf)


- Standard prompting -- just ask for answer; vs.
- Chain-of-thought prompting -- Ask for steps to arrive at answer, providing examples.
- Given sufficient scale, llm's are able to learn complex tasks from a few examples -- emergent ability.
  - Not very helpful for smaller models (create fluent but illogical chains of thought)
- When models generate a chain-of-thought expressing the reasoning behind some answer to a prompy, the accuracy of that answer increases significantly.
- Chain of thought prompting allows models to decompose multi-step propblems, so additional computation is spent on the intermediate steps.
- Chain of thought gives insight into model behavior and reasoning (++ interpretable machine learning (IML))
- Widely applicable to any language-based tasks.
- Baseline for standard prompting is still few-shot instead of one-shot prompting, which further exemplifies the benefits of chain-of-thought prompting.
- Ablation study:
  - Equation only: Instead of full chain of thought, only output math equation used to arrive at answer. Not as good still, so something about the use of natural language matters.
  - Variable compute only: asking model to come up with equation makes it spend more compution/intermediate-tokens on harder problems. So just ask it to output dots for each character in the equation. Still performs similar to baseline.
  - Chain of thought after the answer: Still worse, so something about using the chain of thought as part of arriving at the answer matters.

Language models are Few Shot Learners:

- Models
	- RD7 Paper: LaMDA 400m, 8b, 137b; GPT 400m, 7b, 175b; PaLM 8b, 62b, 540b; UL2 20B; Codex.
		- No fine-tuning, all ICL.
	- OG Paper: 8 GPT models from param count of 125m - 175b.
		- Performed fine-tuning on a subset of CommonCrawl.
		- Provided varying counts of examples when prompting the models (a'la "Simple prompting" in the chain of thought paper).
	- Both use different benchmarks for performance
	- Essentially what's new here is the researchers for the chain-of-though paper enhance the example provided in the few-shot prompting case to push the model to perform additional natural language computation on building a chain of thought before arriving at an answer.
	- Through ablation studies, the researchers showed that it isn't just providing examples, or pushing the language model to spend more intermediate tokens in its computation, that improves performance.
		- The OG paper (few shot learners) showed that providing examples improves performance; the new paper shows that there is some emergent property that allows large language models to form some kind of logical reasoning by generating chains of thought in building an answer, improving performance.
