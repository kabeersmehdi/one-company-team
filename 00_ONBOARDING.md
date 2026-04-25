# 00_ONBOARDING.md
**One-Company-Skill · Company Setup Interview**

---

## Purpose

This is the first skill that runs when setting up your One-Company-Skill system.  
It conducts a structured interview across 3 phases and outputs a completed `company-profile.json` that every officer and sub-skill in the system reads from.

**Do not skip or partially complete this file.** Every officer skill depends on the output it generates.

---

## How to Use This File

1. Open a new Claude conversation (Projects recommended).
2. Paste this entire file as your first message, or attach it as a document.
3. Tell Claude: *"Run the One-Company-Skill onboarding interview."*
4. Answer each question fully — the richer your answers, the better every downstream skill performs.
5. At the end, Claude will output your completed `company-profile.json`. Save it to the root of your one-company-skill folder.

---

## System Prompt (paste this into Claude's system prompt or Project instructions)

```
You are running the One-Company-Skill Onboarding Interview for a company setting up their AI org structure.

Your job is to conduct a structured 3-phase interview and then output a completed company-profile.json file at the end.

Rules:
- Ask one phase at a time. Wait for the user's full response before moving to the next phase.
- Ask clarifying follow-up questions if an answer is vague or too short to be actionable.
- Be conversational but efficient — this is a setup interview, not a coaching session.
- When you reach the end of Phase 3, synthesize all answers into the company-profile.json schema provided at the bottom of this file. Output it as a clean JSON code block.
- Do not hallucinate officer profiles or department details. Only use what the user tells you.
- If the user skips a question, mark that field as null in the JSON — do not guess.
```

---

## Phase 1 — Company Snapshot

*Goal: Establish the foundational context every skill will inherit.*

Ask the user the following questions. You may ask them all at once or one by one depending on user preference.

```
PHASE 1 OF 3 — Company Snapshot

1. What is your company's full name and any common shorthand or abbreviation you use internally?

2. What industry are you in, and how would you describe what you do in one sentence — the way you'd explain it to someone at a dinner party, not a pitch deck?

3. How many full-time employees do you have? Include contractors if they're long-term.

4. What are the 3 most critical business functions your company performs every week?
   (Examples: client delivery, sales outreach, financial reporting, content production)

5. What tools and platforms does your team use daily?
   (Examples: Notion, Slack, HubSpot, Figma, QuickBooks, Salesforce, Linear, etc.)

6. Describe your company's communication tone and culture in 3 words or a short sentence.
   (Examples: "fast and direct," "warm but professional," "data-first, never fluffy")

7. Optional but powerful — paste 1–2 examples of your actual work output.
   This could be a past email, a project brief, a proposal, or a client update.
   This calibrates every skill's tone and judgment to match your real standards.
```

---

## Phase 2 — Officer Selection

*Goal: Activate only the officers that are relevant to this company. Unused officers create noise.*

Present the following roster to the user. They confirm which to activate, deactivate, or customize.

```
PHASE 2 OF 3 — Officer Selection

Below is the full default C-Suite roster. For each one, tell me:
  [ACTIVE]   — This role exists and makes real decisions at your company
  [INACTIVE] — This role doesn't apply right now (we'll keep the template, just won't activate it)
  [CUSTOM]   — You want to rename, combine, or replace this role with something more specific to your org

------------------------------------------------------------
OFFICER                     DEFAULT STATUS    YOUR CHOICE
------------------------------------------------------------
CEO (Chief Executive Officer)         ACTIVE    [ ]
COO (Chief Operating Officer)         ACTIVE    [ ]
CFO (Chief Financial Officer)         ACTIVE    [ ]
CTO (Chief Technology Officer)        ACTIVE    [ ]
CIO (Chief Information Officer)       INACTIVE  [ ]
CMO (Chief Marketing Officer)         ACTIVE    [ ]
CHRO (Chief Human Resources Officer)  ACTIVE    [ ]
CCO (Chief Compliance Officer)        INACTIVE  [ ]
CDO (Chief Data Officer)              INACTIVE  [ ]
CSO (Chief Sustainability Officer)    INACTIVE  [ ]
President                             INACTIVE  [ ]
General Counsel                       ACTIVE    [ ]
------------------------------------------------------------

If you marked any as [CUSTOM], answer these for each custom officer:
  a. What is their title?
  b. Which departments do they own or oversee?
  c. Who do they report to?
  d. What makes this role different from the standard options above?
```

---

## Phase 3 — Officer Deep-Dive

*Goal: Build a detailed profile for each ACTIVE officer so their skill file has real decision-making context.*

For each officer the user marked ACTIVE, run through the following questions.  
Tell the user upfront: *"We'll go through each active officer one at a time. The more specific you are, the better the AI will replicate their judgment."*

```
PHASE 3 OF 3 — Officer Deep-Dive
[Repeat this block for each ACTIVE officer]

--- [ OFFICER TITLE ] ---

a. Is this a real person at your company or a purely AI-modeled role?
   If real → What is their name? (Optional, used for personalization only)

b. What are this officer's top 3 decisions or tasks they handle every single week?

c. What is their single biggest bottleneck or recurring problem right now?

d. What would they NEVER approve or do without escalating to someone above them?
   (This defines the escalation trigger for their skill)

e. What does "excellent work" look like for this officer's domain?
   Give a specific example if you can.

f. What is their communication style?
   (Examples: "short bullets, no fluff," "detailed narrative with data," "visual and example-driven")

g. What tools does this officer or their team use most?

h. Are there any hard rules, non-negotiables, or red lines for this role?
   (Examples: "never discount below 20% margin," "always CC legal on client contracts")

i. Optional: Paste a real example of output from this person or their team.
   (A past decision memo, email, report, or brief — this is the single biggest quality lever)
```

---

## Output Schema

After completing all 3 phases, generate the following JSON exactly. Use `null` for any field the user skipped.

```json
{
  "meta": {
    "version": "1.0",
    "generated_by": "00_ONBOARDING.md",
    "last_updated": "[DATE]",
    "status": "active"
  },

  "company": {
    "name": null,
    "shorthand": null,
    "industry": null,
    "description_plain_english": null,
    "size_employees": null,
    "critical_functions": [],
    "tools": [],
    "tone": null,
    "sample_work_provided": false
  },

  "officers": {
    "active": [],
    "inactive": [],
    "custom": [
      {
        "title": null,
        "alias": null,
        "owns_departments": [],
        "reports_to": null,
        "differentiator": null
      }
    ]
  },

  "officer_profiles": {
    "CEO": {
      "real_person": null,
      "name": null,
      "top_weekly_decisions": [],
      "biggest_bottleneck": null,
      "escalation_triggers": [],
      "excellence_standard": null,
      "communication_style": null,
      "tools": [],
      "non_negotiables": [],
      "sample_output_provided": false
    },
    "COO": {
      "real_person": null,
      "name": null,
      "top_weekly_decisions": [],
      "biggest_bottleneck": null,
      "escalation_triggers": [],
      "excellence_standard": null,
      "communication_style": null,
      "tools": [],
      "non_negotiables": [],
      "sample_output_provided": false
    },
    "CFO": {
      "real_person": null,
      "name": null,
      "top_weekly_decisions": [],
      "biggest_bottleneck": null,
      "escalation_triggers": [],
      "excellence_standard": null,
      "communication_style": null,
      "tools": [],
      "non_negotiables": [],
      "sample_output_provided": false
    },
    "CTO": {
      "real_person": null,
      "name": null,
      "top_weekly_decisions": [],
      "biggest_bottleneck": null,
      "escalation_triggers": [],
      "excellence_standard": null,
      "communication_style": null,
      "tools": [],
      "non_negotiables": [],
      "sample_output_provided": false
    },
    "CIO": {
      "real_person": null,
      "name": null,
      "top_weekly_decisions": [],
      "biggest_bottleneck": null,
      "escalation_triggers": [],
      "excellence_standard": null,
      "communication_style": null,
      "tools": [],
      "non_negotiables": [],
      "sample_output_provided": false
    },
    "CMO": {
      "real_person": null,
      "name": null,
      "top_weekly_decisions": [],
      "biggest_bottleneck": null,
      "escalation_triggers": [],
      "excellence_standard": null,
      "communication_style": null,
      "tools": [],
      "non_negotiables": [],
      "sample_output_provided": false
    },
    "CHRO": {
      "real_person": null,
      "name": null,
      "top_weekly_decisions": [],
      "biggest_bottleneck": null,
      "escalation_triggers": [],
      "excellence_standard": null,
      "communication_style": null,
      "tools": [],
      "non_negotiables": [],
      "sample_output_provided": false
    },
    "CCO": {
      "real_person": null,
      "name": null,
      "top_weekly_decisions": [],
      "biggest_bottleneck": null,
      "escalation_triggers": [],
      "excellence_standard": null,
      "communication_style": null,
      "tools": [],
      "non_negotiables": [],
      "sample_output_provided": false
    },
    "CDO": {
      "real_person": null,
      "name": null,
      "top_weekly_decisions": [],
      "biggest_bottleneck": null,
      "escalation_triggers": [],
      "excellence_standard": null,
      "communication_style": null,
      "tools": [],
      "non_negotiables": [],
      "sample_output_provided": false
    },
    "CSO": {
      "real_person": null,
      "name": null,
      "top_weekly_decisions": [],
      "biggest_bottleneck": null,
      "escalation_triggers": [],
      "excellence_standard": null,
      "communication_style": null,
      "tools": [],
      "non_negotiables": [],
      "sample_output_provided": false
    },
    "President": {
      "real_person": null,
      "name": null,
      "top_weekly_decisions": [],
      "biggest_bottleneck": null,
      "escalation_triggers": [],
      "excellence_standard": null,
      "communication_style": null,
      "tools": [],
      "non_negotiables": [],
      "sample_output_provided": false
    },
    "General_Counsel": {
      "real_person": null,
      "name": null,
      "top_weekly_decisions": [],
      "biggest_bottleneck": null,
      "escalation_triggers": [],
      "excellence_standard": null,
      "communication_style": null,
      "tools": [],
      "non_negotiables": [],
      "sample_output_provided": false
    }
  },

  "departments": {
    "active": [],
    "inactive": [],
    "ownership_map": {
      "marketing": "CMO",
      "creative": "CMO",
      "finance": "CFO",
      "technology": "CTO",
      "it_security": "CIO",
      "people_ops": "CHRO",
      "legal_compliance": ["CCO", "General_Counsel"],
      "data_analytics": "CDO",
      "sustainability": "CSO",
      "operations": "COO",
      "client_services": "COO"
    }
  },

  "escalation_chains": {
    "default": ["sub_skill", "officer", "COO", "CEO"],
    "legal": ["nda_handler", "contract_reviewer", "General_Counsel", "CEO"],
    "financial": ["budget_tracker", "CFO", "CEO"],
    "people": ["hr_sub_skill", "CHRO", "CEO"],
    "technical": ["tech_sub_skill", "CTO", "COO", "CEO"],
    "custom": []
  }
}
```

---

## Notes for Maintainers

- **Re-run this onboarding anytime** your org structure changes — new hires at the officer level, new tools, acquisitions, or rebrands.
- **`sample_output_provided: true`** flags which officer profiles have real calibration data. Prioritize updating those first if quality degrades.
- **Inactive officers** are never deleted — they remain in the schema with `null` fields so you can activate them without re-running the full interview.
- **Custom officers** follow the same deep-dive format as standard officers. Their `alias` field is used to name their `.md` skill file (e.g., `CCO_creative.md`).
- This file lives at the **root of your one-company-skill folder** and is the single source of truth for the entire system.

---

*Part of the One-Company-Skill system · v1.0*
