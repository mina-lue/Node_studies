# Checkpoint 01 evaluation: Chapters 1-4

Learner: Minalu Mesele
Completed and evaluated: 2026-09-27
Submission: NODEJS_EXAM-CHECKPOINT-01-CH01-04 - Answers.txt

| Section | Score |
| --- | ---: |
| A: Foundations | 28.5/30 |
| B: Mechanisms | 22/25 |
| C: Code reading | 23/25 |
| D: Application | 17.5/20 |
| **Total** | **91/100** |

Result: **NOT YET MASTERED**. The score clears 90%, but W01 and W02 remain open critical weaknesses and remediation/transfer have not yet been passed.

## Regrade record

On 2026-09-27, the original 86/100 was rechecked against the actual question wording. The revised score is 91/100. Q7 gained 0.5 because its main server-design comparison was substantially correct; Q9 gained 0.5 because it correctly described reuse through require.cache despite imprecise internals; Q13 gained 0.5 because its explanation was enough to support the correct output; Q15 gained 0.5 because the correct output and execution count deserved more credit; Q16 gained 0.5 because it correctly identified the async catch boundary and fix; and Q19 gained 2.5 because neither flag ordering nor an installed bin command was specified, and its single-file CLI otherwise meets most required behavior. No critical weakness was silently cleared.

## Per-question grading

1. **3.5/4.** Correct: REPL expansion/purpose and the node command. Missing: the exact requested script command is 'node app.js', not just 'node <path/to/file>'. Model: node alone starts the REPL; node app.js runs that file. Follow-up: write both commands exactly.
2. **5/6.** Correct: first-class/higher-order functions, callbacks, and lexical scope surviving an outer call. Incorrect: closures do not freeze values when an async call is scheduled or prevent mutation. Model: a closure retains bindings and sees their current values when invoked. Follow-up: predict a callback after its captured variable is reassigned (W01).
3. **5/5.** Correct: undefined, null, undeclared names versus missing properties, equality, falsy values, and truthy empty containers. Model: an absent property reads as undefined; an undeclared identifier normally raises ReferenceError. No follow-up needed.
4. **5/5.** Correct: module kinds, require/module/module.exports/exports, and default empty export. Model: exports initially aliases module.exports, which require returns. No follow-up needed.
5. **4/4.** Correct: file/directory paths, process.argv first two elements, and Buffer. Model: user arguments start after the executable and script entries. No follow-up needed.
6. **6/6.** Correct: JSON restrictions, conversion methods, package metadata/dependencies, and semver positions. Model: JSON syntax is stricter than JavaScript object literal syntax; semantic versions mark breaking, compatible feature, and fix changes. No follow-up needed.
7. **5.5/7.** Correct: process/thread CPU and memory costs, context switching, waiting, and callback benefits. Incorrect: not all I/O goes to the OS kernel; some operations use libuv workers. Closures do not preserve frozen state, and low overhead is relative, not guaranteed. Model: the JavaScript loop coordinates pending operations while the OS or libuv does I/O; callbacks observe captured bindings when invoked. Follow-up: classify network versus filesystem I/O and trace a changed captured variable (W01).
8. **4.5/5.** Correct: timer delay, CPU starvation, workload fit. Incorrect unit: 1000 means milliseconds, not microseconds. Model: a timer becomes eligible after its delay and waits for the loop to run it. Follow-up: explain why a busy loop delays a 0-ms timer.
9. **5.5/6.** Correct: synchronous first load, reuse through require.cache, shared state, factory objects, and conditional require. Minor imprecision: require.cache holds module records keyed by resolved filename, rather than only export values. Model: importers of the same resolved module normally share its exported object; calling a factory can create fresh objects. Follow-up: compare shared object and factory examples.
10. **3.5/4.** Correct: blocking versus asynchronous filesystem calls and why the outer catch cannot see a later throw. Missing: spell out the failure branch: err contains an Error and data is generally unavailable; success conventionally has err = null and data. Model: inspect err inside the callback before using data. Follow-up: write both readFile callback branches.
11. **3/3.** Correct: browser latency, AMD, Browserify, and unsupported system APIs. Model: bundling cannot give a browser access to OS-only facilities such as fs. No follow-up needed.
12. **5/5.** Correct exact output and separate closure/timer reasoning. Model: each factory call has its own count binding; timers run after synchronous statements. No follow-up needed.
13. **5/5.** Correct exact output and sufficiently explains own versus inherited value lookup. Model: right.increment reads inherited 80 and then creates an own right.value = 81, leaving the prototype at 80. No required follow-up.
14. **4/4.** Correct values, alias explanation, and fixes. Model: rebinding exports leaves module.exports unchanged. No follow-up needed.
15. **3/4.** Correct exact output, object identity, and one execution. Incorrect explanation: app.js, not worker.js, performs the first counter require; mutation order is 0 -> 2 -> 7, not 0 -> 5 -> 2 -> 7. Model: CommonJS execution is synchronous and the same resolved file normally supplies the same cached object. Follow-up: trace a new three-module program statement by statement (W02).
16. **3/4.** Correct: synchronous-versus-next-tick order, the outer catch boundary, and the fix inside the callback. Incorrect: first line is lowercase 'scheduled'. Missing: after 'scheduled', 'end', 'tick', the uncaught Error: boom is reported with a stack trace and the process exits abnormally; original catch never logs. Model: the callback runs on a later stack outside the scheduling call's catch. Follow-up: exact-output and termination trace of a new next-tick callback (W04).
17. **3/3.** Correct entry file and version classifications. Model: main chooses lib/start.js; ^2.3.4 allows compatible versions below 3.0.0. No follow-up needed.
18. **5/6.** Correct nested dependency layout, chosen copies, and distinct cache identities. Missing: trace fallback search beyond each package's own node_modules, including the application's and ancestor node_modules folders. Model: resolution starts nearest the requiring file and walks outward. Follow-up: add a report without a local formatter and trace its search.
19. **6.5/8.** Correct: a workable one-file CLI when invoked as 'node inspect-config.js path [-v]', asynchronous readFile, JSON.parse catch, filesystem and JSON error reporting, exit codes, relevant package metadata, and no third-party dependency. Incorrect/missing: 'npm install --save' without a package is not a valid dependency-saving step; the requested module boundaries are not shown because all logic is in one file. Model: when package.json is written manually and there are no dependencies, no npm install command is needed. A separate CommonJS loader module would show a reusable boundary. Supporting '-v' before the path, adding a bin field, and including err.message would improve the utility, but were not specified and receive no deduction. Follow-up: refactor loading into a module and state the correct npm setup steps (W03).
20. **6/6.** Correct tilde range, npm outdated columns, prototype risks, and precautions. Model: ~1.4.2 permits 1.4.x fixes only; String.prototype changes can affect unrelated code. No follow-up needed.

## Next action

Review W01-W04 in NODEJS_WEAKNESSES.md. Then request a **new closed-book remediation and transfer assessment** on closure binding changes, CommonJS execution order, exact next-tick error behavior, and robust CLI design. It must use unfamiliar examples. Do not advance to Chapter 5 until the mastery standard is met.
