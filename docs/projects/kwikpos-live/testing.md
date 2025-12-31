# Testing

## Local Testing

### Run All Tests
```bash
mvn test
```

### Run Specific Test Class
```bash
mvn test -Dtest=YourTestClass
```

### Run Integration Tests
```bash
mvn verify
```

## Manual Testing

- Use Postman collections for API testing
- Test multi-tenant scenarios
- Verify data consistency

## Testing Checklist

When testing new features or changes:

- [ ] Unit tests pass locally
- [ ] Integration tests pass
- [ ] Manual API testing with Postman
- [ ] Multi-tenant scenarios verified
- [ ] Database changes tested
- [ ] Error handling tested
- [ ] Edge cases considered
