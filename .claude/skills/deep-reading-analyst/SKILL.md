---
name: deep-reading-analyst
description: "Systematic framework for deep analysis of articles, papers, and long-form content using multiple thinking models (structured thinking, first principles, critical thinking, systems thinking, six thinking hats). Use when users want to: (1) deeply understand complex articles/content, (2) analyze arguments and identify logical flaws, (3) extract actionable insights from reading materials, (4) create study notes or learning summaries, (5) compare multiple sources, or (6) transform knowledge into practical applications. Triggered by phrases like 'analyze this article,' 'help me understand,' 'deep dive into,' 'extract insights from,' or when users provide URLs/long-form content for analysis."
---

# Deep Reading Analyst

Transforms surface-level reading into deep learning through systematic analysis using proven thinking frameworks. Guides users from understanding to application.

## Workflow Decision Tree

```
User provides content
    ↓
Ask: Purpose + Depth Level
    ↓
┌─────────────┬─────────────┬─────────────┬─────────────┐
│  Level 1    │  Level 2    │  Level 3    │  Level 4    │
│  Quick      │  Standard   │  Deep       │  Research   │
│  15min      │  30min      │  60min      │  120min+    │
└─────────────┴─────────────┴─────────────┴─────────────┘
    ↓             ↓             ↓             ↓
Structure    + Critical    + Systems     + Cross-source
  Only         Thinking     + 6 Hats      Comparison
```

## Step 1: Initialize Analysis

**Ask User:**
1. "What's your main goal for reading this?" (problem-solving / learning / writing / curiosity)
2. "Preferred depth?" (Quick / Standard / Deep / Research)
3. "Any specific focus areas?"

**Default if no response:** Level 2 (Standard mode)

## Step 2: Structural Understanding

**Always start here regardless of depth level.**

Extract and present:

```markdown
📄 Content Type: [Article/Paper/Report/Guide]
⏱️ Estimated reading time: [X minutes]
🎯 Core Thesis: [One sentence]

Structure:
├─ Main Argument 1
│   ├─ Supporting point 1.1
│   └─ Supporting point 1.2
├─ Main Argument 2
└─ Main Argument 3

Key Concepts: [3-5 terms]
High-Value Sections: [Paragraph/chapter numbers]
```

## Step 3: Apply Thinking Models

**Select based on depth level:**

### Level 1 (Quick): Structure + Key Insights
- Skip detailed analysis
- Provide: Structure + TOP 3 insights + 1 action item

### Level 2 (Standard): + Critical Thinking
Load `references/critical_thinking.md` and apply:
- Argument quality assessment
- Logic flaw identification  
- Evidence evaluation
- Alternative perspectives

### Level 3 (Deep): + First Principles + Systems Thinking
Additionally load:
- `references/first_principles.md` - Strip to essence
- `references/systems_thinking.md` - Build connections
- `references/six_hats.md` - Multi-perspective analysis

### Level 4 (Research): + Cross-source Comparison
Use web_search to find related sources and compare viewpoints.

## Step 4: Synthesis & Output

**Generate based on user goal:**

### For Problem-Solving:
```markdown
## Applicable Solutions
[Extract 2-3 methods from content]

## Application Plan
Problem: [User's specific issue]
Relevant insight: [From content]
Action steps: [Concrete 1-2-3]
Expected outcome: [Measurable]
```

### For Learning:
```markdown
## Learning Notes
Core concepts: [Reworded in user's language]
Mental models: [Visualized relationships]
Connections to prior knowledge: [Link to what user knows]

## Verification Questions
[3 questions to test understanding]
```

### For Writing Reference:
```markdown
## Key Arguments & Evidence
[Structured extraction]

## Quotable Insights
[3-5 powerful statements with context]

## Counterfactuals
[What the article doesn't address]
```

## Step 5: Knowledge Activation

**Always end with:**

```markdown
## 🎯 Immediate Takeaways (Top 3)
1. [Insight] → Why it matters → One action

## 💡 Quick Win
[One thing to try in next 24 hours]

## 🔗 Next Steps
[ ] Further reading: [If relevant]
[ ] Discuss: [Questions for others]
[ ] Experiment: [Test in real context]
```

## Quality Standards

Every analysis must:
- ✅ Stay faithful to original content (no misrepresentation)
- ✅ Distinguish facts from opinions
- ✅ Provide concrete examples
- ✅ Connect to user's context when possible
- ✅ End with actionable steps

**Avoid:**
- ❌ Overwhelming with all frameworks at once
- ❌ Academic jargon without explanation
- ❌ Analysis without application
- ❌ Copying text verbatim (always reword)

## Interaction Patterns

**Progressive questioning:**
- Understanding: "What do you think the author means by X?"
- Critical: "Do you see any gaps in this argument?"
- Application: "How might you use this in your work?"

**Adapt to signals:**
- User asks "what's the main point?" → They want conciseness, reduce detail
- User challenges your analysis → Lean into critical thinking
- User asks "how do I use this?" → Focus on application section

## Output Format Templates

Load when needed:
- `references/output_templates.md` - Formatted note structures
- `references/comparison_matrix.md` - Multi-source analysis format

## Reference Materials

Detailed thinking model explanations:
- `references/critical_thinking.md` - Argument analysis framework
- `references/first_principles.md` - Essence extraction method
- `references/systems_thinking.md` - Relationship mapping
- `references/six_hats.md` - Multi-perspective protocol
- `references/output_templates.md` - Note format examples
- `references/comparison_matrix.md` - Cross-article analysis
