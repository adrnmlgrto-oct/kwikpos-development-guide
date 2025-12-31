# Troubleshooting

## Common Issues

### Build Failures

**Symptoms:** Maven build fails or produces errors

**Solutions:**

- Verify JDK 17 is active: `java -version`
- Clean Maven cache: `mvn clean`
- Update dependencies: `mvn dependency:resolve`

### Connection Issues

**Symptoms:** Kiosks cannot reach the API server

**Solutions:**

- Verify kiosk can reach the API server
- Check firewall settings
- Ensure correct port configuration
- Test network connectivity

### POS Integration Issues

**Symptoms:** Orders not appearing in POS system

**Solutions:**

- Verify POS system is running
- Check POS connection settings
- Review transformation logic
- Check POS system logs

### Tomcat Deployment Issues

**Symptoms:** Application fails to deploy or start

**Solutions:**

- Ensure using Tomcat 10.0 (not 9.0)
- Check Tomcat logs in logs/catalina.out
- Verify WAR file compatibility
- Ensure port is available

## Getting Additional Help

If issues persist:

- **Technical Questions:** Reach out to the development team, or you may contact the original author of the codebase via email (<a href="mailto:adrnmlgrto.dev@gmail.com" target="_blank">adrnmlgrto.dev@gmail.com</a>)
- **Integration Issues:** Consult with technical support or helpdesk
- **Deployment Problems:** Contact on-site technical support or helpdesk
- **Architecture Questions:** Review adapter patterns or consult senior developers
- **Kiosk Issues:** Check with KwikPOS Pro development team
