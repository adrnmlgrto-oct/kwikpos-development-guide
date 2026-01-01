# Overview

**Purpose:** Bridge layer connecting self-ordering kiosks to legacy POS applications

KwikPOS API serves as an on-premise adapter that enables modern self-ordering kiosks to communicate seamlessly with legacy POS applications, particularly Chase POS, without requiring modifications to the existing POS software.

## Tech Stack

- **Framework:** Spring Boot 3.5.4
- **Runtime:** Java 17
- **Deployment:** Apache Tomcat 10.0
- **Deployment Location:** On-premise POS machine

## Database Configuration

### Database Schemas

KwikPOS API connects to the following database schemas used by the legacy POS application:

- **`posdb`** - Primary database schema for POS operations
- **`orderdb`** - Database schema for order management

These schemas are part of the legacy POS application's database structure and are accessed by the API adapter to facilitate communication between modern kiosks and the legacy POS system.

### Key Tables for Order Processing

The API primarily writes to the following tables in the `orderdb` schema when processing orders from kiosks:

#### `dbo.SALESORDER`
- **Purpose:** Stores order header information
- **Key Data:** Order reference number, customer details, order timestamp, total amount, order status
- **Usage:** Each order from a kiosk creates a new record in this table with a unique order reference number

**Order Statuses:**

- **`"PENDING"`** - Initial status when order is just sent in from the kiosk
    - This is the status the POS looks up to identify new orders waiting to be retrieved by the cashier
    - Orders remain in this status until the cashier retrieves them at the counter
    - **Auto-Cleanup:** Pending orders that exceed 1 hour are automatically deleted
    - **Use Case:** When customers send in an order and select "pay via cash" but don't arrive at the counter to complete payment

- **`"RETRIEVED"`** - Order has been fulfilled and completed
    - Set when the order sent by the kiosk to the POS has been retrieved by the cashier
    - Indicates the customer has paid and the order has been fulfilled
    - **Final status** for completed orders

#### `dbo.SALESORDER_ITEM`
- **Purpose:** Stores individual items within an order
- **Key Data:** Item details, quantity, price, modifiers, linked to order reference number
- **Usage:** Multiple records created per order - one for each item ordered
- **Relationship:** Links to `dbo.SALESORDER` via order reference number

#### `dbo.SALESORDER_PAYMENT`
- **Purpose:** Stores payment information for cashless orders
- **Key Data:** Payment method, amount, transaction details, payment status
- **Usage:** **Currently not in active use** - Reserved for future cashless payment integration
- **Status:** Payment integration with legacy POS requires additional modifications on the POS side (auto-print, event execution) which are not yet implemented
- **Note:** Only applicable for `'CASHLESS'` order types where payment is processed on the self-ordering kiosk

**Important:** As of the current implementation, only `dbo.SALESORDER` and `dbo.SALESORDER_ITEM` are actively used. The `dbo.SALESORDER_PAYMENT` table exists but is not utilized until cashless payment integration is completed on the legacy POS application.

### Database Sequences

#### `dbo.REG_SO_SEQ`
- **Purpose:** Sequence generator for sales order reference numbers
- **Usage:** Generates unique, sequential order reference numbers for orders from kiosks
- **Naming Convention:** "REG" prefix indicates regular/standard kiosk orders
- **Future Considerations:** The naming pattern allows for potential addition of separate sequences for different order sources (e.g., *Grab Food*, *Food Panda*) if needed in the future, though this is not currently implemented

## System Architecture

The following sequence diagram illustrates how the KwikPOS API processes orders from kiosks to the legacy POS system:

![KwikPOS API Sequence Diagram](../../assets/images/kwikpos-api-sequence.svg)

## Key Features

### Kiosk Integration
- API server for self-ordering kiosk integration
- Real-time order transmission from kiosks to POS terminals
- Support for modern kiosk interfaces

### Data Transformation
- Data transformation layer between modern kiosks and legacy POS systems
- Format conversion and data mapping
- Protocol adaptation

### Legacy POS Compatibility
- Compatibility layer for Chase POS integration
- Direct integration with legacy POS applications

### Local Server
- Runs as local server on POS machine
- Handles requests from nearby kiosks
- Low-latency local network communication

## Main Highlight

**This adapter enables our modern self-ordering kiosk products to seamlessly communicate with legacy POS applications, particularly Chase POS, and possibly other POS applications if requested.**

This is the key value proposition:

- Modern kiosk interface maintained
- Seamless integration
- Minimal disruption to existing operations

## Quick Links

- [Responsibilities](responsibilities.md) - Core system responsibilities
- [Deployment Architecture](deployment.md) - Infrastructure and deployment details
- [Development Setup](setup.md) - Local environment configuration
- [Project Structure](structure.md) - Code organization and architecture
- [Development Tasks](development.md) - Common development workflows
- [Testing](testing.md) - Testing strategies and practices
- [Architecture Considerations](architecture.md) - Design principles and patterns
- [Troubleshooting](troubleshooting.md) - Common issues and solutions
- [Roadmap & Planned Work](roadmap.md) - Future features and integrations

## Getting Help

If you encounter issues:

- **Technical Questions:** Reach out to the development team, or you may contact the original author of the codebase via email (<a href="mailto:adrnmlgrto.dev@gmail.com" target="_blank">adrnmlgrto.dev@gmail.com</a>)
- **Integration Issues:** Consult with technical support or helpdesk
- **Deployment Problems:** Contact on-site technical support or helpdesk
- **Architecture Questions:** Review adapter patterns or consult senior developers
- **Kiosk Issues:** Check with KwikPOS Pro development team
