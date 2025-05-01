# Dynamic Fraud Detection Demo with Apache Flink

## Introduction
This project demonstrates a dynamic fraud detection engine built on Apache Flink, designed to handle real-time rule updates and complex event processing without requiring job restarts.

## Instructions (local execution with netcat):

1. Start netcat:
```
nc -lk 9999
```
2. Run main method of com.ververica.field.dynamicrules.Main
3. Submit to netcat in correct format:
rule_id, (rule_state), (aggregation keys), (aggregateFieldName field), (aggregation function), (limit operator), (limit), (window size in minutes)

##### Examples:

1,(active),(paymentType),(paymentAmount),(SUM),(>),(50),(20)
1,(delete),(paymentType),(paymentAmount),(SUM),(>),(50),(20)
2,(active),(payeeId),(paymentAmount),(SUM),(>),(10),(20)
2,(pause),(payeeId),(paymentAmount),(SUM),(>),(10),(20)

##### Examples JSON:  
{ "ruleId": 1, "ruleState": "ACTIVE", "groupingKeyNames": ["paymentType"], "aggregateFieldName": "paymentAmount", "aggregatorFunctionType": "SUM","limitOperatorType": "GREATER","limit": 500, "windowMinutes": 20}

##### Examples of Control Commands:

{"ruleState": "CONTROL", "controlType":"DELETE_RULES_ALL"}
{"ruleState": "CONTROL", "controlType":"EXPORT_RULES_CURRENT"}
{"ruleState": "CONTROL", "controlType":"CLEAR_STATE_ALL"}


##### Examles of CLI params:
--data-source kafka --rules-source kafka --alerts-sink kafka --rules-export-sink kafka

##### Special functions:
1,(active),(paymentType),(COUNT_FLINK),(SUM),(>),(50),(20)

## Maintainer
This project is maintained by Nithish Marneni, a Software Developer with over 3 years of professional experience specializing in Java, SQL, and backend systems. This repository serves as a demonstration of advanced stream processing patterns and dynamic rule evaluation.

- GitHub: https://github.com/nithishmarneni
- LinkedIn: https://www.linkedin.com/in/nithish-marneni/
- Email: mnithishj1@gmail.com