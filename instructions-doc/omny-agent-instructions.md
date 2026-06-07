OMNY — Design Iteration System

**Agent Instructions & Workflow Rules**

For AI agents, designers, and the lead. This document defines the folder structure, phase rules, file requirements, collaboration controls, and session hygiene for all design work on the Omny repo.

**Repo:** Omny

**Platforms:** Cursor, Claude Code, GitHub (Figma MCP, agentation plugin & superpowers plugin)

**Design output:** HTML/CSS (may migrate to Next.js — folder structure unchanged)

**Stakeholder access:** *TBD*

**1. Purpose and core principle**

This system exists to solve one problem: context leak. In a design process involving multiple people, multiple tools, and multiple AI sessions, critical thinking — decisions made, approaches rejected, feedback received — disappears between sessions. This system prevents that by making context storage a structural requirement, not an afterthought.

Every file created in this system serves the context loop. If a file does not contribute to that loop, it does not belong in the repo.

The anchor for every decision in this workflow is: more UX approaches explored, stronger product thinking, faster prototyping. When something in the process conflicts with those goals, the process should change.

**2. Repo and folder structure**

**2.1 Top-level structure**

Every feature on the Omny repo lives in its own top-level folder. The structure below is fixed and must not be changed.

> Omny/  
> └── dsp-reporting/ ← feature folder (example)  
> |  ├── context/ ← Phase 1: raw inputs and global docs  
> |  ├── concepts/ ← Phase 2 & 3: concept work and iterations  
> |  ├── showcase/ ← Phase 4: client-facing wrapper (to be built)  
> |  ├── INDEX.md ← project-level map and status  
> |  └── TAGS.md ← canonical tag definitions, lead-maintained

**2.2 Context folder**

> context/  
> ├── raw/  
> │ ├── meeting-transcript.md  
> │ └── notion-export.md  
> ├── feature-brief.md  
> ├── sitemap.md ← or feature-map.md depending on scope  
> └── userflow.md ← or use-cases.md depending on scope  

The raw/ folder holds original source material, untouched. Nothing in raw/ is ever edited. The three output documents — feature-brief, sitemap, userflow — are derived from raw/ by the lead and represent the converted, structured context for the entire feature.

**2.3 Concepts folder**

> concepts/  
> ├── concept-01/  
> │ ├── INDEX.md ← concept-level map and verification status  
> │ ├── concept-doc.md ← approach, rationale, design plan  
> │ ├── references.md ← Figma MCP pulls, inspo, reference links  
> │ ├── meta.json ← tags, author, status  
> │ ├── change-logs/  
> │ │ ├── DD-MM-YY.md  
> │ │ └── DD-MM-YY.md  
> │ └── iterations/  
> │ ├── iteration-01/  
> │ │ ├── INDEX.md  
> │ │ ├── meta.json  
> │ │ └── \[design files — HTML/CSS\]  
> │ └── iteration-02/  
> │ ├── INDEX.md  
> │ ├── meta.json  
> │ └── \[design files — HTML/CSS\]  
> ├── concept-02/  
> │ └── \[same structure\]  
> └── concept-selection.md ← lead writes this after all concepts are reviewed

Minimum 2 concepts per feature. No fixed maximum. The number is decided by the lead at project kickoff and documented in INDEX.md.

**3. File definitions**

Every file in this system has a fixed purpose. No file should contain content that belongs to another file.

|                      |                                                                                                                                                                                                                        |
|----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **File**             | **Purpose**                                                                                                                                                                                                            |
| feature-brief.md     | Single source of truth for the problem being solved. Defines the feature, the user, the constraints, and what success looks like. Every designer and AI agent reads this before starting any work.                    |
| sitemap.md           | Structural map of the product or feature scope. Prevents designers from going out of scope mid-iteration.                                                                                                              |
| userflow.md          | User journey and use cases. Defines the flows that design must support.                                                                                                                                                |
| concept-doc.md       | Written before any design starts. Contains: the approach, the logic behind it, what it prioritises, what it deliberately excludes, and the design plan. This is where product thinking lives.                          |
| references.md        | Figma MCP pulls, inspiration links, competitor references, and visual direction notes. Updated as references are added during concept work.                                                                            |
| meta.json            | Machine-readable identity card for the concept or iteration. Contains tags, author, status, and lineage fields. Controls what appears in the showcase.                                                                 |
| change-log (dated)   | Running record of what changed in a session and why. One file per working day, named YYYY-MM-DD.md. Updated during the session, not after. Three sections only: what was worked on, what changed, decisions locked in. |
| concept-selection.md | Written by the lead after all concepts are reviewed. Explains which concept moves into full iteration first, why, and the status of all others. One paragraph minimum.                                                 |
| INDEX.md             | Map and status tracker for the folder it lives in. Updated after every significant action. See Section 5 for structure.                                                                                                |
| TAGS.md              | Defines all valid tags used in meta.json. Lead-maintained. No tag may be used in meta.json unless it is defined here first.                                                                                            |

**4. Phases and control**

**4.1 Overview**

The workflow has four phases. Nobody moves to the next phase without the lead merging the current phase into main. This is a hard gate, not a guideline.

|                              |                 |                  |
|------------------------------|-----------------|------------------|
| **Phase**                    | **Who creates** | **Who approves** |
| 1 — Context setup            | Lead            | Lead             |
| 2 — Concept development & iterations    | Designers       | Lead             |
| 3 — Showcase / client review | Lead            | Lead             |

**4.2 Phase 1 — Context setup**

The lead converts raw inputs (meeting transcripts, Notion exports) into the three context documents: feature-brief.md, sitemap.md, userflow.md. These are committed to /context/ and merged into main before any concept work begins.

**Phase gate — nothing in /concepts/ may be created until these are merged:**

- feature-brief.md exists and all sections are filled

- sitemap.md exists

- userflow.md exists

- Lead approval commit exists on main

**4.3 Phase 2 — Concept development**

Each designer creates their concept folder(s) on a short-lived branch. The number of concepts is defined by the lead at kickoff. concept-doc.md must be written and approved before any design files are created.

**Phase gate — before any iteration work begins on a concept:**

- concept-doc.md exists with all sections filled

- references.md exists

- meta.json exists with a valid tag from TAGS.md

- At least one change-log entry exists in /change-logs/

- INDEX.md is up to date

- Lead has approved the concept branch PR

After all concepts are reviewed internally, the lead writes concept-selection.md before Phase 3 begins.

**4.4 Phase 3 — Iterations**

Visual and layout iterations live inside each concept folder under /iterations/. Each iteration is a separate folder. Design files (HTML/CSS or future Next.js) live directly inside the iteration folder — nowhere else.

**Phase gate — before an iteration is ready for lead review:**

- Design files exist in the iteration folder

- meta.json is present with a valid tag

- INDEX.md for the iteration exists and is filled

- A change-log entry for this session exists

- Commit message follows the template in Section 6

**4.5 Phase 4 — Showcase**

The showcase is a pill-tab wrapper that reads meta.json tags to surface concept and iteration options to the client. It is built and maintained by the lead only. Tag changes in meta.json control what appears — no files are moved or deleted to change the client view.

The showcase wrapper is yet to be built. Until it exists, the lead manages client presentations directly from the repo structure.

**5. INDEX.md structure**

INDEX.md files exist at three levels: project root, each concept folder, and each iteration folder. They are the first file any agent or designer reads when starting a session. They must always reflect the current state of their folder.

**5.1 Project-level INDEX.md**

> \# Omny / \[feature-name\]  
>   
> Lead: \[name\]  
> Status: \[active / in-review / complete\]  
> Last updated: YYYY-MM-DD  
>   
> \## Phase status  
> - \[x\] Phase 1 — Context setup  
> - \[x\] Phase 2 — Concept development  
> - \[ \] Phase 3 — Iterations  
> - \[ \] Phase 4 — Showcase  
>   
> \## Concepts  
> \| Concept \| Designer \| Status \| Notes \|  
> \|---------\|----------\|--------\|-------\|  
> \| concept-01 \| \[name\] \| in-iteration \| moving forward \|  
> \| concept-02 \| \[name\] \| parked \| strong, revisit after concept-01 \|  
>   
> \## Open items  
> - \[ \] \[anything blocking or pending\]

**5.2 Concept-level INDEX.md**

> \# \[feature-name\] / concept-\[NN\]  
>   
> Author: \[name\]  
> Status: \[in-progress / ready-for-review / approved / parked\]  
> Last updated: YYYY-MM-DD  
>   
> \## File checklist  
> - \[x\] concept-doc.md  
> - \[x\] references.md  
> - \[x\] meta.json  
> - \[x\] change-logs/YYYY-MM-DD.md  
>   
> \## Iterations  
> \| Iteration \| Status \| Notes \|  
> \|-----------\|--------\|-------\|  
> \| iteration-01 \| archived \| first visual pass \|  
> \| iteration-02 \| current \| tighter layout \|  
>   
> \## Open items  
> - \[ \] \[anything pending for this concept\]

**5.3 Iteration-level INDEX.md**

> \# \[feature-name\] / concept-\[NN\] / iteration-\[NN\]  
>   
> Author: \[name\]  
> Status: \[in-progress / ready-for-review / approved / archived\]  
> Last updated: YYYY-MM-DD  
>   
> \## File checklist  
> - \[x\] meta.json  
> - \[x\] \[design file name\]  
>   
> \## What this iteration shows  
> \[One or two sentences\]  
>   
> \## Open items  
> - \[ \] \[anything pending\]

**6. Commit message template**

Every commit that involves a design or documentation change must follow this template. Single-line commits are only acceptable for trivial fixes (typo, formatting). The agent will reject any substantive commit that does not use this format and prompt the designer to rewrite it.

> type: short summary of what changed (max 10 words)  
>   
> What changed:  
> - \[specific change 1\]  
> - \[specific change 2\]  
>   
> Why:  
> - \[reason behind the change\]  
>   
> Concept: \[concept-01 / concept-02 / ...\]  
> Phase: \[context / concepts / iterations / showcase\]  
> Status: \[in-progress / ready-for-review / approved\]

Valid commit types:

- **add:** new file, concept, or iteration

- **refine:** visual or design update within an existing iteration

- **fix:** correcting something wrong

- **doc:** documentation only — change-log, concept-doc, INDEX updates

- **meta:** meta.json or TAGS.md updates only

The agent auto-fills Concept and Phase based on the folder being committed. The designer fills in what changed and why.

**7. Branching rules**

Main is the only long-lived branch. Every unit of work gets its own short-lived branch, merged, then deleted. Direct pushes to main are forbidden.

|                                   |                                                                           |
|-----------------------------------|---------------------------------------------------------------------------|
| **Branch type**                   | **Naming pattern**                                                        |
| New concept or iteration          | add/\[feature\]-concept\[NN\] or add/\[feature\]-concept\[NN\]-iter\[NN\] |
| Metadata or tag update only       | update/\[short-desc\]                                                     |
| Exploratory, not yet an iteration | explore/\[short-desc\] — deleted when exploration ends                    |
| Frozen client snapshot            | stakeholder-review-YYYY-MM-DD — never modified after creation             |

No personal branches. No designer/wip or designer/scratch branches. If a designer needs scratch space, they use explore/ and delete it when done.

**8. Tags and meta.json**

**8.1 Canonical tags**

Only tags defined in TAGS.md may be used. Tags are case-sensitive and hyphenated. Adding a new tag requires a PR to TAGS.md first.

|                    |                                                   |
|--------------------|---------------------------------------------------|
| **Tag**            | **Meaning**                                       |
| internal-review    | Under team review, not yet client-ready           |
| stakeholder-review | Currently in the client-facing showcase view      |
| current            | Currently recommended version within its concept  |
| archived           | Superseded, kept for history, dimmed in full view |
| experimental       | Exploratory, not for formal review                |

**8.2 meta.json required fields**

> {  
> "id": "concept-\[NN\]-iter\[NN\]",  
> "concept": "concept-\[NN\]",  
> "iteration": "iteration-\[NN\]",  
> "label": "\[short human-readable title\]",  
> "author": "\[name\]",  
> "createdAt": "YYYY-MM-DD",  
> "tags": \["internal-review"\],  
> "description": "\[one sentence on what this shows\]",  
> "supersedes": null,  
> "presentationGroup": null,  
> "changesFromPrevious": \[\],  
> "feedbackAddressed": \[\]  
> }

presentationGroup is immutable once set. Once an iteration was shown in a client review, that field stays permanently — even if the iteration is later archived.

**9. Agent instructions**

This section is written directly for the AI agent. Read this section at the start of every session.

**9.1 Session start — always do this first**

- Read /context/feature-brief.md

- Read the relevant concept-doc.md for the concept being worked on

- Read the latest change-log entry in /change-logs/

- Read the project-level INDEX.md and the concept-level INDEX.md

- Check if any phase gates are unmet — if yes, flag before proceeding

Do not begin any design or documentation work until all four files have been read and the phase gate check is complete.

**9.2 Session start — status check**

At the start of every session, run this check automatically without being asked:

- Compare last modified dates of design files in /iterations/ against the most recent change-log date. If design files were modified more recently than the last change-log, flag this immediately: which files, which concept, how many days behind.

- Check for any INDEX.md files that have not been updated since the last commit. List them.

- Check for any meta.json files missing required fields. List which fields are missing and in which file.

- Report: what phase the project is in, what is complete, what is in progress, what is blocking.

**9.3 Phase gate enforcement**

Before moving forward at any phase transition, run the appropriate checklist from Section 4. If any condition fails:

- List every missing item specifically — file name, folder path, which section is empty

- Do not proceed to the next phase

- Notify the designer of exactly what needs to be completed

Phase gates are not optional.

**9.4 During-session triggers**

These actions trigger automatic checks without waiting to be asked:

- **Design file modified or created:** immediately check if a change-log entry for today exists in /change-logs/. If not, prompt the designer to create one before continuing.

- **Any git add or pre-push action:** verify a commit message exists and follows the template in Section 6. If it doesn't exist or doesn't follow the format, reject and prompt the designer to write one. Do not push without it.

- **Concept-doc.md being written or updated:** check that all sections are present and none are empty before the file is committed. List any empty sections.

- **New iteration folder created:** verify INDEX.md and meta.json are created at the same time. If either is missing, flag before any design files are added.

- **Any PR opened:** verify the branch name follows the naming convention in Section 7. Flag if it doesn't.

**9.5 End of session — always do this last**

Run this checklist at the end of every session, automatically, without being asked:

- Were any design files modified this session? If yes, does a change-log entry for today exist? If not, create it now or prompt the designer to fill it.

- Are there uncommitted changes? If yes, prompt for a commit message using the template. Do not leave uncommitted work.

- Is every INDEX.md reflecting the current state of its folder? If not, update now.

- Are there any files with sections that were supposed to be filled this session but are still empty? List them.

- Is the project-level INDEX.md current? Update if needed.

**The session is not complete until this checklist passes.**

**9.6 What the agent must never do**

- Never push directly to main

- Never create files outside the defined folder structure

- Never skip updating INDEX.md after a file is created or changed

- Never proceed past a phase gate if any condition is unmet

- Never create a personal branch (designer/wip, designer/scratch, etc.)

- Never rename or delete a merged iteration folder

- Never use a tag in meta.json that is not defined in TAGS.md

- Never leave a session with uncommitted changes

- Never accept a commit message that does not follow the template for substantive commits

**10. Collaboration rules**

**10.1 Designer responsibilities**

- Create concept and iteration folders following the structure in Section 2

- Write concept-doc.md before creating any design files

- Update change-logs during the session, not after

- Tag the lead as reviewer on every PR

- When building on another designer's concept, create a new iteration that supersedes the original — never edit the original folder

- When superseding another designer's work, set the supersedes field in meta.json and credit the original author in the author field

**10.2 Lead responsibilities**

- Owns and approves all Phase 1 context documents

- Approves all concept PRs before Phase 3 begins

- Writes concept-selection.md after concept review

- Approves all iteration PRs before they are tagged stakeholder-review

- Is the only person who modifies stakeholder-review and presentationGroup tags

- Creates the frozen stakeholder-review-YYYY-MM-DD branch before every client presentation

- Maintains TAGS.md

- Reviews INDEX.md accuracy as part of every PR review

**10.3 Feedback handling**

- Internal feedback that changes the design creates a new iteration — do not edit the existing iteration folder

- Client feedback creates a new iteration with the feedbackAddressed field in meta.json populated with the specific feedback being responded to

- Feedback that does not result in a change is still recorded — as a comment on the PR or in the change-log — so the reasoning is preserved

**11. Showcase**

The showcase is a pill-tab interface that switches between concepts and their iterations. It reads meta.json tags to determine what appears. It is built and controlled by the lead.

Current status: to be built. Until it exists, client presentations are run directly from the repo.

When built, the showcase must:

- Read tags from meta.json to determine default view

- Show iterations within each concept as navigable tabs or pills

- Allow a full-history toggle that reveals all iterations including archived ones

- Never require file movement to change what is visible — all curation is via tags only

**12. Hygiene rules**

- Delete branches after merge — enable auto-delete on GitHub

- Keep PRs scoped to one concept or one iteration. A PR open more than a week should be split or closed

- Do not accumulate draft PRs. If exploration is not going forward, close the draft and delete the branch

- Large binary files use Git LFS from day one

- Do not rename merged folders — other files reference them via supersedes and linked PRs

- Design files live only inside their iteration folder — never at the concept root level or anywhere outside the defined structure

**13. Quick reference**

For the designer: read this before starting any session.

|                                     |                                                                                              |
|-------------------------------------|----------------------------------------------------------------------------------------------|
| **Situation**                       | **What to do**                                                                               |
| Starting a new session              | Read feature-brief → concept-doc → latest change-log → INDEX.md                              |
| Starting a new concept              | Create concept folder, write concept-doc.md first, get lead approval before any design files |
| Starting a new iteration            | Create iteration folder with INDEX.md and meta.json at the same time as design files         |
| Made design changes                 | Update change-log for today before ending session                                            |
| Ready to commit                     | Use commit message template — agent will reject non-compliant messages                       |
| Ready for lead review               | Open PR, check all phase gate conditions, tag lead as reviewer                               |
| Responding to feedback              | New iteration folder, populate feedbackAddressed in meta.json                                |
| Building on another designer's work | New iteration, set supersedes, credit original author, tag them as reviewer                  |
| Something feels off                 | Run git status first. Then read INDEX.md. Then ask.                                          |
