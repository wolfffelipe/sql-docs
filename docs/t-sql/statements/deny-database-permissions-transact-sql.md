---
title: "DENY Database Permissions (Transact-SQL)"
description: DENY Database Permissions (Transact-SQL)
author: VanMSFT
ms.author: vanto
ms.date: "02/21/2019"
ms.service: sql
ms.subservice: t-sql
ms.topic: reference
helpviewer_keywords:
  - "DENY statement, databases"
  - "permissions [SQL Server], databases"
  - "database permissions [SQL Server], denying"
  - "denying permissions [SQL Server], databases"
dev_langs:
  - "TSQL"
monikerRange: ">=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current||=fabric"
---
# DENY Database Permissions (Transact-SQL)

[!INCLUDE [sql-asdb-asdbmi-asa-pdw-fabricse-fabricdw](../../includes/applies-to-version/sql-asdb-asdbmi-asa-pdw-fabricse-fabricdw.md)]

Denies permissions on a database in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

:::image type="icon" source="../../includes/media/topic-link-icon.svg" border="false"::: [Transact-SQL syntax conventions](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)

## Syntax

```syntaxsql
DENY <permission> [ ,...n ]
    TO <database_principal> [ ,...n ] [ CASCADE ]
    [ AS <database_principal> ]

<permission> ::=
    permission | ALL [ PRIVILEGES ]

<database_principal> ::=
    Database_user
  | Database_role
  | Application_role
  | Database_user_mapped_to_Windows_User
  | Database_user_mapped_to_Windows_Group
  | Database_user_mapped_to_certificate
  | Database_user_mapped_to_asymmetric_key
  | Database_user_with_no_login
```

[!INCLUDE[sql-server-tsql-previous-offline-documentation](../../includes/sql-server-tsql-previous-offline-documentation.md)]

## Arguments

*permission*
Specifies a permission that can be denied on a database. For a list of the permissions, see the Remarks section later in this topic.

ALL
This option does not deny all possible permissions. Denying ALL is equivalent to denying the following permissions: BACKUP DATABASE, BACKUP LOG, CREATE DATABASE, CREATE DEFAULT, CREATE FUNCTION, CREATE PROCEDURE, CREATE RULE, CREATE TABLE, and CREATE VIEW.

PRIVILEGES
Included for ISO compliance. Does not change the behavior of ALL.

CASCADE
Indicates that the permission will also be denied to principals to which the specified principal granted it.

AS \<database_principal>
Specifies a principal from which the principal executing this query derives its right to deny the permission.

*Database_user*
Specifies a database user.

*Database_role*
Specifies a database role.

*Application_role*
**Applies to**: [!INCLUDE[sql2008-md](../../includes/sql2008-md.md)] and later, [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].

Specifies an application role.

*Database_user_mapped_to_Windows_User*
Specifies a database user mapped to a Windows user.

*Database_user_mapped_to_Windows_Group*
Specifies a database user mapped to a Windows group.

*Database_user_mapped_to_certificate*
Specifies a database user mapped to a certificate.

*Database_user_mapped_to_asymmetric_key*
Specifies a database user mapped to an asymmetric key.

*Database_user_with_no_login*
Specifies a database user with no corresponding server-level principal.

## Remarks

A database is a securable contained by the server that is its parent in the permissions hierarchy. The most specific and limited permissions that can be denied on a database are listed in the following table, together with the more general permissions that include them by implication.

|Database permission|Implied by database permission|Implied by server permission|
|-------------------------|------------------------------------|----------------------------------|
|ADMINISTER DATABASE BULK OPERATIONS<br/>**Applies to:** [!INCLUDE[ssSDS_md](../../includes/sssds-md.md)].|CONTROL|CONTROL SERVER|
|ALTER|CONTROL|ALTER ANY DATABASE|
|ALTER ANY APPLICATION ROLE|ALTER|CONTROL SERVER|
|ALTER ANY ASSEMBLY|ALTER|CONTROL SERVER|
|ALTER ANY ASYMMETRIC KEY|ALTER|CONTROL SERVER|
|ALTER ANY CERTIFICATE|ALTER|CONTROL SERVER|
|ALTER ANY COLUMN ENCRYPTION KEY|ALTER|CONTROL SERVER|
|ALTER ANY COLUMN MASTER KEY DEFINITION|ALTER|CONTROL SERVER|
|ALTER ANY CONTRACT|ALTER|CONTROL SERVER|
|ALTER ANY DATABASE AUDIT|ALTER|ALTER ANY SERVER AUDIT|
|ALTER ANY DATABASE DDL TRIGGER|ALTER|CONTROL SERVER|
|ALTER ANY DATABASE EVENT NOTIFICATION|ALTER|ALTER ANY EVENT NOTIFICATION|
|ALTER ANY DATABASE EVENT SESSION<br /> **Applies to**: [!INCLUDE [ssazure-sqldb](../../includes/ssazure-sqldb.md)].|ALTER|ALTER ANY EVENT SESSION|
|ALTER ANY DATABASE SCOPED CONFIGURATION<br /> **Applies to**: [!INCLUDE[sssql16-md](../../includes/sssql16-md.md)] and later, [!INCLUDE[ssSDS](../../includes/sssds-md.md)].|CONTROL|CONTROL SERVER|
|ALTER ANY DATASPACE|ALTER|CONTROL SERVER|
|ALTER ANY EXTERNAL DATA SOURCE|ALTER|CONTROL SERVER|
|ALTER ANY EXTERNAL FILE FORMAT|ALTER|CONTROL SERVER|
|ALTER ANY EXTERNAL LIBRARY <br /> **Applies to**: [!INCLUDE [sssql17-md](../../includes/sssql17-md.md)].|CONTROL|CONTROL SERVER |
|ALTER ANY FULLTEXT CATALOG|ALTER|CONTROL SERVER|
|ALTER ANY MASK|CONTROL|CONTROL SERVER|
|ALTER ANY MESSAGE TYPE|ALTER|CONTROL SERVER|
|ALTER ANY REMOTE SERVICE BINDING|ALTER|CONTROL SERVER|
|ALTER ANY ROLE|ALTER|CONTROL SERVER|
|ALTER ANY ROUTE|ALTER|CONTROL SERVER|
|ALTER ANY SECURITY POLICY<br /> **Applies to**: [!INCLUDE[sssql16-md](../../includes/sssql16-md.md)] and later, [!INCLUDE [ssazure-sqldb](../../includes/ssazure-sqldb.md)].|CONTROL|CONTROL SERVER|
|ALTER ANY SCHEMA|ALTER|CONTROL SERVER|
|ALTER ANY SERVICE|ALTER|CONTROL SERVER|
|ALTER ANY SYMMETRIC KEY|ALTER|CONTROL SERVER|
|ALTER ANY USER|ALTER|CONTROL SERVER|
|AUTHENTICATE|CONTROL|AUTHENTICATE SERVER|
|BACKUP DATABASE|CONTROL|CONTROL SERVER|
|BACKUP LOG|CONTROL|CONTROL SERVER|
|CHECKPOINT|CONTROL|CONTROL SERVER|
|CONNECT|CONNECT REPLICATION|CONTROL SERVER|
|CONNECT REPLICATION|CONTROL|CONTROL SERVER|
|CONTROL|CONTROL|CONTROL SERVER|
|CREATE AGGREGATE|ALTER|CONTROL SERVER|
|CREATE ASSEMBLY|ALTER ANY ASSEMBLY|CONTROL SERVER|
|CREATE ASYMMETRIC KEY|ALTER ANY ASYMMETRIC KEY|CONTROL SERVER|
|CREATE CERTIFICATE|ALTER ANY CERTIFICATE|CONTROL SERVER|
|CREATE CONTRACT|ALTER ANY CONTRACT|CONTROL SERVER|
|CREATE DATABASE|CONTROL|CREATE ANY DATABASE|
|CREATE DATABASE DDL EVENT NOTIFICATION|ALTER ANY DATABASE EVENT NOTIFICATION|CREATE DDL EVENT NOTIFICATION|
|CREATE DEFAULT|ALTER|CONTROL SERVER|
|CREATE FULLTEXT CATALOG|ALTER ANY FULLTEXT CATALOG|CONTROL SERVER|
|CREATE FUNCTION|ALTER|CONTROL SERVER|
|CREATE MESSAGE TYPE|ALTER ANY MESSAGE TYPE|CONTROL SERVER|
|CREATE PROCEDURE|ALTER|CONTROL SERVER|
|CREATE QUEUE|ALTER|CONTROL SERVER|
|CREATE REMOTE SERVICE BINDING|ALTER ANY REMOTE SERVICE BINDING|CONTROL SERVER|
|CREATE ROLE|ALTER ANY ROLE|CONTROL SERVER|
|CREATE ROUTE|ALTER ANY ROUTE|CONTROL SERVER|
|CREATE RULE|ALTER|CONTROL SERVER|
|CREATE SCHEMA|ALTER ANY SCHEMA|CONTROL SERVER|
|CREATE SERVICE|ALTER ANY SERVICE|CONTROL SERVER|
|CREATE SYMMETRIC KEY|ALTER ANY SYMMETRIC KEY|CONTROL SERVER|
|CREATE SYNONYM|ALTER|CONTROL SERVER|
|CREATE TABLE|ALTER|CONTROL SERVER|
|CREATE TYPE|ALTER|CONTROL SERVER|
|CREATE VIEW|ALTER|CONTROL SERVER|
|CREATE XML SCHEMA COLLECTION|ALTER|CONTROL SERVER|
|DELETE|CONTROL|CONTROL SERVER|
|EXECUTE|CONTROL|CONTROL SERVER|
|EXECUTE ANY EXTERNAL SCRIPT <br /> **Applies to**: [!INCLUDE[ssSQL15_md](../../includes/sssql16-md.md)].|CONTROL|CONTROL SERVER|
|INSERT|CONTROL|CONTROL SERVER|
|KILL DATABASE CONNECTION<br /> **Applies to**: [!INCLUDE [ssazure-sqldb](../../includes/ssazure-sqldb.md)].|CONTROL|ALTER ANY CONNECTION|
|REFERENCES|CONTROL|CONTROL SERVER|
|SELECT|CONTROL|CONTROL SERVER|
|SHOWPLAN|CONTROL|ALTER TRACE|
|SUBSCRIBE QUERY NOTIFICATIONS|CONTROL|CONTROL SERVER|
|TAKE OWNERSHIP|CONTROL|CONTROL SERVER|
|UNMASK|CONTROL|CONTROL SERVER|
|UPDATE|CONTROL|CONTROL SERVER|
|VIEW ANY COLUMN ENCRYPTION KEY|CONTROL|VIEW ANY DEFINITION|
|VIEW ANY MASTER KEY DEFINITION|CONTROL|VIEW ANY DEFINITION|
|VIEW DATABASE STATE|CONTROL|VIEW SERVER STATE|
|VIEW DEFINITION|CONTROL|VIEW ANY DEFINITION|

## Permissions

The principal that executes this statement (or the principal specified with the AS option) must have CONTROL permission on the database or a higher permission that implies CONTROL permission on the database.

If you are using the AS option, the specified principal must own the database.

## Examples

### A. Denying permission to create certificates

The following example denies `CREATE CERTIFICATE` permission on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to user `MelanieK`.

```sql
USE AdventureWorks2012;
DENY CREATE CERTIFICATE TO MelanieK;
GO
```

### B. Denying REFERENCES permission to an application role

The following example denies `REFERENCES` permission on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to application role `AuditMonitor`.

**Applies to**: [!INCLUDE[sql2008-md](../../includes/sql2008-md.md)] and later, [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)].

```sql
USE AdventureWorks2012;
DENY REFERENCES TO AuditMonitor;
GO
```

### C. Denying VIEW DEFINITION with CASCADE

The following example denies `VIEW DEFINITION` permission on the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database to user `CarmineEs` and to all principals to which `CarmineEs` has granted `VIEW DEFINITION` permission.

```sql
USE AdventureWorks2012;
DENY VIEW DEFINITION TO CarmineEs CASCADE;
GO
```

## See Also

- [sys.database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)
- [sys.database_principals](../../relational-databases/system-catalog-views/sys-database-principals-transact-sql.md)
- [CREATE DATABASE](../../t-sql/statements/create-database-transact-sql.md)
- [GRANT](../../t-sql/statements/grant-transact-sql.md)
- [Permissions](../../relational-databases/security/permissions-database-engine.md)
- [Principals](../../relational-databases/security/authentication-access/principals-database-engine.md)
