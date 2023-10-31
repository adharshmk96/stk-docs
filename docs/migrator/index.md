---
id: migrator
sidebar_position: 2
title: Migrator
sidebar_label: Migrator
---

- CLI tool for generating migration files and running migrations
- Supported databases
  - sqlite3 (default)

### Get started

Generate migration files ( optinally name it and fill )

```bash
stk migrator generate -n "initial migration" --fill
```

migrate up ( applies all migrations, or specified number of steps )

```bash
stk migrator up
```

migrate down ( applies all down migrations, or specified number of steps )

```bash
stk migrator down
```

History - Shows history of applied migrations

```bash
stk migrator history
```

### Cleanup Commands

Clean - Delete all unapplied migrations

```bash
stk migrator clean
```

Purge - Delete all migration files and remove database migration log table ( Doesn't delete the migrations )

```bash
stk migrator purge
```
