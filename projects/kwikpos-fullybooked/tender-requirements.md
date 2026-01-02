# Tender Requirement ID Mapping

This document provides a comprehensive reference of all tender types used in the FullyBooked integration and their associated requirement field IDs. Each tender type has specific fields that must be captured during the transaction process.

## Overview

Tender requirements define the additional information that needs to be collected for each payment method. The requirement IDs map to specific fields in the `tblSaleTenderRequirement` table and are used in the export views for FullyBooked.

!!! info "Common Requirement ID:"
    Requirement ID `0` (Tendered Amount/Amount) is used across all tender types to capture the payment amount.

---

## Cash Tender

**Tender ID:** `1`

| Requirement ID | Field Name |
|----------------|------------|
| 59 | Remarks |
| 167 | Customer |
| 168 | TIN No. |
| 169 | Address |
| 0 | Tendered Amount |

---

## Credit Card

**Tender ID:** `2`

| Requirement ID | Field Name |
|----------------|------------|
| 1 | Credit Card No. |
| 2 | Name (Credit Card Holder) |
| 3 | Expiration Date |
| 4 | Approval Code |
| 14 | Credit Card Type |
| 77 | Remarks |
| 95 | Order No. |
| 96 | Payment Reference No. |
| 97 | Courier |
| 98 | Tracking No. |
| 99 | Shipping Fee |
| 170 | Customer |
| 171 | TIN No. |
| 172 | Address |
| 0 | Tendered Amount |

---

## Check

**Tender ID:** `3`

| Requirement ID | Field Name |
|----------------|------------|
| 5 | Bank |
| 6 | Cheque No. |
| 7 | Date |
| 78 | Remarks |
| 173 | Customer |
| 174 | TIN No. |
| 175 | Address |
| 0 | Amount |

---

## Exchange

**Tender ID:** `5`

| Requirement ID | Field Name |
|----------------|------------|
| 9 | Exchange No. |
| 0 | Amount |

---

## Gift Cheque

**Tender ID:** `6`

| Requirement ID | Field Name |
|----------------|------------|
| 10 | Gift Cheque No. |
| 79 | Remarks |
| 0 | Amount |

---

## GCash

**Tender ID:** `8`

| Requirement ID | Field Name |
|----------------|------------|
| 12 | Order No. |
| 13 | Payment Reference No. |
| 64 | Courier |
| 65 | Tracking No. |
| 66 | Shipping Fee |
| 80 | Remarks |
| 176 | Customer |
| 177 | TIN No. |
| 178 | Address |
| 0 | Amount |

---

## Others

**Tender ID:** `10`

| Requirement ID | Field Name |
|----------------|------------|
| 19 | Tender Name |
| 20 | Remarks |
| 179 | Customer |
| 180 | TIN No. |
| 181 | Address |
| 0 | Amount |

---

## FBEGC (FullyBooked E-Gift Certificate)

**Tender ID:** `12`

| Requirement ID | Field Name |
|----------------|------------|
| 25 | FBEGC No. |
| 26 | Trace No. |
| 83 | Remarks |
| 182 | Customer |
| 183 | TIN No. |
| 184 | Address |
| 0 | Amount |

---

## DragonPay

**Tender ID:** `13`

| Requirement ID | Field Name |
|----------------|------------|
| 27 | Order No. |
| 55 | Payment Reference No. |
| 56 | Courier |
| 57 | Tracking No. |
| 58 | Shipping Fee |
| 0 | Amount |

---

## CWT (Creditable Withholding Tax)

**Tender ID:** `15`

| Requirement ID | Field Name |
|----------------|------------|
| 29 | TIN No. |
| 30 | Payees Name |
| 31 | Period |
| 32 | ATC Code |
| 0 | Amount |

---

## Gifted

**Tender ID:** `16`

| Requirement ID | Field Name |
|----------------|------------|
| 33 | Voucher No. |
| 84 | Remarks |
| 185 | Customer |
| 186 | TIN No. |
| 187 | Address |
| 0 | Amount |

---

## Lazada

**Tender ID:** `21`

| Requirement ID | Field Name |
|----------------|------------|
| 38 | Confirmation No. |
| 67 | Payment Mode |
| 0 | Amount |

---

## Giftway

**Tender ID:** `22`

| Requirement ID | Field Name |
|----------------|------------|
| 39 | Voucher No. |
| 85 | Remarks |
| 188 | Customer |
| 189 | TIN No. |
| 190 | Address |
| 0 | Amount |

---

## Shopee

**Tender ID:** `23`

| Requirement ID | Field Name |
|----------------|------------|
| 40 | Order No. |
| 68 | Payment Mode |
| 69 | Courier |
| 0 | Amount |

---

## COD (Cash on Delivery)

**Tender ID:** `31`

| Requirement ID | Field Name |
|----------------|------------|
| 48 | Order No. |
| 52 | Courier |
| 53 | Tracking No. |
| 54 | Shipping Fee |
| 126 | Remarks |
| 0 | Amount |

---

## WeChat

**Tender ID:** `32`

| Requirement ID | Field Name |
|----------------|------------|
| 49 | Reference No. |
| 86 | Remarks |
| 191 | Customer |
| 192 | TIN No. |
| 193 | Address |
| 0 | Amount |

---

## Alipay

**Tender ID:** `33`

| Requirement ID | Field Name |
|----------------|------------|
| 50 | Reference No. |
| 87 | Remarks |
| 194 | Customer |
| 195 | TIN No. |
| 196 | Address |
| 0 | Amount |

---

## GrabMart

**Tender ID:** `34`

| Requirement ID | Field Name |
|----------------|------------|
| 51 | Reference No. |
| 88 | Remarks |
| 197 | Customer |
| 198 | TIN No. |
| 199 | Address |
| 0 | Amount |

---

## Bank Transfer

**Tender ID:** `36`

!!! warning "Not Implemented:"
    This tender type is not yet implemented in the export query.

| Requirement ID | Field Name |
|----------------|------------|
| 70 | Order No. |
| 71 | Bank Name |
| 72 | Payment Reference No. |
| 73 | Courier |
| 74 | Tracking No. |
| 75 | Shipping Fee |
| 0 | Amount |

---

## GLife

**Tender ID:** `39`

| Requirement ID | Field Name |
|----------------|------------|
| 100 | Order No. |
| 101 | Payment Reference No. |
| 102 | Courier |
| 103 | Tracking No. |
| 104 | Shipping Fee |
| 105 | Remarks |
| 0 | Amount |

---

## ShopeePay

**Tender ID:** `40`

| Requirement ID | Field Name |
|----------------|------------|
| 106 | Payment Reference No. |
| 107 | Remarks |
| 203 | Customer |
| 204 | TIN No. |
| 205 | Address |
| 0 | Amount |

---

## Store Credit

**Tender ID:** `43`

| Requirement ID | Field Name |
|----------------|------------|
| 127 | Order No. |
| 128 | Payment Reference No. |
| 129 | Courier |
| 130 | Tracking No. |
| 131 | Shipping Fee |
| 132 | Remarks |
| 0 | Amount |

---

## Virtual GC (Gift Certificate)

**Tender ID:** `44`

| Requirement ID | Field Name |
|----------------|------------|
| 133 | Order No. |
| 134 | Payment Reference No. |
| 135 | Courier |
| 136 | Tracking No. |
| 137 | Shipping Fee |
| 138 | Remarks |
| 0 | Amount |

---

## Cashback

**Tender ID:** `45`

| Requirement ID | Field Name |
|----------------|------------|
| 139 | Order No. |
| 140 | Payment Reference No. |
| 141 | Courier |
| 142 | Tracking No. |
| 143 | Shipping Fee |
| 144 | Remarks |
| 0 | Amount |

---

## Digital Wallet

**Tender ID:** `46`

| Requirement ID | Field Name |
|----------------|------------|
| 145 | Order No. |
| 146 | Payment Reference No. |
| 147 | Courier |
| 148 | Tracking No. |
| 149 | Shipping Fee |
| 150 | Remarks |
| 0 | Amount |

---

## BDO - Debit

**Tender ID:** `47`

| Requirement ID | Field Name |
|----------------|------------|
| 151 | Remarks |
| 152 | Customer |
| 153 | TIN No. |
| 154 | Address |
| 0 | Amount |

---

## Metrobank - Debit

**Tender ID:** `48`

| Requirement ID | Field Name |
|----------------|------------|
| 163 | Remarks |
| 164 | Customer |
| 165 | TIN No. |
| 166 | Address |
| 0 | Amount |

---

## BDO E-Wallet

**Tender ID:** `49`

| Requirement ID | Field Name |
|----------------|------------|
| 159 | Remarks |
| 160 | Customer |
| 161 | TIN No. |
| 162 | Address |
| 0 | Amount |

---

## Metrobank E-Wallet

**Tender ID:** `50`

| Requirement ID | Field Name |
|----------------|------------|
| 163 | Remarks |
| 164 | Customer |
| 165 | TIN No. |
| 166 | Address |
| 0 | Amount |

---

## TikTok

**Tender ID:** `62`

!!! danger "Pending Implementation:"
    This tender type has not been implemented yet. Requirement IDs need to be provided by FullyBooked.

| Requirement ID | Field Name |
|----------------|------------|
| TBD | Order No. |
| TBD | Payment Mode |
| TBD | Courier |
| 0 | Amount |

---

## Usage Notes

### Working with Tender Requirements

When modifying tender requirement mappings:

1. **Identify the Tender ID** - Determine which payment method you're working with
2. **Locate Requirement IDs** - Reference this document for the specific field IDs needed
3. **Update View Logic** - Modify the SQL view to include/exclude requirement fields
4. **Test Thoroughly** - Verify that all required fields are captured correctly

### Common Field Patterns

Several requirement fields appear across multiple tender types:

- **Customer Information**: Customer, TIN No., Address
- **Order Details**: Order No., Payment Reference No.
- **Shipping Information**: Courier, Tracking No., Shipping Fee
- **General**: Remarks, Amount

### Adding New Tender Types

When FullyBooked introduces a new payment method:

1. Obtain the Tender ID and all requirement field IDs from FullyBooked
2. Add the new tender type to this documentation
3. Update the `dbo.View_tblSaleTenderRequirement` view to include the new mappings
4. Test the export with sample transactions using the new tender type

