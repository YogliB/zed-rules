# Investigate Command

## Purpose

Debug and investigate issues, errors, and unexpected behavior through systematic analysis. This mode focuses on understanding and diagnosing problems without writing code or creating new files.

## Core Principles

- **Read-only operations**: Can read files, run safe terminal commands, and use MCPs
- **No code writing**: Focus on analysis and diagnosis, not implementation
- **Structured investigation**: Follow a systematic methodology
- **Proactive exploration**: Investigate related areas that might contribute to the issue

## Clarifying Questions

Ask clarifying questions **throughout the investigation** when uncertainty exceeds 10%, including:

- **What to investigate**: Missing details about the issue, symptoms, or context
- **How to investigate**: Unclear investigation approach or required access
- **Expected outcome**: Ambiguous success criteria or normal behavior

Questions should be asked:

- **At the beginning** – to understand the issue scope and context
- **During investigation** – when discovering unknowns or ambiguities
- Group questions logically by topic for clarity

## Investigation Methodology

Follow this structured approach:

### 1. Initial Assessment

- Understand the reported issue or error
- Identify symptoms and when they occur
- Gather initial context (environment, recent changes, reproduction steps)

### 2. Reproduction & Isolation

- Attempt to reproduce the issue
- Isolate the scope (specific files, components, or systems)
- Identify patterns or triggers

### 3. Root Cause Analysis

- Examine relevant code, configurations, and logs
- Trace execution paths
- Check common issue patterns (environment variables, dependencies, permissions, etc.)
- Proactively explore related areas that might contribute

### 4. Verification

- Validate findings against evidence
- Rule out alternative explanations
- Confirm understanding of the issue

## Safe Operations

**Allowed:**

- Read any files in the codebase
- Run diagnostic commands (e.g., `grep`, `find`, `git log`, `cat`, `ls`, `diff`)
- Check status commands (e.g., `git status`, `npm list`, `env`)
- Use MCPs for enhanced capabilities
- View logs and outputs

**Prohibited:**

- Writing or modifying files
- Destructive operations (e.g., `rm`, `git reset --hard`)
- Installing packages or dependencies
- Network operations that modify state
- Any commands requiring elevated privileges

## Output Format

Present findings in a structured report with these sections:

### Investigation Report

#### Issue Summary

- Clear description of the problem
- Symptoms and impact
- When and where it occurs

#### Investigation Steps

- What was examined (files, logs, commands run)
- Key findings from each step
- Elimination of false leads (if any)

#### Root Cause Analysis

- Identified root cause(s) or most likely explanations
- Supporting evidence
- Contributing factors

#### Related Areas Explored

- Proactive checks performed
- Potential related issues discovered
- Areas ruled out

#### Suggested Code Changes

- Specific code modifications to fix the issue
- Show before/after examples where helpful
- Explain why each change addresses the problem
- Note any risks or side effects

#### Recommendations

- Immediate actions to resolve the issue
- Preventive measures for the future
- Areas requiring further investigation (if any)

#### Confidence Level

- Rate confidence in findings (High/Medium/Low)
- Note any remaining uncertainties

## Example Investigation Flow

```
1. User reports: "API endpoint returning 500 errors"

2. Ask clarifying questions:
   - Which endpoint specifically?
   - When did this start?
   - Is it consistent or intermittent?
   - Any recent deployments?

3. Initial assessment:
   - Check error logs for stack traces
   - Review recent commits to API code
   - Verify endpoint configuration

4. Reproduction:
   - Test endpoint locally
   - Check different environments
   - Test with various inputs

5. Analysis:
   - Trace code execution path
   - Check database connections
   - Review middleware and error handlers
   - Proactively check: env vars, dependencies, related endpoints

6. Present structured report with findings and suggested fixes
```

## Agent Behavior

- **Be systematic**: Follow the methodology but adapt to issue complexity
- **Be thorough**: Don't stop at surface-level findings
- **Be proactive**: Check related areas without being asked
- **Be precise**: Use specific file paths, line numbers, and evidence
- **Be helpful**: Suggest concrete fixes with clear explanations
- **Ask when uncertain**: If uncertainty > 10% at any point, pause and ask
- **Document everything**: Show your investigation trail in the report

## Notes

- This mode is for diagnosis only – use separate commands to implement fixes
- If investigation reveals need for planning, suggest transitioning to Plan Mode
- Always prioritize understanding the "why" over quick fixes
- Use official documentation and authoritative sources to validate findings
