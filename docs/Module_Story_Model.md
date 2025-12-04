Module 1 — Story Model (Text Generation)
MMCE – Multi-Model Creativity Engine

1. Purpose of This Module

The Story Model is responsible for generating creative narrative text.
It operates in two stages:

Planning Stage

Generate narrative metadata (tone, style, target age)

Generate scene outline (titles, sequence)

Writing Stage

Generate detailed story text for each scene

Ensures flow, continuity, and child-friendly style

This module must be independent so it can be replaced or upgraded later.

2. Requirements
   Functional Requirements

Accept a user instruction (e.g., “bedtime story about a shy dragon”).

Generate a structured outline with a configurable number of scenes.

Generate full scene text (~80–150 words per scene).

Maintain narrative consistency (characters, tone, pacing).

Produce text suitable for children's stories (safe & simple language).

Return structured output in the MMCE object format.

Non-Functional Requirements

Modular — plug-and-play for different LLMs (OpenAI, HF, local).

Deterministic fallback (dummy mode) for offline development.

Extendable for future fine-tuned story models.

Efficient prompt design to reduce token usage.

3. Inputs & Outputs
   Inputs

user_prompt: description of story request

num_scenes: default 5 (or agent-decided later)

style: e.g., “bedtime story”, “adventure”, “cute cartoon”

tone: e.g., “gentle”, “playful”, “uplifting”

target_age: e.g., “5–7 years old”

Outputs
A. Story Metadata

Title

Tone

Style

Target age

Scene count

B. Scene Objects (Per Scene)

Scene title

Scene description (optional future feature)

Full text paragraph

Thematically structured content

Clean text format for TTS

4. Components of the Story Model
   4.1 Story Planner

Generates:

Story metadata

Scene titles

Basic flow

Example outline:

Scene 1 – The Shy Dragon in the Forest  
Scene 2 – The First Attempt at Making Friends  
Scene 3 – A Helpful Fairy Appears  
Scene 4 – The Dragon Saves the Day  
Scene 5 – Everyone Becomes Friends

4.2 Story Writer

For each scene, generates:

80–150 words

Child-friendly language

Consistent characters

Smooth transitions

5. Prompting Rules (LLM Agnostic)
   Outline Prompt Guidelines

The planner prompt must:

Identify story structure

Break plot into scenes

Stay consistent with tone and age

Scene Writing Prompt Guidelines

Reinforce previous scenes

Bring character continuity

Use simple vocabulary (age-appropriate)

Avoid violence or negative themes

End scenes with positive emotional tone

6. Output Format Specification

Story Model must return a Story object with:

story.metadata
story.scenes[i].title
story.scenes[i].text

These objects must match MMCE’s data structures to support:

Image prompt creation

TTS generation

Music mood mapping

PDF/MP4 export pipelines

7. Success Criteria

The module is considered successfully implemented when:

It generates a structured outline

It produces high-quality story text per scene

The tone matches the user request

Story flows logically scene to scene

The model works even without the agent

It can plug into later MMCE modules

8. Future Enhancements

Fine-tuning a small story model on children's literature

Character embedding system for consistent style

Scene descriptions for more accurate image prompts

Adjustable reading difficulty

Story branching for interactive storytelling
