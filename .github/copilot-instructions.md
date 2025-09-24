---
applyTo: '**/*.ts'
---
---
title: Enduro JS project assistant instructions
applyTo: '**/*.*'
description: |
	These instructions guide automated assistants that edit or generate code and
	responses for the Enduro (Atari-like) JavaScript project in this workspace.
	They emphasize consistent code style, localized conversation behavior, and
	brief project context so responses and code changes align with the user's
	expectations.

rules:
	- indentation: 'Use 2 spaces for indentation in all generated or modified files.'
	- line_length: 'Wrap or avoid lines longer than 120 characters where practical.'
	- code_language: 'When possible, write code, logic, variable names, and code
		comments in English to maintain consistency across contributors and tools.'
	- conversation_localization: |
		Assistant responses must match the language of the user's instructions. If
		the user writes instructions in Portuguese, reply in Portuguese. If the
		user writes in English, reply in English. For mixed-language inputs, prefer
		the language of the most recent instruction message.
	- file_editing_scope: |
		Prefer minimal, well-scoped edits. When changing or creating runnable code,
		include small verification steps (e.g., quick static check or run snippet)
		and keep changes backward-compatible when possible.
	- comments_and_docs: 'Keep user-visible documentation brief and in the user's
		language. Inline code comments should be in English unless the instruction
		explicitly requests otherwise.'

project_context: |
	This workspace contains a single-file web game inspired by Atari's Enduro
	implemented using HTML5 Canvas and vanilla JavaScript. The primary file is
	`index.html`, which contains HTML, CSS, and an embedded JavaScript game loop.
	The assistant should assume the following high-level goals when editing
	project files:
		- Keep the game single-file by default unless the user asks to split it.
		- Preserve a compact build-free structure (no external bundlers) unless
			requested by the user.
		- Favor readability and small helper functions; keep functions short and
			focused.

examples_and_style:
	- 'Use descriptive variable and function names (player, opponents, spawnOpponent, update, render).'
	- 'Prefer small helper functions over very large monolithic functions.'
	- 'When adding new files, include a short README or usage note.'

assistant_behavior:
	- 'Before editing any file, summarize the planned change and add a one-line
		todo to the session plan.'
	- 'Mark one todo `in-progress` before making changes and mark it `completed`
		immediately after making the change.'
	- 'Run a quick verification step after edits: a lint/parse check or a short
		smoke test (for JS files, ensure no syntax errors when parsed by the
		browser).' 
	- 'Keep changes small and reversible. If a large rewrite is necessary, ask
		the user before proceeding.'
  - conversation_localization: |
    Keep assistant responses in the language of the user's instructions. If the user
    writes instructions in Portuguese, reply in Portuguese. If the user writes in
    English, reply in English. For mixed-language inputs, prefer the language of english.

follow_up:
	- 'If users ask for gameplay tuning (physics, speed, AI), propose a small
		set of measurable changes and implement them incrementally with tests.'

---
