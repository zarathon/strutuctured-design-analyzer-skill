# Using Structured Design Analyzer with Claude Code

## Overview

Claude Code is the **perfect companion** for the Structured Design Analyzer skill. While Claude.ai (web interface) provides analysis and guidance, **Claude Code can automatically execute the refactoring plans** for you!

---

## Why Claude Code?

### Traditional Workflow (Manual)
1. ✅ Analyze code (automated)
2. ✅ Get report (automated)
3. ✅ Generate plans (automated)
4. ❌ Read plans (manual)
5. ❌ Write refactored code (manual)
6. ❌ Test changes (manual)
7. ❌ Create commits (manual)
8. ❌ Track progress (manual)

### With Claude Code (Automated)
1. ✅ Analyze code (automated)
2. ✅ Get report (automated)
3. ✅ Generate plans (automated)
4. ✅ Execute plans (automated) ← **Claude Code does this!**
5. ✅ Test changes (automated) ← **Claude Code does this!**
6. ✅ Create commits (automated) ← **Claude Code does this!**
7. ✅ Track progress (automated) ← **Claude Code does this!**

---

## Installation

### Quick Install

```bash
# macOS/Linux
curl -fsSL https://claude.ai/install.sh | bash

# Windows (PowerShell)
irm https://claude.ai/install.ps1 | iex

# npm (all platforms)
npm install -g @anthropic-ai/claude-code
```

### Verify Installation

```bash
claude --version
```

---

## Getting Started

### 1. Navigate to Your Project

```bash
cd /path/to/your/project
```

### 2. Start Claude Code

```bash
claude
```

You'll see:
```
Claude Code v1.x.x
Connected to your project
Type your request or /help for commands
>
```

### 3. Request Analysis

Simply ask in natural language:

```
> Analyze this codebase using Structured Design principles
```

Or more specifically:

```
> Run the Structured Design analyzer on this project and generate refactoring plans
```

---

## What Happens Next

Claude Code will:

### Phase 1: Analysis (1-2 minutes)
```
📊 Analyzing project...
   - Found 47 Python files
   - Analyzing functions and methods
   - Calculating cohesion scores
   - Detecting coupling issues
   - Measuring complexity
   
✅ Analysis complete!
   - 73 modules analyzed
   - Average cohesion: 4.1/7
   - 23 modules need refactoring
```

### Phase 2: Report Generation (30 seconds)
```
📝 Generating reports...
   ✅ Created: analysis_report.md
   ✅ Created: refactoring_plans/00_MASTER_PLAN.md
   ✅ Created: 23 individual refactoring plans
```

### Phase 3: Presentation (immediate)
```
📊 ANALYSIS RESULTS

The Good (5 modules):
✅ validate_email_address - Functional cohesion (7/7)
✅ calculate_order_total - Sequential cohesion (6/7)
✅ format_currency - Functional cohesion (7/7)

The Bad (18 modules):
⚠️  initialize_system - Temporal cohesion (3/7)
⚠️  process_order_steps - Procedural cohesion (4/7)
[... more ...]

The Ugly (5 modules):
🚨 handle_transaction - Logical cohesion (2/7) - CRITICAL
🚨 format_report - Control coupling - CRITICAL
[... more ...]

Would you like to:
1. Review detailed findings
2. Start refactoring critical issues
3. See the master refactoring plan
```

---

## Executing Refactoring Plans

### Option 1: Automated Full Refactoring

```
> Start with the critical issues and refactor them automatically
```

Claude will:
1. Read plan_01 (critical issue)
2. Understand current code
3. Execute each step
4. Run tests after each change
5. Create commit when complete
6. Move to plan_02
7. Repeat until all critical issues resolved

### Option 2: Guided Step-by-Step

```
> Let's refactor handle_transaction step by step, showing me each change
```

Claude will:
1. Show you Step 1
2. Explain what it's doing
3. Make the changes
4. Show you the diff
5. Ask if you want to continue
6. Proceed to Step 2

### Option 3: Manual with Assistance

```
> Show me plan_01_handle_transaction.md and help me understand it
```

Claude will:
1. Display the plan
2. Explain each step
3. Answer your questions
4. Generate code examples
5. Help when you get stuck

---

## Example: Complete Refactoring Session

### Starting the Session

```bash
$ cd my-ecommerce-project
$ claude
```

### Request Analysis

```
> Analyze this project for design quality and create refactoring plans

Claude: I'll analyze your project using Structured Design principles from
        Constantine & Yourdon (1979).
        
        [Runs analyzer...]
        
        Analysis complete!
        - 47 modules analyzed
        - Average cohesion: 3.8/7 (needs improvement)
        - 16 modules require refactoring
        
        Critical Issues (refactor immediately):
        1. handle_transaction - Logical cohesion (2/7)
           Location: payments/processor.py line 45
           Issue: Uses flag to select between 4 operations
           Time: 3-5 hours
        
        Generated plans in ./refactoring_plans/
        
        Would you like to start with the critical issue?
```

### Start Refactoring

```
> Yes, let's start with handle_transaction

Claude: I'll follow plan_01_handle_transaction.md
        
        Current code analysis:
        - Function: handle_transaction(transaction_type, data)
        - Cohesion: Logical (2/7)
        - Problem: Control parameter 'transaction_type' selects operation
        - Operations: payment, refund, adjustment, cancellation
        
        Goal: Transform to Functional cohesion (7/7)
        Estimated time: 3-5 hours
        
        Ready to proceed? (I'll show each step)
```

### Step-by-Step Execution

```
> Yes, proceed

Claude: === Step 1: Identify Operation Branches (20 min) ===
        
        Reading payments/processor.py...
        
        Found handle_transaction at line 45:
        
        def handle_transaction(transaction_type, data):
            if transaction_type == 'payment':
                validate_payment(data)
                process_payment(data)
                record_payment(data)
            elif transaction_type == 'refund':
                validate_refund(data)
                process_refund(data)
                record_refund(data)
            elif transaction_type == 'adjustment':
                validate_adjustment(data)
                process_adjustment(data)
            elif transaction_type == 'cancellation':
                validate_cancellation(data)
                process_cancellation(data)
        
        Operation branches identified:
        1. payment - validates, processes, records payment
        2. refund - validates, processes, records refund
        3. adjustment - validates, processes adjustment
        4. cancellation - validates, processes cancellation
        
        ✅ Step 1 complete
        
        === Step 2: Extract to Separate Functions (1-2 hours) ===
        
        Creating focused functions...
        
        [Shows code being created...]
        
        def handle_payment(payment_data):
            """Process a customer payment transaction"""
            validate_payment(payment_data)
            process_payment(payment_data)
            record_payment(payment_data)
        
        def handle_refund(refund_data):
            """Process a customer refund transaction"""
            validate_refund(refund_data)
            process_refund(refund_data)
            record_refund(refund_data)
        
        [... etc for all 4 operations ...]
        
        ✅ Step 2 complete - Created 4 new functions
        
        === Step 3: Update Call Sites (1-2 hours) ===
        
        Searching for all calls to handle_transaction...
        
        Found 8 call sites:
        1. api/routes.py line 123
        2. api/routes.py line 145
        3. api/webhooks.py line 67
        [... etc ...]
        
        Updating call sites...
        
        Before (api/routes.py:123):
        result = handle_transaction('payment', payment_info)
        
        After:
        result = handle_payment(payment_info)
        
        [... updates all 8 call sites ...]
        
        ✅ Step 3 complete - Updated 8 call sites
        
        === Step 4: Remove Original Function (30 min) ===
        
        Removing handle_transaction from payments/processor.py...
        
        ✅ Step 4 complete
        
        === Step 5: Run Tests ===
        
        Running test suite...
        
        tests/test_payments.py::test_payment_processing ✅ PASSED
        tests/test_payments.py::test_refund_processing ✅ PASSED
        tests/test_payments.py::test_adjustment ✅ PASSED
        tests/test_payments.py::test_cancellation ✅ PASSED
        tests/test_api.py::test_payment_endpoint ✅ PASSED
        [... 43 more tests ...]
        
        ✅ All 47 tests passing!
        
        === Verification ===
        
        ✅ No control parameters
        ✅ Each function has single purpose
        ✅ Clear, descriptive names
        ✅ All tests pass
        ✅ Functional cohesion achieved (7/7)
        
        Refactoring complete!
        Files changed:
        - payments/processor.py
        - api/routes.py
        - api/webhooks.py
        
        Ready to commit?
```

### Commit Changes

```
> Yes, create a commit

Claude: Creating commit...
        
        ✅ Committed:
        
        commit abc123def456
        Author: You <you@example.com>
        Date: Fri Nov 8 14:32:10 2025
        
            Refactor handle_transaction from logical to functional cohesion
            
            - Split handle_transaction into 4 focused functions
            - Eliminated control coupling (transaction_type parameter)
            - Each function now has single, clear purpose
            - All tests passing
            - Cohesion improved: 2/7 → 7/7
            
            Based on: Structured Design plan_01_handle_transaction.md
            Principle: "Each module should do ONE thing and do it well"
        
        Progress: 1/16 issues resolved (6%)
        
        Next critical issue: format_report (control coupling)
        Estimated time: 2-3 hours
        
        Continue with next issue?
```

### Continue or Pause

```
> Show me the progress report first

Claude: === REFACTORING PROGRESS ===
        
        Completed: 1/16 (6%)
        Time invested: ~2 hours
        Time remaining: ~40-50 hours
        
        Status by Priority:
        
        Critical (2 total):
        ✅ handle_transaction - DONE (2h)
        ⏳ format_report - NEXT (2-3h)
        
        High Priority (14 total):
        ⏳ initialize_system (3-4h)
        ⏳ create_customer_profile (2-3h)
        ⏳ process_user_order (1-2h)
        [... etc ...]
        
        Code Quality Improvements:
        Before: Avg cohesion 3.8/7, 16 issues
        After:  Avg cohesion 4.1/7, 15 issues (↑)
        
        Next Steps:
        1. Continue with format_report (critical)
        2. Take a break, resume later
        3. Create PR for review
        4. Re-analyze to see full impact
```

---

## Advanced Usage

### Re-analyze After Changes

```
> Re-run the analyzer to see our improvements

Claude: Running fresh analysis...
        
        Before (last analysis):
        - Average cohesion: 3.8/7
        - Critical issues: 2
        - High priority: 14
        
        After (current):
        - Average cohesion: 4.1/7 (↑ 8%)
        - Critical issues: 1 (↓ 50%)
        - High priority: 14
        
        Improvements:
        ✅ handle_transaction: 2/7 → 7/7 (MAJOR improvement)
        
        Keep going! You're making progress.
```

### Batch Processing

```
> Refactor all critical issues in one session

Claude: I'll work through both critical issues:
        1. format_report (2-3h)
        2. (already done: handle_transaction)
        
        Starting with format_report...
        [... processes automatically ...]
        
        ✅ All critical issues resolved!
        Total time: 4-5 hours
        Code quality significantly improved
```

### Create Pull Request

```
> Create a PR for these refactorings

Claude: Creating pull request...
        
        Title: Refactor payment processing to functional cohesion
        
        Description:
        ## Summary
        Refactored payment transaction handling to eliminate logical
        cohesion and control coupling issues.
        
        ## Changes
        - Split handle_transaction into 4 focused functions
        - Eliminated transaction_type control parameter
        - Updated 8 call sites
        - All tests passing
        
        ## Metrics
        - Cohesion improved: 2/7 → 7/7
        - Coupling reduced: removed control parameter
        - Based on Structured Design principles (Constantine & Yourdon)
        
        ## Testing
        ✅ 47 tests passing
        ✅ No regressions
        
        ✅ Pull request created: #123
        
        Link: https://github.com/yourorg/repo/pull/123
```

---

## Tips & Best Practices

### 1. Start with Critical Issues
```
> Focus on critical issues first - they have highest ROI
```

### 2. Work in Small Batches
```
> Let's do one issue at a time so I can review each change
```

### 3. Use Branches
```
> Create a feature branch for this refactoring work
```

### 4. Run Tests Frequently
```
> Run tests after each step to catch issues early
```

### 5. Review Before Committing
```
> Show me a diff of all changes before we commit
```

### 6. Track Progress
```
> Re-analyze after every 3 refactorings to track improvement
```

---

## Troubleshooting

### Tests Failing

```
> Tests are failing after the refactoring

Claude: Let me check what went wrong...
        
        [Analyzes test failures]
        
        Found the issue: Call site in api/webhooks.py line 89 
        still using old function name.
        
        Fixing...
        
        ✅ Fixed. Re-running tests...
        ✅ All tests passing now!
```

### Unsure About a Step

```
> I'm not sure about Step 3 - can you explain it more?

Claude: Of course! Step 3 is about updating all the places in your
        code that call the old function.
        
        Right now, code calls:
        handle_transaction('payment', data)
        
        After refactoring, we want:
        handle_payment(data)
        
        I'll search your entire codebase for all calls to 
        handle_transaction and update them one by one.
        
        Would you like me to show you each one before changing it?
```

### Want to Pause

```
> Let's stop here and resume tomorrow

Claude: No problem! Here's where we are:
        
        Completed: plan_01_handle_transaction ✅
        In progress: None
        Next: plan_02_format_report
        
        To resume tomorrow:
        1. Start Claude Code: `claude`
        2. Say: "Continue with plan_02_format_report"
        
        All your progress is committed and safe!
```

---

## Benefits Summary

### Time Savings
- **Manual refactoring**: 40-50 hours
- **With Claude Code**: 5-10 hours (hands-on) + 30-40 hours (automated)
- **Your time saved**: 30-40 hours! ⏰

### Quality Improvements
- ✅ Follows plans exactly
- ✅ Runs tests automatically
- ✅ Creates good commits
- ✅ Tracks progress
- ✅ Maintains consistency

### Learning Benefits
- 📚 Watch principles applied in real-time
- 🎓 Understand WHY changes are made
- 💡 Learn patterns for future coding
- 📖 Reference for your team

---

## Next Steps

1. **Install Claude Code** (5 minutes)
2. **Navigate to your project**
3. **Request analysis**
4. **Let Claude Code refactor**
5. **Review and commit**
6. **Repeat for next issue**
7. **Track improvement**
8. **Celebrate better code!**

---

## Support

Need help?
- Type `/help` in Claude Code for commands
- Ask Claude: "How do I...?"
- Review generated plans in `refactoring_plans/`
- Check principle reference in skill

---

**Claude Code + Structured Design Analyzer = Automated Code Quality Improvement!** 🚀
