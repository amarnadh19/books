# AWS STEP FUNCTIONS

Step functions is a serviceless orchestration service that let you combine AWS Lambda Function and other AWS services to build business-critical applications.

Through Step Functions' graphical console, you see your application’s workflow as a series of event-driven steps.

Step Functions is based on state machines and tasks.

A state machine is a workflow.

A task is a state in a workflow that represents a single unit of work that another AWS service performs. A task can be a lambda function or an AWS service.

Each step in a workflow is a state.

## Standard and Express workflows

Step Functions has two workflow types.


### Standard workflows

- 2,000 per second execution rate.
- exactly-once workflow execution and can run for up to one year
- 4,000 per second state transition rate
- Priced per state transition
- Shows execution history and visual debugging
- Supports all service integrations and patterns
- Standard workflows are ideal for long-running, auditable workflows, as they show execution history and visual debugging.

### Express WorkFlow

- Express workflows have at-least-once workflow execution and can run for up to five minutes.
- Express workflows are ideal for high-event-rate workloads, such as streaming data processing and IoT data ingestion.
- 100,000 per second execution rate
- Nearly unlimited state transition rate
- Priced per number and duration of executions
- Sends execution history to Amazon CloudWatch
- Supports all service integrations and most patterns.

Workflow of step function is ``` start --> state ---> end ```

Language used in state machine is Amazon State Language (ASL) - Written in Json.

Types of states:

- succeed and fail
- wait
- choice
- parallel
- map
- task
