# Store Package Test Case Map

This document maps test scenarios to their corresponding test functions in the `store` package.

## store/tikv

| Scenario | Test File | Test Function |
|----------|-----------|---------------|
| Basic KV get/put operations | store/tikv/kv_test.go | TestBasicKVOperations |
| Transaction commit | store/tikv/txn_test.go | TestTxnCommit |
| Transaction rollback | store/tikv/txn_test.go | TestTxnRollback |
| Optimistic lock conflict | store/tikv/txn_test.go | TestOptimisticLockConflict |
| Pessimistic lock acquire | store/tikv/pessimistic_test.go | TestPessimisticLockAcquire |
| Pessimistic lock deadlock | store/tikv/pessimistic_test.go | TestPessimisticDeadlock |
| Snapshot read | store/tikv/snapshot_test.go | TestSnapshotRead |
| Coprocessor request | store/tikv/coprocessor_test.go | TestCoprocessorRequest |
| Region cache refresh | store/tikv/region_cache_test.go | TestRegionCacheRefresh |
| Region split handling | store/tikv/region_cache_test.go | TestRegionSplit |
| Retry on region error | store/tikv/retry_test.go | TestRetryOnRegionError |
| Backoff strategy | store/tikv/backoff_test.go | TestBackoffStrategy |
| GC worker lifecycle | store/tikv/gc_worker_test.go | TestGCWorkerLifecycle |
| Safe point update | store/tikv/gc_worker_test.go | TestSafePointUpdate |
| 1PC transaction | store/tikv/txn_test.go | TestOnePCTransaction |
| Async commit | store/tikv/txn_test.go | TestAsyncCommit |

## store/mockstore

| Scenario | Test File | Test Function |
|----------|-----------|---------------|
| Mock store basic ops | store/mockstore/mockstore_test.go | TestMockStoreBasicOps |
| Mock coprocessor | store/mockstore/mocktikv/cop_handler_test.go | TestMockCoprocessor |
| Mock cluster split | store/mockstore/cluster_test.go | TestMockClusterSplit |
| Unistore transaction | store/mockstore/unistore/txn_test.go | TestUnistoreTransaction |

## store/driver

| Scenario | Test File | Test Function |
|----------|-----------|---------------|
| Driver open store | store/driver/driver_test.go | TestDriverOpenStore |
| TxnDriver begin | store/driver/txn_test.go | TestTxnDriverBegin |
| Error mapping | store/driver/error_test.go | TestErrorMapping |

## Notes

- Tests under `store/tikv` that require a real TiKV cluster should use the `tidb-realtikv-runner` skill.
- Mock store tests can run without external dependencies and are suitable for unit testing.
- For integration scenarios involving both store and executor layers, refer to `executor-case-map.md`.
