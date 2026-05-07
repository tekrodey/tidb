# Planner Package Test Case Map

This document maps test files and their corresponding test cases in the `planner` package.

## planner/core

| Test File | Test Function | Description |
|-----------|--------------|-------------|
| `planner/core/integration_test.go` | `TestIndexMerge` | Tests index merge path selection |
| `planner/core/integration_test.go` | `TestPushDownToTiFlash` | Tests predicate pushdown to TiFlash |
| `planner/core/integration_test.go` | `TestMPPJoin` | Tests MPP join planning |
| `planner/core/integration_test.go` | `TestPartitionPruning` | Tests partition pruning in planner |
| `planner/core/integration_test.go` | `TestSubquery` | Tests subquery planning and decorrelation |
| `planner/core/cbo_test.go` | `TestCBOWithoutAnalyze` | Tests cost-based optimization without stats |
| `planner/core/cbo_test.go` | `TestCBOWithAnalyze` | Tests cost-based optimization with stats |
| `planner/core/cbo_test.go` | `TestCBOIndexChoose` | Tests index selection via CBO |
| `planner/core/plan_test.go` | `TestDAGPlanBuilderSimpleCase` | Tests simple DAG plan construction |
| `planner/core/plan_test.go` | `TestDAGPlanBuilderJoin` | Tests join plan construction |
| `planner/core/plan_test.go` | `TestDAGPlanBuilderSubquery` | Tests subquery in DAG plan |
| `planner/core/plan_test.go` | `TestDAGPlanTopN` | Tests TopN operator planning |
| `planner/core/plan_test.go` | `TestDAGPlanBuilderAgg` | Tests aggregation plan construction |
| `planner/core/optimizer_test.go` | `TestSelectivity` | Tests selectivity estimation |
| `planner/core/optimizer_test.go` | `TestOuterJoinElimination` | Tests outer join elimination rule |
| `planner/core/optimizer_test.go` | `TestEliminateProjection` | Tests projection elimination |
| `planner/core/optimizer_test.go` | `TestMaxMinEliminate` | Tests max/min aggregate elimination |
| `planner/core/optimizer_test.go` | `TestBuildKeyInfo` | Tests key info derivation for plans |
| `planner/core/rule_join_reorder_test.go` | `TestJoinReorderDPv2` | Tests DP-based join reorder algorithm |
| `planner/core/rule_join_reorder_test.go` | `TestJoinReorderGreedy` | Tests greedy join reorder algorithm |
| `planner/core/stats_test.go` | `TestDeriveStats` | Tests statistics derivation through plan tree |
| `planner/core/stats_test.go` | `TestColumnPruning` | Tests column pruning optimization |

## planner/cascades

| Test File | Test Function | Description |
|-----------|--------------|-------------|
| `planner/cascades/integration_test.go` | `TestCascadesBasic` | Tests basic cascades planner functionality |
| `planner/cascades/transformation_rules_test.go` | `TestTransformationRules` | Tests logical transformation rules |
| `planner/cascades/implementation_rules_test.go` | `TestImplementationRules` | Tests physical implementation rules |

## Notes

- Integration tests in `planner/core/integration_test.go` require a running TiKV or mock store.
- CBO tests in `planner/core/cbo_test.go` may require `ANALYZE TABLE` to be run first.
- Use `testdata/` directories alongside test files for golden file comparisons.
- Run with `-record` flag to update golden files: `go test ./planner/core/ -record`
