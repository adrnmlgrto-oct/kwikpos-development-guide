# Troubleshooting

## Common Issues

### Build Failures

**Symptoms:** Maven build fails or produces errors

**Solutions:**
- Verify JDK 8 is active: `java -version`
- Clean Maven cache: `mvn clean`
- Update dependencies: `mvn dependency:resolve`

### Database Connection Issues

**Symptoms:** Cannot connect to MySQL database

**Solutions:**
- Check MySQL service is running
- Verify credentials in `application.properties`
- Ensure database exists
- Test connection using MySQL Workbench

### Tomcat Deployment Issues

**Symptoms:** Application fails to deploy or start on Tomcat

**Solutions:**
- Check Tomcat logs in logs/catalina.out
- Verify WAR file is not corrupted
- Ensure port 8080 (*or the configured port*) is available
- Confirm Tomcat version is 9.0

## Getting Additional Help

If issues persist:

- **Technical Questions:** Reach out to the development team
- **Database Issues:** Contact Sophie
- **Deployment Problems:** Contact Sophie
- **Architecture Questions:** Review existing codebase patterns or consult senior developers
