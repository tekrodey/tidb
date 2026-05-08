# Expression Package Test Case Map

This document maps test scenarios to their corresponding test files and functions in the `expression` package.

## Builtin Functions

| Scenario | Test File | Test Function |
|----------|-----------|---------------|
| String functions (CONCAT, SUBSTR, etc.) | `expression/builtin_string_test.go` | `TestConcatFunc`, `TestSubstringFunc` |
| Math functions (ABS, CEIL, FLOOR, etc.) | `expression/builtin_math_test.go` | `TestAbsFunc`, `TestCeilFunc` |
| Date/Time functions (NOW, DATE_ADD, etc.) | `expression/builtin_time_test.go` | `TestNowFunc`, `TestDateAddFunc` |
| Control flow (IF, IFNULL, CASE) | `expression/builtin_control_test.go` | `TestIfFunc`, `TestIfNullFunc` |
| Comparison functions (GREATEST, LEAST) | `expression/builtin_compare_test.go` | `TestGreatestFunc`, `TestLeastFunc` |
| Encryption functions (MD5, SHA1, AES) | `expression/builtin_encryption_test.go` | `TestMD5Func`, `TestSHA1Func` |
| JSON functions (JSON_EXTRACT, etc.) | `expression/builtin_json_test.go` | `TestJSONExtractFunc` |
| Cast functions | `expression/builtin_cast_test.go` | `TestCastFunc` |
| Miscellaneous functions (SLEEP, UUID) | `expression/builtin_miscellaneous_test.go` | `TestSleepFunc` |

## Expression Evaluation

| Scenario | Test File | Test Function |
|----------|-----------|---------------|
| Constant folding | `expression/constant_propagation_test.go` | `TestConstantPropagation` |
| Expression evaluation with NULL | `expression/expression_test.go` | `TestEvaluateExprWithNull` |
| Column expression | `expression/column_test.go` | `TestColumn` |
| Scalar function cloning | `expression/scalar_function_test.go` | `TestScalarFuncClone` |
| Expression type inference | `expression/typeinfer_test.go` | `TestInferType` |

## Aggregation

| Scenario | Test File | Test Function |
|----------|-----------|---------------|
| COUNT aggregation | `expression/aggregation/agg_test.go` | `TestCount` |
| SUM/AVG aggregation | `expression/aggregation/agg_test.go` | `TestSumAvg` |
| GROUP_CONCAT | `expression/aggregation/agg_test.go` | `TestGroupConcat` |
| Window functions | `expression/aggregation/window_func_test.go` | `TestWindowFunc` |

## Schema & Column Resolution

| Scenario | Test File | Test Function |
|----------|-----------|---------------|
| Schema column lookup | `expression/schema_test.go` | `TestSchema` |
| Column pruning | `expression/column_test.go` | `TestColumnPruning` |

## Notes
- Most expression tests use `testkit` for SQL-level testing
- Builtin function tests often use `types.MakeDatums` for input construction
- Use `expression.NewFunctionInternal` for unit-level function testing
- Vectorized expression tests are co-located with their scalar counterparts
