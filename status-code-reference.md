# Status Code Reference

This page documents the status codes used in sales records across different POS systems in the KwikPOS ecosystem.

## Overview

Status codes are used to identify the type of transaction or operation recorded in the sales database. Different POS systems use different status code mappings, which is important to understand when working with sales data, reports, or integrations.

## Legacy POS (Chase)

The following status codes are used in Chase POS sales records:

| Status Code | Transaction Type |
|:-----------:|:-----------------|
| 1 | Regular Transaction |
| 3 | Post Void |
| 4 | Suspend |
| 5 | Regular Transaction *(Failed to Print EJ / Timed Out During Transaction)* |
| 6 | Change Fund |
| 7 | Cash Pickup |
| 8 | Tender Declaration |
| 9 | X-Read |
| 10 | Z-Read |
| 11 | Print Tempo |
| 99 | Refund |
| 501 | Spot Audit |
| 502 | X-Read *(All Cashiers)* |

### Usage Notes

- **Status Code 1** represents the most common transaction type - regular customer sales
- **Status Code 5** indicates a regular transaction that encountered printing issues but was still completed
- **Status Codes 9, 10, 502** are reporting operations (X-Read, Z-Read)
- **Status Codes 6, 7, 8** are cash management operations
- **Status Code 99** is used for customer refunds
- **Status Codes 501** is for audit operations

## KwikPOS Pro

The following status codes are used in KwikPOS Pro sales records:

| Status Code | Transaction Type |
|:-----------:|:-----------------|
| 1 | Regular Transaction |
| 2 | Post Void |

### Usage Notes

- KwikPOS Pro uses a simplified status code system compared to Chase POS
- **Status Code 1** represents regular customer sales transactions
- **Status Code 2** represents voided transactions

## Important Considerations

### When Working with Sales Data

When querying or analyzing sales data across different POS systems:

1. **Be aware of the POS system in use** - Different clients may be using different POS systems
2. **Filter appropriately** - When calculating sales totals, you typically want to filter for regular transactions (Status Code 1)
3. **Exclude non-sales operations** - Operations like X-Reads, Z-Reads, and cash management should be excluded from sales reports
4. **Handle voids correctly** - Post voids (Status Code 3 in Chase POS, Status Code 2 in KwikPOS Pro) should be handled appropriately in calculations

### Code Examples

**Filtering Regular Transactions (Chase POS):**
```sql
-- Include only regular sales transactions
SELECT * FROM posdb.dbo.SALES1
WHERE [status] IN (1, 5);  -- Regular transactions including those with print issues
```

**Filtering Regular Transactions (KwikPOS Pro):**
```sql
-- Include only regular sales transactions
SELECT * FROM sales_m2
WHERE "status" = 1;  -- Regular transactions only
```

**Excluding Non-Sales Operations (Chase POS):**
```sql
-- Exclude reporting and cash management operations
SELECT * FROM posdb.dbo.SALES1
WHERE [status] NOT IN (6, 7, 8, 9, 10, 11, 501, 502);
```

### Cross-System Compatibility

When building features that work across both Chase POS and KwikPOS Pro:

- **Regular Transactions:** Status Code 1 is consistent across both systems
- **Voided Transactions:** Chase POS uses 3, KwikPOS Pro uses 2
- **System-Specific Codes:** Be aware that Chase POS has many operation types that don't exist in KwikPOS Pro

## Related Documentation

- [KwikPOS Live Overview](projects/kwikpos-live/index.md) - Backend system documentation
- [KwikPOS API Overview](projects/kwikpos-api/index.md) - Kiosk adapter documentation
- [FullyBooked (WebExt)](projects/kwikpos-fullybooked/index.md) - Integration of KwikPOS & FullyBooked documentation

---

**Note:** This reference is maintained based on production systems as of the last update date. If you notice discrepancies or new status codes, please update this documentation and notify the development team.
