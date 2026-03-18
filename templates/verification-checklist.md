# Verification Checklist

Use this checklist to verify completion at each phase.

## Design Phase

- [ ] Explored project context
- [ ] Asked clarifying questions (one at a time)
- [ ] Proposed 2-3 approaches with trade-offs
- [ ] Presented design in sections
- [ ] User approved design
- [ ] Spec document written
- [ ] Spec passed review loop
- [ ] User reviewed and approved spec
- [ ] Phase confirmation: planning phase entered

## Planning Phase

- [ ] Read spec document
- [ ] Defined file structure
- [ ] Decomposed into tasks (2-5 min each)
- [ ] Each task has:
  - [ ] Exact file paths
  - [ ] Complete code
  - [ ] Test commands
  - [ ] Commit commands
- [ ] Plan document written
- [ ] Plan passed review loop
- [ ] Phase confirmation: execution phase entered

## Execution Phase

### Per Task

- [ ] Agent selected (Codex/Claude Code)
- [ ] Implementer dispatched
- [ ] Implementer completed task
- [ ] Tests passing
- [ ] Code committed
- [ ] Spec reviewer approved
- [ ] Code quality reviewer approved

### After All Tasks

- [ ] All tasks complete
- [ ] All tests passing
- [ ] Code review passed
- [ ] User notified of completion

## Quick Dev Mode

- [ ] Task fits within 3-task limit
- [ ] Simplified spec generated (1-2 sentences)
- [ ] Codex availability checked
- [ ] Tasks executed
- [ ] Tests passing
- [ ] Changes committed

## Verification Evidence

| Check | Evidence |
|-------|----------|
| Design complete | Spec file at `docs/...` |
| Plan complete | Plan file at `docs/...` |
| Task complete | Git commit SHA |
| Spec review pass | Review approval |
| Code review pass | Review approval |
