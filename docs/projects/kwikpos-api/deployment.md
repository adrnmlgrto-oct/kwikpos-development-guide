# Deployment Architecture

## Infrastructure

- **Location:** Installed on individual POS machines acting as local servers
- **Application Server:** Apache Tomcat 10.0 servlet container
- **Network:** Local network access for nearby kiosks
- **Integration:** Direct connection with Chase POS application
- **Database:** Direct MS SQL Server database connection

## Deployment Characteristics

- **Scope:** Single store deployment
- **Isolation:** Each installation serves one POS terminal
- **Network:** Local LAN communication (`0.0.0.0`)
- **Availability:** Must be running whenever kiosks are operational

## Configuration

- POS machine-specific settings
- Kiosk connection parameters
- Legacy POS integration settings
- Network and security configuration
