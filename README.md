# ReasonFusion

Claude and ChatGPT work through a hard research problem together. They debate it as domain experts, critique each other's solutions, and then co-write a paper whose references are all checked against real scholarly databases.

**Live app:** https://engr-dr-ammad.github.io/ReasonFusion/

## How it works

1. **Literature.** Claude writes search queries, and the app pulls real papers with their abstracts from [OpenAlex](https://openalex.org). Any DOIs you supply are resolved through [Crossref](https://www.crossref.org).
2. **Debate.** In each round, both models solve the problem on their own, then critique the other's latest solution and revise their own. The debate ends when both report `AGREEMENT: yes` or the round limit is reached.
3. **Extra references.** Each model suggests more sources. A suggestion is kept only if its DOI or title matches a Crossref or OpenAlex record. Everything else is rejected and listed.
4. **Draft, review, revise.** The lead author drafts the paper, the other model peer-reviews it, and the lead author revises.
5. **Citation check.** Citations can point only to verified sources, and any invalid tag becomes `[citation needed]`. The reference list is built from database metadata, never from model output. The app adds an AI assistance statement.

Exports: Markdown, BibTeX, and the full debate transcript.

## Using it

Open the live app and enter your Anthropic and OpenAI API keys. The page sends them straight from your browser to `api.anthropic.com` and `api.openai.com`, with no server in between. Keys are saved in your browser only if you tick "Remember keys". Model names can be edited, so you can switch to newer models when they come out.

On a phone, open the link and choose **Add to Home Screen** to use it as an app. You can also download `index.html` and open it locally.

## Limits

- Verification proves a source **exists** and that its metadata is correct. It doesn't prove the source supports the sentence that cites it, so read every cited paper.
- The models can't run experiments. The prompts tell them never to invent results and to describe an evaluation plan instead.
- Many journals don't allow AI to be listed as an author and require AI use to be disclosed. The human authors are responsible for the final manuscript.
- Each run costs API usage, roughly 15–30 calls.
