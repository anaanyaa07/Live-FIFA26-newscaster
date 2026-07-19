# Live-FIFA26-newscaster

⚽ Football Companion — n8n Workflow

An n8n workflow that generates a friendly, beginner-focused football newsletter on demand, pulling the latest FIFA tournament news via SerpApi and writing it up with Claude.

What it does


A form ("Football news for today") triggers the workflow when submitted.
An AI Agent (Claude Sonnet 4.6) searches Google via SerpApi for the latest football happenings, using today's date.
Claude formats the results into an HTML newsletter called "⚽ Football Companion", with:

A top story section with scores, scorers, and goal minutes
Inline explainer boxes (📖) that define football terms for beginners
A section previewing upcoming fixtures (date, time, venue)
A warm, emoji-friendly tone written for people who don't follow football



The result is shown back to the user on the same form.


Workflow structure

NodePurposeOn form submissionTrigger — starts the workflow when the form is submittedAI AgentCore logic — prompts Claude to research and write the newsletterAnthropic Chat ModelLanguage model powering the AI Agent (Claude Sonnet 4.6)Google search in SerpApiTool the AI Agent uses to fetch live football newsFormDisplays the generated newsletter as the response

Requirements


An n8n instance (Cloud or self-hosted)
Anthropic API credential (for the Claude language model node)
SerpApi credential (for live search results)


Credentials are not included in this export for security reasons — you'll need to create your own and connect them after import.

Setup


Download football-latest-news.json from this repo (or clone the repo).
In n8n, go to Workflows → Add workflow → Import from File, and select the JSON file.
Open the Anthropic Chat Model node and select/create your Anthropic credential.
Open the Google search in SerpApi node and select/create your SerpApi credential.
Save and Activate the workflow.
Open the form trigger's production URL and submit it to generate a newsletter.


Notes


The agent is instructed to only use facts confirmed by the SerpApi search tool and never invent scores, names, or dates.
Output is returned as raw HTML, ready to drop into an email or webpage.
