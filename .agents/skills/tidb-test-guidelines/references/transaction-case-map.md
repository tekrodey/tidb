# Transaction Test Case Map

This document maps transaction-related test scenarios to their corresponding test files and functions in the TiDB codebase.

## Package: `sessiontxn`

| Test Scenario | File | Function |
|---|---|---|
| Optimistic transaction basic | `sessiontxn/txn_manager_test.go` | `TestOptimisticTxnBasic` |
| Pessimistic transaction basic | `sessiontxn/txn_manager_test.go` | `TestPessimisticTxnBasic` |
| Transaction retry on conflict | `sessiontxn/txn_manager_test.go` | `TestTxnRetryOnConflict` |
| Savepoint rollback | `sessiontxn/txn_manager_test.go` | `TestSavepointRollback` |
| Auto-commit behavior | `sessiontxn/txn_manager_test.go` | `TestAutoCommit` |

## Package: `store/tikv`

| Test Scenario | File | Function |
|---|---|---|
| 2PC commit | `store/tikv/2pc_test.go` | `TestTwoPhaseCommit` |
| Prewrite conflict | `store/tikv/2pc_test.go` | `TestPrewriteConflict` |
| Lock resolution | `store/tikv/lock_test.go` | `TestResolveLock` |
| Async commit | `store/tikv/2pc_test.go` | `TestAsyncCommit` |
| One-phase commit | `store/tikv/2pc_test.go` | `TestOnePhaseCommit` |
| Large transaction | `store/tikv/2pc_test.go` | `TestLargeTxn` |

## Package: `executor`

| Test Scenario | File | Function |
|---|---|---|
| BEGIN/COMMIT/ROLLBACK | `executor/executor_test.go` | `TestTransactionDML` |
| SELECT FOR UPDATE | `executor/executor_test.go` | `TestSelectForUpdate` |
| Deadlock detection | `executor/executor_test.go` | `TestDeadlock` |
| Isolation level read committed | `executor/executor_test.go` | `TestIsolationLevelRC` |
| Stale read | `executor/stale_txn_test.go` | `TestStaleTxnRead` |

## Package: `session`

| Test Scenario | File | Function |
|---|---|---|
| Transaction context reset | `session/session_test.go` | `TestTransactionContextReset` |
| Implicit transaction | `session/session_test.go` | `TestImplicitTransaction` |
| Transaction with DDL | `session/session_test.go` | `TestTxnWithDDL` |
| SET transaction isolation | `session/session_test.go` | `TestSetTransactionIsolation` |

## Notes

- Pessimistic transactions require `tidb_txn_mode = 'pessimistic'` to be set.
- Async commit and one-phase commit tests may require real TiKV; see `tidb-realtikv-runner` skill.
- Deadlock tests often use failpoints; see `tidb-failpoint-test-runner` skill.
- Stale read tests depend on timestamp oracle (TSO) behavior and may be timing-sensitive.
