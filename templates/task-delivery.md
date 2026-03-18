# Task Delivery Template

Use this template when delivering a task to an implementer subagent.

## Template

```markdown
## Task: [Task Name]

### Context
[Where this fits in the larger project, dependencies]

### Requirements
[What needs to be implemented]

### File Structure
- Create: `path/to/new-file.ts`
- Modify: `path/to/existing-file.ts:123-145`

### Implementation Steps

- [ ] **Step 1: Write failing test**
```typescript
// Test code here
```

- [ ] **Step 2: Verify failure**
```bash
npm test path/to/test.ts
# Expected: FAIL
```

- [ ] **Step 3: Write implementation**
```typescript
// Implementation code here
```

- [ ] **Step 4: Verify pass**
```bash
npm test path/to/test.ts
# Expected: PASS
```

- [ ] **Step 5: Commit**
```bash
git add .
git commit -m "feat: [description]"
```

### Acceptance Criteria
- [ ] Tests pass
- [ ] Code follows existing patterns
- [ ] No overbuilding (YAGNI)
- [ ] Committed
```

## Usage

1. Extract task from plan
2. Fill in context and requirements
3. Include exact file paths
4. Provide complete code snippets
5. Add test commands with expected output
