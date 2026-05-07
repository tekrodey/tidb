# DDL Test Case Map

This file maps DDL-related test scenarios to their corresponding test files and functions.
Use this as a reference when writing or triaging DDL tests.

## Test File Locations

| Test Area | File Path | Test Function(s) |
|-----------|-----------|------------------|
| Create Table | `ddl/ddl_test.go` | `TestCreateTable`, `TestCreateTableWithLike` |
| Drop Table | `ddl/ddl_test.go` | `TestDropTable`, `TestDropTableIfExists` |
| Alter Table Add Column | `ddl/column_test.go` | `TestAddColumn`, `TestAddColumns` |
| Alter Table Drop Column | `ddl/column_test.go` | `TestDropColumn`, `TestDropColumns` |
| Alter Table Modify Column | `ddl/column_change_test.go` | `TestColumnChange`, `TestModifyColumn` |
| Add Index | `ddl/index_test.go` | `TestAddIndex`, `TestAddPrimaryKey` |
| Drop Index | `ddl/index_test.go` | `TestDropIndex`, `TestDropPrimaryKey` |
| Rename Table | `ddl/ddl_test.go` | `TestRenameTable`, `TestRenameTables` |
| Truncate Table | `ddl/ddl_test.go` | `TestTruncateTable` |
| Create Database | `ddl/db_test.go` | `TestCreateDatabase` |
| Drop Database | `ddl/db_test.go` | `TestDropDatabase` |
| Partition Table | `ddl/partition_test.go` | `TestPartitionTable`, `TestAlterTablePartition` |
| Foreign Key | `ddl/foreign_key_test.go` | `TestForeignKey`, `TestAddForeignKey` |
| Auto Increment | `ddl/ddl_test.go` | `TestAutoIncrement`, `TestAutoIncrementWithCache` |
| Default Value | `ddl/column_test.go` | `TestColumnDefaultValue` |
| Generated Column | `ddl/generated_column_test.go` | `TestGeneratedColumn` |
| View | `ddl/view_test.go` | `TestCreateView`, `TestDropView` |
| Sequence | `ddl/sequence_test.go` | `TestCreateSequence`, `TestAlterSequence` |
| Placement Policy | `ddl/placement_policy_test.go` | `TestCreatePlacementPolicy` |
| TTL | `ddl/ttl_test.go` | `TestAlterTTL`, `TestTTLInfoChange` |
| Schema Version | `ddl/schema_test.go` | `TestSchemaVersionError` |
| DDL Owner | `ddl/owner_test.go` | `TestDDLOwner`, `TestCampaignOwner` |
| DDL Reorg | `ddl/reorg_test.go` | `TestReorg`, `TestReorgWorker` |
| DDL Job Queue | `ddl/job_test.go` | `TestGetDDLJobs`, `TestCancelDDLJob` |

## Integration Test Locations

| Test Area | File Path |
|-----------|-----------|
| DDL Serial | `tests/integrationtest/testdata/ddl_serial_test` |
| DDL Suite | `tests/integrationtest/testdata/ddl_suite_test` |
| Alter Table | `tests/integrationtest/testdata/alter_table_test` |

## Notes

- DDL tests involving concurrent operations should use `TestDDLConcurrent` patterns.
- For failpoint-based DDL tests, see `.agents/skills/tidb-failpoint-test-runner/SKILL.md`.
- Reorg-related tests may require longer timeouts; use `testfailpoint` or adjust via session variables.
- When adding new DDL feature tests, prefer adding to the relevant `*_test.go` under `ddl/` package.
