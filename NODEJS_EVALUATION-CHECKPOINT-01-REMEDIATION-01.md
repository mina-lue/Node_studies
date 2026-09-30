# Checkpoint 01 remediation evaluation

Submitted and evaluated: 2026-09-30
Exam: NODEJS_EXAM-CHECKPOINT-01-REMEDIATION-01.txt

| Part | Score |
| --- | ---: |
| I: Focused remediation | 45/46 |
| II: Transfer | 52.5/54 |
| **Total** | **97.5/100** |

Result: **MASTERED**. The numerical threshold is met, all four logged
weaknesses were explained and applied to unfamiliar examples, and no critical
weakness remains open.

Before this evaluation was finalized, the learner removed an accidental
annotation from the Q8 package.json example. The corrected answer was graded
as submitted; no other Q8 answer content changed.

## Question-by-question grading

1. **8/8.** Correct: closure retains the variable binding, later changes are visible, and separate factory calls have separate bindings. Missing: nothing. Model: callbacks read the current binding when invoked. No follow-up needed. W01 evidence.
2. **11.5/12.** Correct output: sync, 7, 13, with the right timing and separate state. Minor error: value is a lexical variable, not a property on either returned object. Model: bump and report close over value; the object contains only those methods. Follow-up: identify own properties versus captured variables. W01 evidence.
3. **10/10.** Correct output: 3 3 3. The const binding created inside each loop iteration is a valid repair. Model: each stored function closes over its own iteration binding. No follow-up needed. W01 transfer evidence.
4. **15.5/16.** Correct exact output, initial load in app.js, all mutations, cache hits, and shared identity. Minor imprecision: the cached module contains an export reference; mutating count does not rewrite a cached value. Model: both modules export or receive the same mutable object. Follow-up: distinguish module record from exported object. W02 evidence.
5. **13.5/14.** Correct exact output, one module execution, shared exported factory identity, separate returned objects, and a valid shared-object alternative. Minor imprecision: the exported function is reused; each returned object is new. Model: module caching and factory call results are different layers of identity. Follow-up: compare two require calls with two factory calls. W02 transfer evidence.
6. **9.5/10.** Correct order before, after, later; outer catch does not run and the uncaught throw ends the process abnormally. Minor presentation error: Error: stop is the subsequent error report, not a console.log line before it. Model: nextTick callback runs on a later stack. Follow-up: label console output and error report separately. W04 evidence.
7. **10/10.** Correct inner catch, retained synchronous logs, exact revised output, and explanation of catch scope. Model: the catch must be active in the callback where the throw occurs. No follow-up needed. W04 transfer evidence.
8. **19.5/20.** Correct: valid package manifest after the requested correction, command bin mapping, separate CommonJS CLI and loader, npm link for a manually created package, both flag orders, asynchronous read, JSON parsing, reported errors, and nonzero exit codes. Minor gap: an unknown flag such as -x can be treated as a file path, so invalid options are not identified as such. Model: validate recognized options separately from positional paths. Follow-up: reject an unknown option explicitly in a future CLI. W03 transfer evidence.

## Weakness resolution and next unit

- W01 mastered: Q1-Q3 explain mutable captured bindings and apply them to separate factories and a loop.
- W02 mastered: Q4-Q5 correctly trace first execution, cache hits, shared exports, and separate factory results.
- W03 mastered: Q8 uses a valid manifest, bin mapping, npm link, and separate modules.
- W04 mastered: Q6-Q7 predict exact asynchronous order, abnormal termination, and a working inner catch.

Checkpoint 01 is complete. The next unit is Chapters 5-7. Read those
chapters actively before requesting the next assessment.
