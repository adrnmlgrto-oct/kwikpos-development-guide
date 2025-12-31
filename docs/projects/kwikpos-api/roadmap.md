# Roadmap & Planned Work

This document outlines planned features, integrations, and improvements for KwikPOS API. These items represent future work that needs to be implemented.

## Planned Features

### KwikPOS Terminal (Fine-Dine Handheld Device) Support

**Priority:** High<br />
**Status:** Planned

**Description:**
Modify or extend this project to support KwikPOS Terminal, a handheld ordering device for waiters in fine-dining restaurant setups. While technically still functioning as a kiosk-like ordering device, it's designed for waiter-assisted table ordering rather than self-service.

**Product Context:**

- KwikPOS Terminal is in the current product lineup
- Used in fine-dining restaurant environments where waiters take orders at individual tables
- Handheld device (likely tablet-based) that connects to the POS system
- Similar data flow to kiosks but different UX and use case

**User Stories:**

- As a waiter, I want to take table orders on a handheld device so that I can capture orders directly at the table
- As a restaurant manager, I want orders from terminals to sync with the POS so that kitchen can receive them immediately
- As a waiter, I want to assign orders to specific table numbers so that we can track which orders belong to which tables

**Technical Approach:**

- Evaluate whether to extend current KwikPOS API or create a separate terminal-specific adapter
- Implement table management functionality (table numbers, table status)
- Add support for order assignment to tables and waiters
- Consider authentication/authorization for individual waiter accounts
- Implement order modification flows (add items, remove items, split bills)
- Support for dine-in specific features (course sequencing, special requests)

**Key Differences from Self-Service Kiosks:**

- Table number assignment required
- Waiter identification/tracking needed
- More complex order modification workflows
- May need split billing support
- Course/timing management (appetizers, mains, desserts)
- Special dietary requests and customizations

**Acceptance Criteria:**

- Terminal devices can authenticate and connect to POS
- Orders can be assigned to specific tables
- Waiter identification is captured with orders
- Order modifications are supported
- Integration with existing Chase POS works seamlessly
- Table status tracking (occupied, available, reserved)
- Performance is acceptable for restaurant peak hours

**Resources:**

- Product specs for KwikPOS Terminal (to be provided)
- UX/UI designs for terminal interface
- Requirements gathering with operations team

**Notes:**

- Coordinate with KwikPOS Terminal product team for specific requirements
- Consider whether this should be a separate project or extension of current API
- May need to handle different network configurations (Wi-Fi for mobile devices)

---

## POS System Compatibility

### Integration with Other POS Providers
**Priority:** Medium<br />
**Status:** Planned

**Description:**
Support integration with POS systems beyond Chase POS to enable selling KwikPOS kiosk products to clients who want to use their existing POS provider without switching systems. This expands the market reach for standalone kiosk sales.

**Current Support:** Chase POS only<br />
**Planned Support:** Multiple POS providers (TBD based on sales requirements)

**Business Context:**

- Enables selling kiosk products independently without requiring clients to switch their entire POS system
- Allows clients to keep their current POS provider while adding modern kiosk ordering capabilities
- Expands addressable market for kiosk-only sales
- No definite timeline yet, but likely to be requested once sales team starts selling kiosks independently

**Integration Requirements:**

- POS system API documentation or database schema access
- Understanding of POS system's data models for menu items, orders, and transactions
- Network connectivity requirements between kiosk and POS
- Authentication/authorization mechanisms for the target POS system
- Transaction handling and error recovery patterns specific to each POS

**Technical Challenges:**

- Each POS system has different data structures and APIs
- May require custom transformation logic for each POS provider
- Different authentication/security models across POS systems
- Varying levels of API maturity and documentation quality
- Testing complexity with multiple POS environments
- Maintaining backward compatibility with Chase POS while adding new providers

**Implementation Approach:**

- Design an abstraction layer to support multiple POS providers
- Create a plugin/adapter pattern for each POS system
- Implement a configuration system to specify which POS provider is being used
- Build transformation layers specific to each POS provider's data format
- Develop comprehensive testing framework for multi-POS support
- Document integration requirements for each supported POS system

**Testing Plan:**

- Test order flow end-to-end with each POS provider
- Verify data transformation accuracy for menu items and orders
- Test error scenarios (POS offline, network issues, timeout handling)
- Validate concurrent order handling from multiple kiosks
- Performance testing under load for each POS provider
- Security and authentication testing
- Regression testing to ensure Chase POS integration remains stable

**Notes:**

- This will be triggered by sales team requirements - no specific timeline yet
- Priority and specific POS providers will be determined based on client demands
- Consider creating a priority list of POS systems based on market research

---

## Data Transformation Enhancements

### Calorie Count (kcal) Inclusion in Items Endpoint Response
**Priority:** High<br />
**Status:** In Progress

**Description:**
Add calorie count information to the items endpoint response to comply with Quezon City Local Government Unit (LGU) Ordinance No. *SP-3254 S-2024*, which requires food establishments to display calorie information on all menus including electronic/digital menus such as kiosks.

**Regulatory Context:**
Quezon City Calorie Labeling Ordinance (*SP-3254 S-2024*) mandates restaurants and food businesses to include calorie counts (in `kcal`) per serving on all menus, including:

- Printed menus
- Digital/electronic menus (including kiosks)
- Menu boards

**Implementation Timeline per Ordinance:**

- **Phase 1 (Dec 20, 2025):** Food chains with 5 or more branches within Quezon City
- **Phase 2 (2026):** Businesses with 2 or more branches, plus hotels
- **Phase 3 (2027):** All food businesses (with some exemptions for micro-enterprises)

**Current Behavior:**
Items endpoint returns menu items without calorie information. The POS database has a column for calorie count, and now it returns it successfully, and the only remaining thing to do are validations and testing

**Planned Enhancement:**

- Locate and identify the calorie count column in the POS database schema
- Add calorie count field to the item DTO (Data Transfer Object)
- Update SQL queries in mapper to include calorie column
- Include `calories` field in API response
- Ensure proper data type handling (integer or decimal)
- Handle null/missing calorie values gracefully

**Current Progress:**

- ✅ Initial investigation started - identifying calorie column in POS database
- ✅ Column mapping and SQL query updates already done
- ⏳ Still needs: Testing, validation, and deployment

**Implementation Details:**

- Database column identified: `[posdb].[dbo].[ITEMS].[calories]`
- Response field name: `calories` (standardize naming)
- Handle cases where calorie data is not available (null handling)
- Unit of measurement: kilocalories (`kcal`) per serving
- Data type: Integer or Decimal or Double (verify with POS database schema)

**Testing Requirements:**

- Verify calorie data is correctly retrieved from POS database
- Confirm response format matches kiosk frontend expectations
- Test with items that have calorie data
- Test with items that don't have calorie data (null handling)
- Validate data accuracy against known menu items
- Performance testing to ensure no significant impact on response time
- Integration testing with kiosk application

**Acceptance Criteria:**

- Items endpoint includes calorie count in response
- Calorie value matches POS database value
- Null/missing values are handled gracefully
- API documentation updated to reflect new field
- Kiosk frontend can display calorie information correctly
- No breaking changes to existing API consumers

**Resources:**

- [Quezon City Ordinance SP-3254 S-2024](https://quezoncity.gov.ph/wp-content/uploads/2024/04/SP-3254-S-2024.pdf)
- [QC Calorie Labeling IRR](https://quezoncity.gov.ph/wp-content/uploads/2025/01/IRR_Calorie-Labeling-Ordinance.pdf)
- [PNA Article on QC Guidelines](https://www.pna.gov.ph/articles/1242973)
- [PhilStar: How QC's rule will change menus](https://www.philstar.com/nation/2025/02/03/2418191/how-qcs-calorie-labeling-rule-will-change-restaurant-menus)

**Notes:**

- **IMPORTANT:** Work on this has already been started and is partially complete
- Next developer needs to validate, confirm, and test the implementation
- Coordinate with kiosk frontend team to ensure proper display of calorie information
- This is a **compliance requirement** with legal deadlines - prioritize accordingly
- May need to work with clients to ensure their menu items have calorie data populated in POS
- Consider adding API versioning if this is a breaking change

**Next Steps:**

1. Validate the database column mapping is correct
2. Update DTOs to include calorie field
3. Test thoroughly with real POS data
4. Update API documentation
5. Coordinate with frontend team for kiosk UI updates
6. Plan deployment timeline to meet Phase 1 deadline (Dec 20, 2025)

---

## Notes for Future Developers

### General Context

This project was personally started by myself, and its currently what I would call a "good" and flexible project that can adapt to requirement changes.

Technically, this started to allow backwards compatibility with our modern self-ordering kiosk products to send orders to existing clients with their legacy POS devices.

Do note that it might be updated in the future where you would need to integrate other POS provider's applications to allow our own products to still be sold.

### On-Premise Deployment Considerations
- The setting up and deployment would technically be handled by the helpdesk support teams. Do coordinate with them for these kinds of deployments with clients.

### Key Contacts
- **Helpdesk Support:** Tyrese

### Things to Keep in Mind
- **Always** confirm the modifications whether if it would be possible for us to do, or the change would be on the POS side.
- **Always** update the team lead or the project manager if the modifications requested after deployment needs to be billed or charged before implementing.

---

## Timeline & Prioritization

### Q4 2025 / Q1 2026 (Immediate Priority)
- **Calorie Count Implementation** - MUST complete before Phase 1 deadline (Dec 20, 2025)
  - Complete database column mapping validation
  - Finalize SQL query updates
  - Testing and validation
  - Deployment to individual client store branches with KwikPOS API

### 2026 (As Needed)
- **KwikPOS Terminal Support** - Timeline TBD based on product launch schedule
  - Requirements gathering and technical design
  - Implementation of table management features
  - Waiter authentication and order assignment
  - Testing with actual terminal devices

### Future (No Specific Timeline)
- **Multi-POS Provider Support** - Will be triggered by sales team requirements
  - Determine which POS systems to support based on client demand
  - Design abstraction layer for multi-POS compatibility
  - Implement adapters for priority POS systems
  - Testing and validation with each POS provider

### Ongoing
- Bug fixes and technical improvements as identified
- Performance optimizations
- Security updates and patches

---

**Last Updated:** December 31, 2025<br />
**Updated By:** Adrian Melegrito (Original Developer)
