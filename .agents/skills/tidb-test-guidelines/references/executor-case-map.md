# Executor Package Test Case Map

This document maps test functions in the `executor` package to their corresponding test files and descriptions, to assist with test triage and coverage analysis.

## File: executor/executor_test.go

| Test Function | Description |
|---|---|
| TestAdminCheckTable | Verifies ADMIN CHECK TABLE detects data inconsistencies |
| TestAdminCheckIndex | Verifies ADMIN CHECK INDEX detects index inconsistencies |
| TestAdminRecoverIndex | Verifies ADMIN RECOVER INDEX repairs missing index entries |
| TestAdminCleanupIndex | Verifies ADMIN CLEANUP INDEX removes orphan index entries |
| TestSelectWithoutFrom | Tests SELECT expressions without a FROM clause |
| TestSelectLimit | Tests LIMIT and OFFSET clauses in SELECT statements |
| TestSelectOrderBy | Tests ORDER BY clause behavior including NULLs handling |
| TestSelectGroupBy | Tests GROUP BY aggregation correctness |
| TestSelectHaving | Tests HAVING clause filtering on aggregated results |
| TestSelectDistinct | Tests DISTINCT keyword deduplication |

## File: executor/join_test.go

| Test Function | Description |
|---|---|
| TestJoin | Basic inner join correctness |
| TestJoinWithoutWhere | Join without WHERE clause (cross join behavior) |
| TestHashJoin | Hash join algorithm correctness |
| TestMergeJoin | Merge join algorithm correctness |
| TestIndexLookUpJoin | Index lookup join correctness |
| TestLeftJoin | LEFT OUTER JOIN correctness including NULL padding |
| TestRightJoin | RIGHT OUTER JOIN correctness including NULL padding |
| TestSemiJoin | Semi-join (IN subquery) correctness |
| TestAntiSemiJoin | Anti-semi-join (NOT IN subquery) correctness |

## File: executor/aggregate_test.go

| Test Function | Description |
|---|---|
| TestAggregation | General aggregation function correctness |
| TestStreamAgg | Stream aggregation algorithm correctness |
| TestHashAgg | Hash aggregation algorithm correctness |
| TestAggPushDown | Aggregation push-down optimization correctness |
| TestGroupConcatOrderBy | GROUP_CONCAT with ORDER BY clause |
| TestApproxCountDistinct | APPROX_COUNT_DISTINCT function accuracy |

## File: executor/write_test.go

| Test Function | Description |
|---|---|
| TestInsert | Basic INSERT correctness |
| TestInsertIgnore | INSERT IGNORE behavior on duplicate key |
| TestInsertOnDuplicateKey | INSERT ... ON DUPLICATE KEY UPDATE correctness |
| TestUpdate | Basic UPDATE correctness |
| TestUpdateMultiTable | Multi-table UPDATE correctness |
| TestDelete | Basic DELETE correctness |
| TestDeleteMultiTable | Multi-table DELETE correctness |
| TestReplace | REPLACE INTO correctness |

## Notes

- Tests marked with `// slow test` may be skipped in short mode via `-test.short`.
- Failpoint-dependent tests are listed separately in the failpoint skill references.
- For integration test mappings, see `tidb-integrationtest-recorder` skill.
