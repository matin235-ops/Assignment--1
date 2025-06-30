# JMeter Performance Testing Configuration

## Prerequisites
- Apache JMeter installed
- JMeter Plugin for Jenkins
- Performance test scenarios defined

## Test Plan Structure
```
Test Plan
├── Thread Group (Users)
├── HTTP Request Defaults
├── HTTP Requests
├── Listeners
└── Assertions
```

## Sample Test Plan for Flask Application

### Thread Group Configuration
- Number of Threads (users): 10
- Ramp-Up Period: 10 seconds
- Loop Count: 5

### HTTP Request Configuration
- Server Name: localhost
- Port: 5000
- Path: /
- Method: GET

## JMeter Test Script
```xml
<?xml version="1.0" encoding="UTF-8"?>
<jmeterTestPlan version="1.2">
  <hashTree>
    <TestPlan guiclass="TestPlanGui" testclass="TestPlan" testname="Flask App Performance Test">
      <stringProp name="TestPlan.comments"></stringProp>
      <boolProp name="TestPlan.functional_mode">false</boolProp>
      <boolProp name="TestPlan.serialize_threadgroups">false</boolProp>
      <elementProp name="TestPlan.arguments" elementType="Arguments" guiclass="ArgumentsPanel" testclass="Arguments" testname="User Defined Variables">
        <collectionProp name="Arguments.arguments"/>
      </elementProp>
      <stringProp name="TestPlan.user_define_classpath"></stringProp>
    </TestPlan>
  </hashTree>
</jmeterTestPlan>
```

## Integration with Jenkins
1. Install Performance Plugin in Jenkins
2. Add JMeter test execution in Jenkinsfile
3. Generate performance reports
4. Archive test results
