# Node.js Weakness Log

ID: W01
Concept: Closures capture bindings, not frozen values (critical)
Observed misunderstanding: Q2 and Q7 describe closures as preserving variable values at the moment an async call is made and protecting them from mutation.
Correct mental model: A closure retains access to lexical bindings. It sees a captured variable's value when it runs, including later reassignment. Separate factory calls create separate bindings.
Evidence/source chapter: Checkpoint 01 Q2 and Q7; Chapter 2.
Remediation exercise: Predict a delayed callback after its captured variable changes, then contrast two separate factory invocations.
Status: open

ID: W02
Concept: CommonJS load order and shared module state (critical)
Observed misunderstanding: Q15 credits worker.js with the first counter load and gives an impossible mutation sequence, even though the final output is correct.
Correct mental model: The first require in app.js executes counter.js once; first.value then changes 0 to 2. worker.js gets the same cached object and adds 5, yielding 7. Later require returns that object without executing counter.js again.
Evidence/source chapter: Checkpoint 01 Q15; Chapter 3.
Remediation exercise: Trace a fresh three-module example statement by statement, marking first execution, cache hits, object identity, and each mutation.
Status: open

ID: W03
Concept: CLI argument parsing and package entry points
Observed misunderstanding: Q19 gives npm install --save without a package and does not show the requested module boundaries. Its argv[2] handling works when the path precedes the optional -v flag; the exam did not require the opposite order. The exam also did not require an installed bin command.
Correct mental model: If no external packages are used, there is nothing to install or save. A reusable CommonJS module can hold file loading and JSON parsing while the CLI handles arguments and output. For the chosen invocation, enforce or document path-first ordering.
Evidence/source chapter: Checkpoint 01 Q19; Chapter 4.
Remediation exercise: Split the CLI and loader into two CommonJS files, give valid npm setup steps, and document the accepted argument order.
Status: open

ID: W04
Concept: Exact asynchronous output and uncaught errors
Observed misunderstanding: Q16 writes Scheduled instead of scheduled and omits explicit abnormal process termination after the uncaught throw.
Correct mental model: Console output is case-sensitive. The next-tick callback runs after synchronous statements; its throw escapes the earlier try/catch, prints an uncaught exception, and exits abnormally.
Evidence/source chapter: Checkpoint 01 Q16; Chapter 2.
Remediation exercise: Predict the exact output and termination of a new next-tick example, then catch its error inside the callback.
Status: open
