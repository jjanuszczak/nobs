# Clear Writing Checker

An agent skill that reviews writing against three high-signal style guides:

- **Clay AI Writing Policy** — human ownership, writing-as-thinking, anti-slop rules
- **Amazon “Write Like an Amazonian” tips** — data-driven, concise, objective prose
- **ASD-STE100 (distilled)** — controlled language for clarity and technical precision

The skill automatically routes to the most relevant guide(s), retrieves only the applicable rules, and returns structured feedback with quoted issues, severity, rule citations, and suggested rewrites.

## Installation

### Recommended (skills CLI)

```bash
npx skills add jjanuszczak/nobs
```

Common variants:

```bash
# Install globally
npx skills add jjanuszczak/nobs -g

# Install for specific agents only
npx skills add jjanuszczak/nobs -a claude-code -a cursor

# Non-interactive (CI / scripts)
npx skills add jjanuszczak/nobs -y
```

### Manual install (Claude Code example)

```bash
mkdir -p ~/.claude/skills/clear-writing-checker
# Copy or symlink the skill file
cp SKILL.md ~/.claude/skills/clear-writing-checker/SKILL.md
# (Optional) also place the three reference guides in the same folder or your agent’s knowledge base
```

After installation, invoke the skill with phrases such as “check writing”, “review this text”, “apply style guides”, or “STE100 check”.

## Usage

Provide the text to review and optional metadata:

- `doc_type`: `technical` | `business` | `ai-assisted` | `internal` | `customer-facing` | `general`
- `audience`, `purpose`, `ai_used`
- `force_guides`: e.g. `["clay", "amazon"]` to override auto-routing

The skill returns a consistent report containing:

- Which guide(s) were applied and why
- Overall status (Pass / Needs revision / Major issues)
- Findings grouped by severity (Critical / Major / Minor) with quotes, rule citations, and rewrites
- Strengths
- Prioritized next actions

## Repository Contents

| File | Description |
|------|-------------|
| `SKILL.md` | The complete skill definition (front matter + prompt body) |
| `references/` (optional) | Place the three source guides here for RAG or direct loading |
| `README.md` | This file |

## Attributions

This skill combines three independent sources. Full credit belongs to the original authors and the people who made them widely available:

- **Clay AI Writing Policy**  
  Written by [Sophie Alpert](https://sophiebits.com) ([@sophiebits](https://x.com/sophiebits)) while at Clay.  
  Popularized on X by [Chandra (@NCResq)](https://x.com/NCResq) and [Everett (@retttx)](https://x.com/retttx).

- **Amazon Writing Tips**  
  Drawn from Amazon’s internal 2018 “Write Like an Amazonian” guide.  
  The version used here was widely shared on X by [Xiangyi Li (@xdotli)](https://x.com/xdotli).

- **ASD-STE100 / STE Writing Skill**  
  The distilled agent skill and supporting materials come from  
  [woosal1337/blog – ep01-the-cure-for-ai-slop](https://github.com/woosal1337/blog/tree/main/videos/ep01-the-cure-for-ai-slop).  
  ASD-STE100 itself is the official Simplified Technical English specification (asd-ste100.org). This skill is unofficial and not affiliated with ASD.

## License

The skill prompt itself is released under MIT.  
The referenced guides remain under their original authors’ / organizations’ rights. Use them responsibly and retain attributions.

---

Built to reduce AI slop and raise the baseline for clear, owned writing.