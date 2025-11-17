DevOps PR Assistant
LLM-powered pull request triage for faster, smarter code reviews
Track: Enterprise Agents — Google × Kaggle Agents Intensive Capstone (2025)

**Overview**
Manual pull request (PR) triage slows down engineering teams. Developers spend time on repetitive
tasks like identifying missing tests, checking risk levels, assigning reviewers, and managing labels.
These delays reduce development velocity and lead to inconsistent review quality.
DevOps PR Assistant is a multi-agent, LLM-driven automation pipeline that analyzes incoming PRs,
summarizes diffs, recommends the next best action, posts automated comments, applies labels, and
logs all decisions for future insights.
This agent integrates LLM reasoning + GitHub tooling + persistent memory to automate the boring
parts of code review — letting developers focus on real logic, not admin work.

**Problem**
Teams frequently face:
- Slow review cycles
- Reviewers missing high-risk changes
- Missing tests or incomplete descriptions
- Manual labeling and triage overhead
- No centralized view of PR quality or patterns
Traditional CI rules are rigid and cannot understand context behind code changes.

**Solution**
A three-agent workflow that evaluates every pull request:
1. Triager Agent
- Receives GitHub PR events (via webhook)
- Fetches metadata + diff summary
- Passes a normalized context to Advisor agent
2. Advisor Agent (LLM)
- Understands the PR using structured prompting
- Produces:
- recommendation → approve / add_tests / request_changes / add_reviewer / run_specific_check
- rationale → one clear sentence
- Uses custom tool: diff summarizer
3. Notifier Agent
- Posts a clean, formatted comment on the PR
- Applies an appropriate label
- Stores event in SQLite memory
This pipeline forms a deterministic, explainable PR review helper that is easy to deploy, extend, and
evaluate.
