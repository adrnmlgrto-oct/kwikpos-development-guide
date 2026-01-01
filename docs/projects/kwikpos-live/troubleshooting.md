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

### Login Issues (Production)

**Symptoms:** Users suddenly unable to login despite application working hours earlier

**Possible Causes & Solutions:**

#### 1. Expired SSL Certificate

**Symptoms:**

- Login was working previously but suddenly stopped
- Browser shows SSL/certificate errors
- HTTPS connections failing

**Solutions:**

- Check SSL certificate expiration date
- Verify certificate is valid and not expired
- **Action Required:** Report expired SSL certificate immediately to the infrastructure team
- Renew SSL certificate through AWS Certificate Manager or certificate provider
- Update certificate on the load balancer/server

**How to Check:**

- For the safest way without using any command line terminals, you may simply go into the website itself for KwikPOS Live and inspect the SSL certificate there.

#### 2. EC2 Storage Full (*Most Common*)

**Symptoms:**

- Application becomes unresponsive
- Login attempts fail or timeout
- Logs show disk space errors
- Services fail to start or write data

**Solutions:**

- Connect to EC2 instance via RDP
- Check disk space usage on C: drive (or applicable drive)
- Clear temporary files and logs if storage is full
- Identify large files consuming space, most of the time it's related to **log files** or any past **dump files**
- Archive or delete old log files (retain only logs from the last 5 days)
- Consider increasing EBS volume size if consistently running out of space

**How to Check Storage via RDP:**

1. Connect to EC2 instance using Remote Desktop Protocol (RDP)
2. Open File Explorer
3. Right-click on C: drive → Properties
4. Check available space
5. If space is critically low (< 10% free):
    - Navigate to application logs directory
    - Archive or delete old log files
    - Clear Windows temp folder: `C:\Windows\Temp`
    - Check Tomcat logs: `<TOMCAT_HOME>\logs`

**Preventive Measures:**

- Set up CloudWatch alarms for disk space monitoring
- Implement log rotation policies
- Regularly clean up temporary files
- Monitor storage usage trends

**Action Required:**

- Report storage issues to infrastructure/DevOps team
- Document which logs or files were consuming space
- Consider implementing automated log cleanup or rotation

## Getting Additional Help

If issues persist:

- **Technical Questions:** Reach out to the development team
- **Database Issues:** Contact Sophie
- **Deployment Problems:** Contact Sophie
- **Architecture Questions:** Review existing codebase patterns or consult senior developers
