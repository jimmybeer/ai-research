# AI Prompt Playbook  
*(Inspired by the “You’re Not Behind Yet” style of learning AI)*

---

## 1. Why Prompts Matter

Modern AI tools (like ChatGPT, Codex CLI, and other LLMs) are only as useful as the tasks you give them.

- You haven’t “missed the AI wave”; we’re still early.
- You don’t need to be highly technical to get value.
- The main skill is **structuring your thinking as prompts**.

This playbook is a practical guide to:
- Understand how to work with AI.
- Turn your existing workflows into AI-boosted workflows.
- Use reusable prompt patterns (“prompt library”) instead of starting from scratch every time.

---

## 2. Three Ways to Use AI

### 2.1 Everyday Explorer

**Who:** Knowledge workers, students, self-learners.  
**Goal:** Use AI as an intelligent assistant.

Typical tasks:
- Explaining concepts in different ways.
- Summarising documents/emails.
- Drafting and redrafting text.
- Brainstorming ideas.

**Key skills:**
- Giving context (who, what, why).
- Specifying audience and tone.
- Asking AI to check your understanding.

---

### 2.2 Power User

**Who:** Professionals who want serious productivity gains.  
**Goal:** Build **repeatable workflows** using AI.

Typical tasks:
- Weekly/monthly reports.
- Requirements breakdowns and traceability checks.
- Content pipelines (research → outline → draft → edit).
- Data → analysis → narrative reports.

**Key skills:**
- Breaking work into steps.
- Designing prompt templates for each step.
- Saving and reusing your best prompts (prompt library).
- Combining tools (LLM + search + local files + scripts).

---

### 2.3 Builder

**Who:** People who want to create tools / products / automations.  
**Goal:** Build systems that use AI under the hood.

Typical tasks:
- Agent workflows (e.g. Codex CLI tasks and tools).
- Code generation and refactoring.
- Command-line or web tools that call AI to do subtasks.
- Glueing together scripts, APIs, and AI.

**Key skills:**
- “Vibe coding”: describing what you want, letting AI draft code.
- Turning vague product ideas into specific interfaces and behaviours.
- Designing data flows: input → transform → output → feedback.

---

## 3. Core Prompting Principles

### 3.1 Use the R-GACIF Pattern

Before sending a prompt, try to include:

1. **R**ole – who the AI should “pretend” to be  
2. **G**oal – what you want as the final outcome  
3. **A**udience – who the result is for & their expertise  
4. **C**ontext – relevant background and constraints  
5. **I**nput – the actual material (text, code, data, etc.)  
6. **F**ormat – how you want the answer structured

A generic skeleton:

> Act as a **[role]**.  
> Your goal is to **[goal]**.  
> The audience is **[audience]**.  
> Here is the context: **[context]**.  
> Here is the input:  
> ```  
> [input]  
> ```  
> Follow these constraints: **[constraints]**.  
> Return the answer in **[format]**.  
> At the end, **[next step – e.g. ask me 3 clarifying questions]**.

---

### 3.2 Think in Iterations, Not Single Prompts

- First pass: rough, broad, exploratory.
- Second pass: refine or narrow (“focus on X only”, “remove Y”).
- Third pass: reformat or adapt (“make it a checklist / table / JSON / requirements list”).

Treat AI like a collaborator:
- “That’s close; now tighten the argument.”
- “Rewrite for a non-technical audience.”
- “Turn this into bullet-point requirements.”

---

### 3.3 Ask for Structure and Constraints

Better prompts:
- Define word count or level of detail.
- Set tone: “formal technical”, “conversational”, “executive summary”.
- Request specific sections: *Context, Analysis, Risks, Recommendations*.
- Ask for assumptions and limitations at the end.

---

### 3.4 Use AI as a Thinking Partner

Don’t just ask it to “do the task”; ask it to:

- List **options** and trade-offs.
- Identify **risks**, **edge cases**, or **missing information**.
- Provide **checklists** you can use to review the work manually.

---

## 4. Workflow Design with AI (Continued)

### 4.2 Example Workflows

#### Workflow 1: Technical Report Generation

**Outcome:** Comprehensive technical report for stakeholders

**Steps:**

**1. Research & Information Gathering** (Human + AI)
- Human: Collect source documents, data, references
- AI Prompt:
```
"Summarize each of these 3 documents focusing on [topic]:

Document 1: [paste]
Document 2: [paste]
Document 3: [paste]

For each, extract:
- Key data points
- Main claims and conclusions
- Relevant standards or requirements
- Any contradictions between documents

Flag anything unclear with [?]"
```

**2. Structure & Outline** (AI + Human)
- AI Prompt:
```
"Based on these summaries, create a structured outline for a technical report.

Audience: Engineering managers with some technical background
Required sections: Executive Summary, Background, Analysis, Findings, 
Recommendations, Risks, Conclusion

For each section, provide 3-5 bullet points of key content to cover."
```
- Human: Review outline, adjust structure

**3. Draft Core Content** (AI, section by section)
- AI Prompt for each section:
```
"Write the [Analysis] section using this outline:
[paste relevant bullets]

Source material:
[paste relevant summaries]

Requirements:
- Technical but accessible language
- 500-700 words
- Include supporting data for claims
- Use short paragraphs
- Flag information gaps with [?]

Format with Markdown headings."
```

**4. Technical Review** (Human - Critical!)
- Verify all technical claims
- Check calculations and data
- Validate conclusions
- Add domain expertise
- Correct errors

**5. Refine & Polish** (AI + Human)
- AI Prompt:
```
"Review this draft section and improve it:

[paste section]

Tasks:
1. Tighten writing - remove 20% of words without losing meaning
2. Improve clarity of complex explanations
3. Flag weak arguments or unclear logic
4. Ensure consistent terminology
5. Check transitions between paragraphs

Provide the revised version."
```

**6. Executive Summary** (AI, after all sections done)
- AI Prompt:
```
"Create an executive summary for this complete report:

[paste full report]

Requirements:
- 5 bullet points maximum
- Each bullet: one key finding or recommendation
- Written for senior stakeholders
- Actionable and specific
- 150 words total"
```

**7. Final Validation** (Human)
- Read full report end-to-end
- Check formatting and consistency
- Verify all technical content
- Approve and publish

**Time saved:** ~60-70% vs. manual writing (after workflow is optimized)

---

#### Workflow 2: Code Documentation Generation

**Outcome:** Comprehensive documentation for a code module

**Steps:**

**1. Code Analysis** (AI)
```
"Analyze this code file and create a technical overview:

```[language]
[paste code]
```

Provide:
1. High-level purpose of this module
2. Main classes/functions and their roles
3. Dependencies and integrations
4. Data flow (what goes in, what comes out)
5. Any patterns or design principles used

Format as structured markdown."
```

**2. Function Documentation** (AI)
```
"For each function in this code, generate documentation:

```[language]
[paste code]
```

For each function provide:
- Purpose (1-2 sentences)
- Parameters (name, type, description)
- Return value (type, description)
- Exceptions or errors raised
- Usage example
- Edge cases or important notes

Format as docstring style comments compatible with [language]."
```

**3. Usage Examples** (AI + Human)
```
"Create 3 usage examples for this code, showing:
1. Basic usage (simplest case)
2. Common use case (realistic scenario)
3. Advanced usage (complex scenario)

Include:
- Setup/prerequisites
- Complete working code
- Expected output
- Explanation of what's happening

Code:
```[language]
[paste code]
```
```

**4. Technical Review** (Human)
- Test all code examples
- Verify technical accuracy
- Check for missing edge cases
- Add domain-specific notes

**5. Compilation** (AI)
```
"Combine these elements into a complete README.md:

Overview: [paste]
Function docs: [paste]
Examples: [paste]

Structure:
# Module Name
## Overview
## Installation
## Quick Start
## API Reference
## Examples
## Contributing
## License

Make it professional and user-friendly."
```

---

#### Workflow 3: Meeting Notes → Action Items

**Outcome:** Structured action items from meeting transcription

**Steps:**

**1. Transcription Cleanup** (AI)
```
"Clean up this meeting transcript:
- Fix obvious typos and grammar
- Remove filler words (um, uh, like, you know)
- Preserve all technical terms and names
- Keep the meaning exact

Transcript:
[paste raw transcript]"
```

**2. Summary Extraction** (AI)
```
"From this meeting transcript, extract:

1. Key decisions made
2. Action items (who, what, when)
3. Open questions or unresolved issues
4. Important discussion points
5. Follow-up topics for next meeting

Transcript:
[paste cleaned transcript]

Format:
Use bullet points, be specific, include names/dates when mentioned."
```

**3. Action Item Structuring** (AI)
```
"Convert these action items into a structured task list:

[paste action items from step 2]

For each action item provide:
- Task description (clear and actionable)
- Assigned to (person's name)
- Due date (or 'TBD' if not specified)
- Dependencies (if any)
- Priority (infer from discussion: High/Medium/Low)

Format as markdown table."
```

**4. Email Draft** (AI)
```
"Draft a meeting follow-up email using this information:

Summary: [paste]
Action items: [paste table]
Open questions: [paste]

Email should:
- Thank attendees
- Briefly summarize key decisions
- Present action items clearly
- Invite corrections or additions
- Professional but friendly tone
- Under 200 words

Start with subject line."
```

**5. Review & Send** (Human)
- Verify all action items are accurate
- Check names and dates
- Confirm priorities
- Add any missing context
- Send email

---

### 4.3 Test and Iterate Your Workflows

Treat workflows like code - they need testing and refinement.

#### Testing Process:

**1. Initial Test**
- Run the workflow with a real example
- Document time taken for each step
- Note any places where it breaks or produces poor results
- Compare quality to manual process

**2. Edge Case Testing**
- Try with unusual or complex inputs
- Test with minimal information
- Test with too much information
- Try different formats or structures

**3. Consistency Testing**
- Run the same input multiple times
- Check if outputs are consistent
- Identify which steps have high variability
- Refine prompts to improve consistency

**4. Refinement Cycle**
```
Test → Identify Issues → Update Prompts → Test Again

Document what you change and why:

Workflow: Technical Report Generation
Version: 1.3
Date: 2024-11-20

Changes from v1.2:
- Added "include data sources" to drafting prompt
- Increased word limit from 500 to 700 for Analysis section
- Added explicit request for short paragraphs
- Result: Reports are more detailed and readable

Test results:
- Speed: 45 min vs 3 hours manual (85% time savings)
- Quality: Comparable to manual, requires 15 min review
- Consistency: High - 4/5 tests produced acceptable first drafts
```

#### Create a Workflow Testing Log:

```markdown
# Workflow Testing Log

## Workflow: [Name]
Version: [X.X]
Last Updated: [Date]

### Test Results

#### Test 1: [Date]
**Input:** [Description]
**Result:** ✓ Success / ✗ Failed
**Time:** [X minutes]
**Quality:** [Rating 1-5]
**Issues:** [List problems]
**Notes:** [Observations]

#### Test 2: [Date]
**Input:** [Description]
**Result:** ✓ Success / ✗ Failed
**Time:** [X minutes]
**Quality:** [Rating 1-5]
**Issues:** [List problems]
**Notes:** [Observations]

### Refinements

**v1.1 → v1.2**
- Changed: [What]
- Reason: [Why]
- Impact: [Result]

**v1.2 → v1.3**
- Changed: [What]
- Reason: [Why]
- Impact: [Result]
```

---

## 5. Prompt Library (Organized by Use Case)

Save these templates and customize for your needs. Replace `[brackets]` with your specifics.

### 5.1 Learning & Explanation

#### Prompt: Concept Explainer

```
Act as a patient, knowledgeable tutor specializing in [subject area].

Goal: Explain [topic] to someone with [background level: beginner/intermediate/expert].

Use this structure:
1. Big picture intuition (why it matters, what problem it solves)
2. Simple example or analogy
3. Core concepts with clear definitions
4. More detailed technical explanation
5. Common misconceptions to avoid

Requirements:
- Avoid unnecessary jargon, or define it when first used
- Use short paragraphs and bullet points for clarity
- Include 1-2 diagrams or visual descriptions if helpful
- Maximum [word count] words

After explaining, ask me 3 questions to check my understanding.
```

**Usage Example:**
```
Act as a patient, knowledgeable tutor specializing in web development.

Goal: Explain "REST APIs" to someone with beginner programming knowledge 
but no web development experience.

Use this structure:
1. Big picture intuition (why it matters, what problem it solves)
2. Simple example or analogy
3. Core concepts with clear definitions
4. More detailed technical explanation
5. Common misconceptions to avoid

Requirements:
- Avoid unnecessary jargon, or define it when first used
- Use short paragraphs and bullet points for clarity
- Include 1-2 analogies to real-world situations
- Maximum 600 words

After explaining, ask me 3 questions to check my understanding.
```

---

#### Prompt: Tutorial Generator

```
Act as an experienced educator creating hands-on tutorials.

Goal: Create a step-by-step tutorial for [skill/task].

Audience: [Description of learner level and background]

Tutorial structure:
1. Learning objectives (3-5 specific outcomes)
2. Prerequisites (what they need to know/have first)
3. Estimated time to complete
4. Step-by-step instructions (numbered, clear, specific)
5. Code examples or screenshots where relevant
6. Common pitfalls and how to avoid them
7. Practice exercises (2-3, increasing difficulty)
8. How to verify success
9. Next steps (what to learn next)

Requirements:
- Every step should be actionable and testable
- Include expected outputs/results
- Explain WHY, not just HOW
- Conversational but professional tone
- [Length requirement]
```

---

#### Prompt: Understanding Checker

```
I'm learning about [topic]. I think I understand it, but I want to verify.

Here's my understanding in my own words:
"""
[Your explanation of the topic]
"""

Please:
1. Identify what I got right
2. Identify any misconceptions or gaps
3. Clarify anything I misunderstood
4. Add important details I missed
5. Give me 2 practice problems to test my understanding
6. Suggest what I should learn next to build on this

Be encouraging but honest about any errors.
```

---

### 5.2 Content Creation & Editing

#### Prompt: Universal Summarizer

```
Act as an expert summarizer and editor.

Goal: Transform this text into a [type: executive summary / bullet list / 
one-page brief / key takeaways].

Audience: [Description of who will read this]

Context: [What this will be used for]

Source text:
"""
[PASTE TEXT HERE]
"""

Requirements:
- Maximum [word/character count]
- Focus on [specific aspects]
- Preserve key technical terms
- Remove fluff and redundancy
- [Tone: formal/casual/technical]

Structure:
[Specify sections if needed, e.g.:]
- Main Points (3-5 bullets)
- Key Data/Statistics
- Recommendations or Action Items
- Risks/Assumptions/Open Questions

Highlight anything that needs verification with [?].
```

**Customization Points:**
- **Type:** executive summary, bullet list, one-pager, abstract, synopsis
- **Audience:** executives, technical team, general public, students
- **Focus:** main arguments, technical details, action items, risks
- **Length:** 100 words, 500 words, 1 page, 5 bullets

---

#### Prompt: Tone Adjuster

```
Rewrite this text to match a different tone while preserving the meaning:

Original text:
"""
[PASTE TEXT]
"""

Current tone: [describe current tone]
Target tone: [formal / casual / technical / persuasive / educational / 
friendly / authoritative]

Target audience: [who will read this]

Additional requirements:
- [Preserve/remove] technical jargon
- [Increase/decrease] sentence length
- [Add/remove] examples or analogies
- Maximum [word count] words
- [UK/US] English

Provide the rewritten version, then briefly explain the key changes you made.
```

**Example usage:**
```
Current tone: Casual and conversational
Target tone: Formal and technical
Target audience: Senior engineering review board
```

---

#### Prompt: Format Converter

```
Convert this content from [current format] to [target format]:

Source content:
"""
[PASTE CONTENT]
"""

Current format: [prose paragraph / bullet list / data table / JSON / etc.]
Target format: [what you want]

Requirements:
- Preserve all information
- [Reorganize/maintain] the structure
- [Add/remove] headers or sections
- Ensure [specific format standard]

If any information doesn't fit the new format well, note it with [?].
```

**Common conversions:**
- Prose → bullet list
- Meeting notes → structured agenda
- Data table → narrative summary
- Email thread → single summary
- Code → documentation
- JSON → readable table

---

### 5.3 Technical & Development

#### Prompt: Code Generator ("Vibe Coding")

```
Act as a senior [language] developer.

Goal: Design and implement [feature/tool/script/function].

Context:
- Project: [description]
- Environment: [OS, frameworks, dependencies]
- Constraints: [performance, compatibility, style guide]
- Existing architecture: [relevant details]

Tasks:
1. Ask me 3-5 clarifying questions before you start coding
2. Propose a simple design (functions, classes, data structures)
3. Generate well-commented code with docstrings
4. Provide usage examples
5. Include error handling and edge cases
6. Add a "How to run/test this" section

Code requirements:
- Readable and modular
- Follow [style guide: PEP 8, Google Style, etc.]
- Prefer simple solutions over clever ones
- Include type hints where applicable
- Add TODO comments for future improvements

Stop after clarifying questions - wait for my answers before coding.
```

**Example:**
```
Act as a senior Python developer.

Goal: Design and implement a CSV processor that validates data and 
generates a summary report.

Context:
- Project: Data pipeline for monthly sales reports
- Environment: Python 3.10+, runs in WSL2, will be scheduled via cron
- Constraints: Must handle files up to 100MB, process in under 5 minutes
- Existing architecture: Uses pandas, outputs to PostgreSQL

Tasks:
1. Ask me 3-5 clarifying questions before you start coding
2. Propose a simple design (functions, classes, data structures)
3. Generate well-commented code with docstrings
4. Provide usage examples
5. Include error handling and edge cases
6. Add a "How to run/test this" section

Code requirements:
- Readable and modular
- Follow PEP 8
- Prefer simple solutions over clever ones
- Include type hints
- Add logging for debugging

Stop after clarifying questions - wait for my answers before coding.
```

---

#### Prompt: Code Reviewer

```
Act as a senior code reviewer performing a thorough code review.

Review this code for:
1. **Correctness:** Logic errors, bugs, edge cases
2. **Performance:** Inefficiencies, bottlenecks, optimization opportunities
3. **Readability:** Naming, structure, comments, clarity
4. **Security:** Vulnerabilities, input validation, data handling
5. **Best Practices:** Idiomatic code, design patterns, maintainability
6. **Testing:** What tests are missing?

Code to review:
```[language]
[PASTE CODE]
```

Provide:
- Summary (1-2 sentences)
- Critical issues (must fix)
- Important suggestions (should fix)
- Minor improvements (nice to have)
- What's done well
- Specific code suggestions for fixes (show the improved code)

Be constructive and specific. Use this format:

## Critical Issues
[list with specific line numbers]

## Important Suggestions
[list with specific line numbers]

## Minor Improvements
[list]

## What's Done Well
[list]

## Suggested Fixes
```[language]
[show corrected code]
```
```

---

#### Prompt: Documentation Generator

```
Create comprehensive documentation for this code:

```[language]
[PASTE CODE]
```

Generate:

1. **Module Overview** (2-3 paragraphs)
   - Purpose and main functionality
   - When/why to use this
   - Key design decisions

2. **Installation/Setup** (if applicable)
   - Requirements
   - Installation steps
   - Configuration

3. **Quick Start Guide**
   - Simplest possible usage example
   - Expected output

4. **API Reference**
   For each public function/class:
   - Purpose
   - Parameters (name, type, description, default)
   - Return value (type, description)
   - Exceptions/errors
   - Usage example

5. **Advanced Usage**
   - Complex scenarios
   - Integration with other components
   - Configuration options

6. **Common Issues & Troubleshooting**
   - Known limitations
   - Error messages and solutions

Format as Markdown suitable for a README.md file.
```

---

#### Prompt: Debugging Assistant

```
I'm trying to [task] but getting this error:

**Error message:**
"""
[PASTE ERROR]
"""

**My code:**
```[language]
[PASTE CODE]
```

**What I've tried:**
[List what you've already attempted]

**Environment:**
- [Language/framework versions]
- [Operating system]
- [Relevant dependencies]

Please:
1. Explain what this error means in simple terms
2. Identify the likely root cause
3. Suggest 2-3 solutions (easiest first)
4. Provide corrected code for the most likely solution
5. Explain how to prevent this error in the future
6. Suggest what to check if that doesn't work

Be specific and include code examples.
```

---

### 5.4 Analysis & Decision Support

#### Prompt: Options Analyzer

```
I'm trying to decide between multiple options for [situation/problem].

Options I'm considering:
A) [Describe option A]
B) [Describe option B]
C) [Describe option C]

Context:
- Current situation: [describe]
- Constraints: [time, budget, resources]
- Goals: [what success looks like]
- Stakeholders: [who cares about this decision]

For each option, provide:
1. **Pros** (3-5 advantages)
2. **Cons** (3-5 disadvantages)
3. **Hidden costs or complexities** (what might I be missing?)
4. **Risk level** (Low/Medium/High and why)
5. **Time to implement**
6. **Long-term implications**

Then:
7. **Decision criteria** I should use to choose
8. **Additional information** I should gather
9. **Your recommendation** with reasoning

Format as a structured comparison table for easy scanning.
```

---

#### Prompt: Risk Identifier

```
Act as a risk assessment specialist.

I'm planning to [describe plan/project/decision].

Details:
[Provide context, constraints, timeline, resources, stakeholders]

Conduct a comprehensive risk analysis:

1. **Potential Risks** (brainstorm 8-12 things that could go wrong)
   For each: Describe the risk, likelihood (L/M/H), impact (L/M/H)

2. **Hidden Assumptions** (what am I assuming that might be wrong?)

3. **Blind Spots** (what am I likely overlooking or not seeing?)

4. **External Dependencies** (what's outside my control that could fail?)

5. **Cascade Failures** (if X fails, what else fails?)

6. **Pre-Mortem** (assume this failed badly - what happened?)

7. **Mitigation Strategies** (for top 5 risks, how can I reduce or eliminate?)

8. **Warning Signs** (early indicators that things are going wrong)

Be thorough and critical - I want to know everything that could go wrong.
```

---

#### Prompt: Assumption Checker

```
I'm making the following plan/argument/analysis:

"""
[PASTE YOUR PLAN/ARGUMENT]
"""

Please identify all assumptions I'm making:

1. **Explicit Assumptions** (things I stated)
2. **Implicit Assumptions** (things I'm assuming without stating)
3. **Questionable Assumptions** (assumptions that might be wrong)
4. **Critical Assumptions** (if wrong, the whole thing fails)

For each critical assumption:
- Why it matters
- How to validate it
- What to do if it's wrong
- Alternative assumptions to consider

Then suggest what additional information I should gather before proceeding.
```

---

#### Prompt: Decision Framework Generator

```
I need to make a decision about [topic/problem].

Context:
[Describe the situation, stakeholders, constraints, timeline]

Create a decision-making framework:

1. **Decision Criteria** (what factors should influence this decision?)
   - List 5-7 criteria
   - For each, explain why it matters
   - Suggest weighting (% importance)

2. **Information Needed**
   - What data/facts do I need to gather?
   - Where can I get this information?
   - What's the minimum info needed to decide?

3. **Evaluation Process**
   - Step-by-step process to evaluate options
   - How to score each option against criteria
   - How to handle trade-offs

4. **Decision Matrix Template**
   - Create a table to evaluate options
   - Include scoring guide

5. **Validation Checks**
   - How to verify this is a good decision
   - Red flags that suggest reconsidering

Make it practical and actionable.
```

---

### 5.5 Meta-Prompting

#### Prompt: Prompt Debugger

```
Act as a "prompt engineering expert" helping me improve my prompts.

Here's my prompt:
"""
[PASTE YOUR PROMPT]
"""

Here's what I wanted vs. what I got:
- **Intended outcome:** [describe what you wanted]
- **Actual result:** [describe what you got]
- **Problem:** [what was wrong with the result]

Please:
1. **Diagnose** - Identify 3-5 problems with my original prompt
2. **Explain** - Why each problem led to poor results
3. **Rewrite** - Provide an improved version using best practices
4. **Annotate** - Mark the key improvements and explain why they work better
5. **Alternative** - Suggest a different approach if the rewrite won't work

Use the CGRATF framework (Context, Goal, Role, Audience, Tone/Format, Follow-up) 
in your rewrite.
```

---

#### Prompt: Prompt Generator

```
I want to create a reusable prompt template for [task/use case].

Task description:
[Describe what you want the prompt to accomplish]

Requirements:
- Target audience: [who will use this prompt]
- Typical inputs: [what varies each time]
- Expected outputs: [what format/content]
- Common variations: [different scenarios it should handle]
- Quality criteria: [how to judge if output is good]

Create a prompt template that:
1. Is clear and specific
2. Uses best practices (role, goal, audience, format, etc.)
3. Has [brackets] for customization points
4. Includes usage instructions
5. Shows an example of the filled-in prompt

Also provide:
- When to use this prompt
- Common customization points
- Tips for best results
- Potential issues and how to avoid them
```

---

#### Prompt: Workflow Designer

```
Act as a workflow optimization expert.

I want to create an AI-augmented workflow for: [describe the task/process]

Current manual process:
[Describe your current steps, time taken, pain points]

Goals:
- [What you want to improve: speed, quality, consistency]
- [Constraints: tools, budget, time]

Design an optimal workflow that:
1. **Maps the process** (3-7 steps, each step has clear input/output)
2. **Assigns tools** (which steps use AI, which need human judgment)
3. **Provides prompts** (AI prompt template for each AI step)
4. **Includes validation** (how to check quality at each step)
5. **Estimates time savings** (realistic time comparison)
6. **Identifies risks** (where might this workflow fail?)

For each AI step, provide a complete, reusable prompt template.

Format as a clear, step-by-step guide I can follow immediately.
```

---

## 6. Real-World Examples: Before and After

### Example 1: Weak → Strong Prompt (Learning)

**❌ Weak:**
```
Explain machine learning
```

**Why it's weak:**
- No audience specified
- No context about why you're learning
- No indication of depth needed
- No format preference
- AI will give generic, Wikipedia-like explanation

**✓ Strong:**
```
Act as a patient computer science tutor.

Goal: Explain "machine learning" to me so I can understand whether it's 
relevant for my business problem.

My background: I'm a business analyst with strong Excel skills but no 
programming experience. I understand basic statistics (mean, median, 
correlation).

My situation: My company is considering using ML for customer churn 
prediction. I need to understand what ML is and isn't good for, so I can 
have informed conversations with our data science team.

Please:
1. Start with a simple analogy I can relate to
2. Explain the core concept (what is ML really doing?)
3. Give 2-3 real business examples
4. Explain when ML is and isn't appropriate
5. Flag 2-3 common misconceptions about ML
6. Use max 500 words, no code, no equations

After explaining, ask me 3 questions to check if I understood the key concepts.
```

**Why it's better:**
- Clear role and audience
- Specific context and goal
- Constraints on complexity (no code, no equations)
- Structured output (6 specific elements)
- Verification step (questions at the end)
- Appropriate length (500 words)

---

### Example 2: Single Prompt → Workflow (Technical Writing)

**❌ One-shot attempt:**
```
Write complete technical documentation for our user authentication system
```

**Why it's weak:**
- Too large a task for one prompt
- No structure or organization
- Can't review/adjust midstream
- AI will make assumptions about what to include
- Hard to verify accuracy
- Likely to miss important details

**✓ Workflow approach:**

**Step 1: Requirements Gathering**
```
"I need to document our authentication system. Before I provide code, 
ask me 7-10 clarifying questions about:
- What aspects need documenting (API, architecture, user guide?)
- Who is the audience (developers, end users, security auditors?)
- What's the scope (just auth, or related systems too?)
- What format is needed (README, wiki, API docs?)
- What's most important vs. nice-to-have?"
```

**Step 2: Outline Creation**
```
"Based on my answers: [paste answers]

Create a detailed documentation outline with:
- Section names
- 3-5 bullet points per section (what to cover)
- Estimated length per section
- Priority (must-have, should-have, nice-to-have)

Make it comprehensive but organized."
```

**Step 3: Architecture Documentation**
```
"Write the 'System Architecture' section using this outline:
[paste relevant bullets]

Context: [paste code/diagrams]

Requirements:
- Audience: Senior developers new to the codebase
- Length: 400-600 words
- Include: data flow, components, security layers
- Use Mermaid diagram for data flow
- Technical but clear language

Flag anything you're uncertain about with [?]."
```

**Step 4: Technical Review (Human)**
- Verify all technical details
- Check code examples actually work
- Add security considerations
- Validate architecture description

**Step 5: API Reference**
```
"Generate API reference documentation from this code:

```python
[paste authentication code]
```

For each endpoint provide:
- Purpose
- HTTP method and route
- Parameters (type, required/optional, description)
- Request body schema
- Response codes and bodies
- Authentication requirements
- Example request/response
- Common errors

Format as Markdown tables for easy scanning."
```

**Step 6: User Guide**
```
"Write a user-facing guide for authentication. Using the technical docs 
we created: [paste relevant sections]

Transform for non-technical users:
- Remove implementation details
- Focus on HOW to use, not HOW it works
- Include screenshots or ASCII diagrams
- Step-by-step login/logout/password reset flows
- Troubleshooting common issues
- Plain language, conversational tone
- Max 800 words"
```

**Step 7: Review & Integration (Human)**
- Test all examples
- Verify user guide with actual users
- Check for outdated information
- Ensure consistency across sections
- Combine into final documentation

**Why this is better:**
- Iterative and reviewable
- Each step is manageable
- Can correct course midstream
- Human verification at critical points
- Produces consistent, comprehensive docs
- Clear separation of technical vs. user content

---

### Example 3: Vague → Specific (Code Generation)

**❌ Vague:**
```
Write a script to process files
```

**✓ Specific:**
```
Act as a senior Python developer specializing in data processing.

Goal: Write a script that processes CSV files in a specific way.

Requirements:
1. Read all CSV files from an input directory
2. For each file:
   - Validate that it has columns: date, user_id, action, value
   - Filter rows where action = "purchase" and value > 100
   - Calculate total value per user_id
   - Add a "month" column extracted from the date column
3. Combine all processed data into a single output CSV
4. Generate a summary report: total users, total value, average per user

Environment:
- Python 3.10+
- Can use pandas, no other external libraries
- Will run on Linux (WSL)
- Input files: 10-50MB each, 5-20 files at a time

Code requirements:
- Include error handling for malformed CSVs
- Add progress indicators (which file being processed)
- Use type hints
- Add docstrings for main functions
- Include logging for debugging
- Make it modular (separate functions for each step)

Provide:
1. The complete script with comments
2. Usage instructions
3. Example command line invocation
4. What to do if errors occur

Before coding, ask any clarifying questions.
```

**Why it's better:**
- Exact input/output specified
- Processing steps enumerated
- Environment and constraints clear
- Code quality requirements stated
- Asks for clarifications first
- Includes error handling requirements
- Specifies documentation needed

---

### Example 4: No Context → Full Context (Decision Making)

**❌ No context:**
```
Should I use MongoDB or PostgreSQL?
```

**✓ Full context:**
```
I'm a backend developer choosing a database for a new project and need help 
deciding between MongoDB and PostgreSQL.

Project context:
- Web application for task management (like Trello/Asana)
- Expected users: 1,000-10,000 initially, potential to scale to 100k+
- Team: 3 developers, moderate database experience
- Timeline: 3 months to MVP
- Budget: Startup, need cost