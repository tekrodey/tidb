# DistSQL Test Case Map

This document maps test scenarios to their corresponding test files and functions in the `distsql` package.

## Package Location
`distsql/`

## Test Files

| Test File | Test Function | Scenario |
|-----------|--------------|----------|
| `distsql/select_result_test.go` | `TestSelectResult` | Basic select result handling |
| `distsql/select_result_test.go` | `TestSelectResultWithMemTracker` | Memory tracking during select |
| `distsql/select_result_test.go` | `TestSelectResultClose` | Proper resource cleanup on close |
| `distsql/select_result_test.go` | `TestSelectResultWithCancel` | Context cancellation handling |
| `distsql/distsql_test.go` | `TestConstructRequest` | Building DistSQL requests |
| `distsql/distsql_test.go` | `TestHandleWithDynamicPruning` | Dynamic partition pruning |
| `distsql/distsql_test.go` | `TestBuildKeyRanges` | Key range construction |
| `distsql/distsql_test.go` | `TestScanWithConcurrency` | Concurrent scan operations |
| `distsql/chunk_row_codec_test.go` | `TestChunkRowCodec` | Chunk row encoding/decoding |
| `distsql/chunk_row_codec_test.go` | `TestDecodeProduceChunkWithDatums` | Datum-based chunk decoding |

## Scenario Categories

### Request Construction
- Building scan requests for table/index ranges
- Setting concurrency and fetch size parameters
- Applying pushed-down conditions

### Result Handling
- Streaming vs. non-streaming result consumption
- Partial result merging from multiple regions
- Error propagation from TiKV coprocessor

### Memory Management
- Tracking memory usage via `MemTracker`
- Releasing chunks after consumption
- OOM handling during large scans

### Cancellation & Timeout
- Propagating context cancellation to in-flight RPCs
- Deadline exceeded handling
- Graceful shutdown of result streams

## Notes
- Most integration-level DistSQL tests live in `executor/` and use `testkit`
- Unit tests in `distsql/` focus on codec and request-building logic
- For coprocessor push-down tests, see `executor-case-map.md`
