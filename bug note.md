# Bug Notes

## Project: Buggy python code

This document records the bugs identified in `student_utils.py`, the evidence from the failing tests, their causes, and the fixes applied.

| Bug | Evidence / Failed Test | Cause | Fix |
|---|---|---|---|
| Average Calculation | Returned `135.0` instead of `90.0` for `[80, 90, 100]`; a single mark caused `ZeroDivisionError`. | Dividing by `len(marks) - 1` instead of `len(marks)`. | Change the denominator to `len(marks)`. |
| Pass Boundary | `is_passing(40)` returned `False` instead of `True`. | Used `>` instead of `>=` to compare marks against `PASS_MARK`. | Change the condition to `mark >= PASS_MARK`. |
| Grade Ordering | `get_grade(95)` returned `"First"` instead of `"Distinction"`. | The `average >= 60` condition was checked before `average >= 90`. | Check the distinction condition before the first-grade condition. |

## RED → FIX → GREEN

### RED
The original buggy implementation was tested against nine unit tests. The tests identified incorrect average calculations, division by zero, an incorrect passing boundary, and incorrect grade classification.

### FIX
The bugs were corrected in `student_utils.py`. The test cases and expected results were kept unchanged.

### GREEN
The same nine unit tests were executed again after the fixes. The expected result was that all nine tests passed with no failures or errors.

## Conclusion
Unit testing helped identify the errors in the original implementation. Correcting the implementation while keeping the tests unchanged demonstrated the RED → FIX → GREEN debugging cycle.
