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

- Use Postman to simulate kiosk orders
- Test different order types and configurations
- Verify error handling
- Check transformation accuracy

## Integration Testing

- Test with actual kiosk if available
- Verify POS system receives correct data
- Test concurrent order handling
- Check system performance under load

## Testing Checklist

When testing new features or changes:

- ✅ Unit tests pass locally
- ✅ Integration tests pass
- ✅ Postman collection tests successful
- ✅ Order transformation verified
- ✅ POS communication tested (if available)
- ✅ Error handling scenarios covered
- ✅ Concurrent request handling verified
- ✅ Performance under load tested
