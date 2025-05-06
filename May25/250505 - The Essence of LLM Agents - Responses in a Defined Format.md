It's been two years since LLM agents made their debut. From babyAGI to LangChain, many major players now have their own LLM agent SDKs, each with tens of thousands of stars on GitHub. Not only these, but also many related tools—like A2A and MCP—have gained popularity.

However, I’ve found it is not easy to find an agent framework that meets my two simple requirements:

- Easy to change the prompt—both the system prompt and intermediate prompts.
- Simple tracking and debugging capabilities.

I've tested some options. Google's ADK is great for tracking, but after an hour of experimentation, I still couldn't figure out how it produces the system prompt, let alone how to change it.

While checking the prompts, I also discovered that Google's SDK doesn’t use the PLAN/THOUGHT state found in the ReAct framework. It simply performs casual function calling from the model. That reminded me that RooCode (a popular AI coding extension, most used app on OpenRouter) also doesn’t use PLAN/THOUGHT.

I've seen some recent talks from OpenAI and Anthropic, and they don’t mention the PLAN/THOUGHT state anymore. So, it seems that recent LLM agents can operate effectively without PLAN/THOUGHT.

I think this change comes from several reasons:

- Earlier LLMs (like GPT-3.5) were not very good at reasoning. Now, LLMs are much better at reasoning and also trained to use function calling effectively.
- If needed, we can still trigger the model's reasoning, and it can handle PLAN/THOUGHT states quite well. For some complex tasks I've tested, this actually improves results.

One more thing: RooCode doesn’t use function calling at all. It just calls the response and does some text processing—a bit like old-fashioned LLM agents. This shows that the essence of LLM agents is simply returning responses in a defined format. Whether it's function calling or formatted text, both approaches are valid (but function calling is better).

Lastly, I think agents are often overcomplicated for many use cases. Workflows might be better in most situations, especially in programming. They're faster, less error-prone, and easier to predict. Don’t just follow the hype—use what actually works.