# Statistics Package Test Case Map

This document maps test scenarios to their corresponding test functions in the `statistics` package.

## Unit Tests (`statistics/*_test.go`)

| Scenario | Test Function | File |
|----------|--------------|------|
| CMSketch basic operations | `TestCMSketch` | `cmsketch_test.go` |
| CMSketch merge | `TestCMSketchCopy` | `cmsketch_test.go` |
| TopN operations | `TestTopN` | `top_n_test.go` |
| TopN merge | `TestTopNMerge` | `top_n_test.go` |
| Histogram basic | `TestHistogram` | `histogram_test.go` |
| Histogram less row count | `TestHistogramLessRowCount` | `histogram_test.go` |
| Histogram merge | `TestMergeHistogram` | `histogram_test.go` |
| FMSketch basic | `TestFMSketch` | `fmsketch_test.go` |
| FMSketch merge | `TestFMSketchMerge` | `fmsketch_test.go` |
| Sample collector | `TestSampleCollector` | `sample_test.go` |
| Column stats | `TestColumnStats` | `statistics_test.go` |
| Index stats | `TestIndexStats` | `statistics_test.go` |
| Stats table | `TestStatsTable` | `statistics_test.go` |
| Pseudo stats | `TestPseudoTable` | `statistics_test.go` |
| Stats build | `TestBuild` | `builder_test.go` |

## Integration Tests (`statistics/handle/*_test.go`)

| Scenario | Test Function | File |
|----------|--------------|------|
| Analyze table | `TestAnalyzeTable` | `handle_test.go` |
| Auto analyze | `TestAutoAnalyze` | `handle_test.go` |
| Stats update | `TestStatsUpdate` | `handle_test.go` |
| Stats cache | `TestStatsCache` | `handle_test.go` |
| Stats load | `TestStatsLoad` | `handle_test.go` |
| DDL handler | `TestDDLHandler` | `ddl_handler_test.go` |
| Stats feedback | `TestStatsFeedback` | `feedback_test.go` |
| Stats dump | `TestDumpStatsBuckets` | `dump_test.go` |
| Stats load JSON | `TestLoadStatsFromJSON` | `dump_test.go` |
| Extended stats | `TestExtendedStats` | `extended_stats_test.go` |
| Column stats usage | `TestColumnStatsUsage` | `handle_test.go` |

## Notes

- Statistics tests often require a real TiKV backend for accurate row count estimation tests
- Use `testkit.NewTestKit` for integration-style tests in the handle package
- CMSketch and histogram tests can run without TiKV
- Auto-analyze tests may be flaky due to timing; use `require.Eventually` where appropriate
