#

##
1. Project
I built a reusable AI-powered UGC advertising prompt system that generates short-form video ad content — hooks, full scripts, CTAs, captions, and platform adaptations — for a real local business, using Claude as the generation engine.

2. Business
Mozambik Somerset West, an Afro-Portuguese casual dining restaurant located in The Sanctuary Shopping Centre, Somerset West, South Africa. It serves peri-peri and garlic-lemon-herb chicken, prawns, Portuguese-inspired dishes, and vegetarian/vegan options, with a relaxed beach-bar atmosphere.

3. Problem
The ads address two linked customer problems: people get bored returning to the same restaurants, and groups often struggle to agree on somewhere that has enough variety for everyone (different diets, different cravings). Every hook, script, and CTA in the system was built to speak directly to that decision-making friction, rather than generic restaurant marketing.

4. Prompt logic
The system works in a layered sequence rather than one single prompt:

A base business profile (name, audience, problem, product, tone, platforms, CTA) is defined once and reused across every output.
That profile feeds a hook-generation prompt that produces multiple angles (problem, curiosity, personal experience, etc.) constrained by word count and tone rules.
The strongest hook is carried forward into a structured script prompt (Hook → Problem → Personal Experience → Solution → Benefit → CTA).
A separate critique prompt scores the script against fixed criteria and flags anything that reads like traditional advertising, before a rewrite pass fixes only the weak sections.
The same core concept is then re-prompted for different formats (Reels, Shorts, Paid Social) and different output types (CTAs, captions), always inheriting the same business profile so messaging stays consistent.
A final QC prompt re-checks every output against a fixed checklist before anything is considered final.

5. Prompt engineering techniques

Variable-based prompting — business details (name, location, audience, products, tone, CTA) were defined once as reusable variables and referenced across every prompt, rather than rewritten each time.
Role prompting — Claude was assigned specific roles ("experienced UGC advertising copywriter," "UGC advertising editor") to shape the style and standard of each output.
Constraint prompting — hard limits were enforced throughout: word counts on hooks and CTAs, a fixed six-part script structure, hashtag limits on captions, and an explicit rule against inventing testimonials, stats, or claims.
Tone conditioning — every output was constrained to sound authentic, conversational, and spoken-aloud natural, explicitly avoiding corporate or ad-style phrasing.
Structured output — outputs were requested in consistent, labeled formats (hook/problem/experience/solution/benefit/CTA; tables for QC scoring) so results are predictable and easy to reuse.
Iterative refinement — scripts and hooks were critiqued against scoring criteria, weak sections identified, and only those sections rewritten rather than regenerating from scratch.
Platform adaptation — the same core concept was re-prompted with platform-specific constraints (length, pacing, hook style) for Instagram Reels, YouTube Shorts, and Paid Social.
Quality control — a final structured QC pass checked every output against ten fixed criteria (tone, hook strength, problem clarity, claims, etc.) with a pass/needs-improvement table before final sign-off.

6. Results
The system generated:

10 short-form video hooks across 10 different angles
5 full UGC advertising concepts, each with hook, problem, story, solution, benefit, CTA, visuals, and on-screen text
10 CTAs (soft, direct, urgency, and local)
5 Instagram captions with CTAs and hashtags
3 platform-specific adaptations of the strongest concept (Instagram Reels, YouTube Shorts, Paid Social)

7. Tools
Claude (Anthropic) for prompt design and content generation, and GitHub for version control and documentation of the project.

8. Reusability
The framework isn't hardcoded to Mozambik — the business profile (name, location, audience, product, unique value, tone, platforms, CTA) sits at the top as a swappable variable block. To reuse the system for a different business, you only need to replace those variables; the prompt logic, structure, constraints, and QC checklist stay exactly the same, meaning the same pipeline can generate a full UGC ad system for any local business without rebuilding the prompts from scratch.
