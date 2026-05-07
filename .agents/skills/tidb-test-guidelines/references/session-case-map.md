# Session Package Test Case Map

This file maps test scenarios to their corresponding test functions in the `session` package.

## Session Lifecycle

| Scenario | Test File | Test Function |
|----------|-----------|---------------|
| Session creation and initialization | `session_test.go` | `TestSession` |
| Session close and cleanup | `session_test.go` | `TestSessionClose` |
| Session variable inheritance | `session_test.go` | `TestSessionVars` |
| Concurrent session access | `session_test.go` | `TestConcurrentSession` |

## Transaction Management

| Scenario | Test File | Test Function |
|----------|-----------|---------------|
| Begin/Commit/Rollback | `session_test.go` | `TestTransaction` |
| Auto-commit behavior | `session_test.go` | `TestAutoCommit` |
| Pessimistic transactions | `session_test.go` | `TestPessimisticTransaction` |
| Optimistic transactions | `session_test.go` | `TestOptimisticTransaction` |
| Transaction retry | `session_test.go` | `TestTransactionRetry` |
| Savepoints | `session_test.go` | `TestSavepoint` |

## System Variables

| Scenario | Test File | Test Function |
|----------|-----------|---------------|
| Set/Get system variables | `session_test.go` | `TestSysVars` |
| Scope validation (global vs session) | `session_test.go` | `TestSysVarScope` |
| Variable persistence across reconnect | `session_test.go` | `TestSysVarPersist` |
| SQL mode handling | `session_test.go` | `TestSQLMode` |

## Authentication & Privileges

| Scenario | Test File | Test Function |
|----------|-----------|---------------|
| User login and authentication | `session_test.go` | `TestAuth` |
| Privilege checks on DDL | `session_test.go` | `TestPrivilegeDDL` |
| Privilege checks on DML | `session_test.go` | `TestPrivilegeDML` |
| Role-based access control | `session_test.go` | `TestRBAC` |

## Prepared Statements

| Scenario | Test File | Test Function |
|----------|-----------|---------------|
| Prepare and Execute | `session_test.go` | `TestPrepare` |
| Prepared statement cache | `session_test.go` | `TestPreparedStmtCache` |
| Binary protocol | `session_test.go` | `TestBinaryProtocol` |
| Parameter binding | `session_test.go` | `TestParamBinding` |

## Schema Handling

| Scenario | Test File | Test Function |
|----------|-----------|---------------|
| Schema version check | `session_test.go` | `TestSchemaVersion` |
| Schema change during transaction | `session_test.go` | `TestSchemaChangeDuringTxn` |
| Information schema queries | `session_test.go` | `TestInfoSchema` |
