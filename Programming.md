# Programming for AI Platform Engineers

## Complete Theory + Deep Concepts + Real-World Use Cases + Practice Labs + Solutions

---

# Why Programming Matters for AI Platform Engineers

An AI Platform Engineer builds and operates:

- AI Platforms
- MLOps Platforms
- LLM Platforms
- Internal Developer Platforms
- Agentic AI Systems
- Kubernetes Operators
- Infrastructure Automation
- AI APIs
- Model Serving Systems

Programming is used for:

- Infrastructure Automation
- Platform Development
- API Development
- Monitoring Automation
- Kubernetes Automation
- AI Workflow Automation
- Cost Optimization
- Security Automation

---

# Learning Path

```text
Python Fundamentals
        ↓
Advanced Python
        ↓
Bash Scripting
        ↓
REST APIs
        ↓
GraphQL APIs
        ↓
Async Programming
        ↓
Design Patterns
        ↓
Platform Engineering Projects
```

---

# Module 1: Advanced Python

## What is Python?

Python is the primary language used in:

- AI Engineering
- MLOps
- LLMOps
- Platform Engineering
- Cloud Automation
- DevOps

---

## Advanced Python Topics

### Data Structures

#### List

```python
users = ["alice", "bob", "john"]
```

#### Tuple

```python
server = ("10.0.0.10", 8080)
```

#### Set

```python
unique_ips = {"10.0.0.1", "10.0.0.2"}
```

#### Dictionary

```python
server = {
    "name": "api-server",
    "port": 8080
}
```

---

### List Comprehensions

Traditional:

```python
numbers = []

for i in range(10):
    numbers.append(i)
```

Pythonic:

```python
numbers = [i for i in range(10)]
```

---

### Lambda Functions

```python
square = lambda x: x*x

print(square(5))
```

Output:

```text
25
```

---

### Generators

#### Why?

Used when processing huge datasets.

Bad:

```python
numbers = [i for i in range(10000000)]
```

Good:

```python
def generate():
    for i in range(10000000):
        yield i
```

---

### Decorators

#### Why?

Used for:

- Logging
- Monitoring
- Authentication
- API Tracking

Example:

```python
def logger(func):

    def wrapper():

        print("Started")

        func()

        print("Completed")

    return wrapper

@logger
def deploy():
    print("Deploying")
```

Output:

```text
Started
Deploying
Completed
```

---

### Object-Oriented Programming (OOP)

#### Class

```python
class Server:

    def __init__(self,name):
        self.name=name

server=Server("api")
```

#### Inheritance

```python
class Platform:
    pass

class AIPlatform(Platform):
    pass
```

---

## Practice Task 1

Create a class called GPUNode.

Requirements:

- hostname
- gpu_count
- status

Methods:

- start()
- stop()

### Solution

```python
class GPUNode:

    def __init__(self,hostname,gpu_count):
        self.hostname=hostname
        self.gpu_count=gpu_count

    def start(self):
        print("Node Started")

    def stop(self):
        print("Node Stopped")
```

---

# Module 2: Bash Scripting

## Why Bash?

Used for:

- Linux Automation
- Kubernetes Automation
- CI/CD
- Monitoring
- Backup Scripts

---

## Variables

```bash
NAME="Bittu"

echo $NAME
```

---

## Conditions

```bash
if [ -f test.txt ]
then
echo "Exists"
fi
```

---

## Loops

```bash
for i in {1..5}
do
echo $i
done
```

---

## Functions

```bash
hello() {
 echo "Welcome"
}
```

---

## Practice Task 2

Create 10 directories.

### Solution

```bash
for i in {1..10}
do
mkdir app$i
done
```

---

## Practice Task 3

Find all log files older than 30 days.

### Solution

```bash
find /var/log -name "*.log" -mtime +30
```

---

## Real-World Use Case

Delete logs older than 90 days.

```bash
find /logs -name "*.log" -mtime +90 -delete
```

---

# Module 3: REST APIs

## What is API?

Application Programming Interface.

Allows systems to communicate.

```text
Frontend
   ↓
REST API
   ↓
Database
```

---

## HTTP Methods

| Method | Purpose |
|----------|----------|
| GET | Read |
| POST | Create |
| PUT | Update |
| DELETE | Delete |

---

## GET Request

```python
import requests

response=requests.get(
    "https://api.github.com/users/octocat"
)

print(response.json())
```

---

## POST Request

```python
requests.post(
    url,
    json=data
)
```

---

## API Status Codes

| Code | Meaning |
|--------|----------|
| 200 | Success |
| 201 | Created |
| 400 | Bad Request |
| 401 | Unauthorized |
| 404 | Not Found |
| 500 | Server Error |

---

## Practice Task 4

Call GitHub API and print user details.

### Solution

```python
import requests

response=requests.get(
"https://api.github.com/users/octocat"
)

print(response.json())
```

---

## Real AI Platform Example

```text
Client
 ↓
API Gateway
 ↓
Model Endpoint
 ↓
Prediction
```

---

# Module 4: GraphQL

## Why GraphQL?

REST:

```text
GET /users/1
GET /repos
GET /projects
```

Multiple requests required.

GraphQL:

```text
Single Request
```

---

## GraphQL Query

```graphql
{
 user(login:"octocat") {

   name

   repositories(first:5){

      nodes{
         name
      }

   }

 }
}
```

---

## Benefits

- Single Request
- Flexible Queries
- Better Performance
- Reduced Overfetching

---

## Practice Task 5

Query GitHub GraphQL API.

Research:

- Authentication Token
- GraphQL Endpoint

---

# Module 5: Async Programming

## Why Async?

AI Platforms handle:

- Thousands of Requests
- Model Endpoints
- API Calls
- Monitoring Events

Synchronous:

```text
Request1
Wait
Request2
Wait
Request3
```

Async:

```text
Request1
Request2
Request3

Execute Together
```

---

## Async Example

```python
import asyncio

async def task():

    await asyncio.sleep(2)

    print("Done")

asyncio.run(task())
```

---

## Multiple Tasks

```python
import asyncio

async def deploy(name):

    await asyncio.sleep(2)

    print(name)

async def main():

    await asyncio.gather(
        deploy("app1"),
        deploy("app2"),
        deploy("app3")
    )

asyncio.run(main())
```

---

## Practice Task 6

Deploy 5 applications concurrently.

### Solution

```python
asyncio.gather(
 deploy("a"),
 deploy("b"),
 deploy("c"),
 deploy("d"),
 deploy("e")
)
```

---

## Real AI Use Case

Call:

- OpenAI
- Anthropic
- Gemini
- Vector Database

Concurrently for lower latency.

---

# Module 6: Design Patterns

## Why Design Patterns?

Large AI Platforms require:

- Scalability
- Reusability
- Maintainability

---

## Singleton Pattern

Used for:

- Database Connections
- Configuration Managers

```python
class Config:

    _instance=None

    def __new__(cls):

        if not cls._instance:
            cls._instance=super().__new__(cls)

        return cls._instance
```

---

## Factory Pattern

Used for:

- Model Creation
- Cloud Provider Creation

```python
class AWS:
    pass

class Azure:
    pass

def create_cloud(provider):

    if provider=="aws":
        return AWS()

    elif provider=="azure":
        return Azure()
```

---

## Observer Pattern

Used for:

- Monitoring
- Alerting
- Event Systems

```text
CPU High
 ↓
Prometheus
 ↓
Alertmanager
 ↓
Slack
```

---

## Strategy Pattern

Used for:

- AI Routing
- Load Balancing
- Model Selection

```text
GPT-4
Claude
Gemini
   ↓
Strategy Chooses
Best Model
```

---

## Practice Task 7

Create a Factory Pattern for:

- OpenAI
- Claude
- Gemini

### Solution

```python
class OpenAI:
    pass

class Claude:
    pass

class Gemini:
    pass

def create_model(model):

    if model=="openai":
        return OpenAI()

    elif model=="claude":
        return Claude()

    elif model=="gemini":
        return Gemini()
```

---

# Capstone Project

## AI Platform Automation Framework

### Features

- REST API Client
- Async API Requests
- Configuration Manager
- Logging Framework
- Monitoring Integration
- Cloud Automation

### Architecture

```text
CLI
 ↓
Python Services
 ↓
Config Manager
 ↓
REST Clients
 ↓
Cloud Providers
 ↓
Monitoring
```

---

# Daily Practice Tasks

## Beginner

1. Create Python Classes
2. Write Bash Scripts
3. Call REST APIs
4. Parse JSON

## Intermediate

1. Async API Calls
2. GraphQL Queries
3. Logging Framework
4. Config Management

## Advanced

1. Build API Gateway Client
2. Build Kubernetes Automation Tool
3. Build Platform CLI
4. Build AI Model Router

---

# Interview Questions

### Difference Between Threading and Asyncio?

Threading uses multiple threads.

Asyncio uses a single event loop.

---

### Why Async Programming?

Handle thousands of I/O operations efficiently.

---

### REST vs GraphQL?

REST uses multiple endpoints.

GraphQL uses a single endpoint with flexible queries.

---

### Why Use Generators?

Memory efficiency when processing large datasets.

---

### Why Singleton Pattern?

Ensure only one instance exists.

---

### Why Factory Pattern?

Create objects dynamically without exposing creation logic.

---

# Most Important Skills for AI Platform Engineers

- Python
- Bash
- REST APIs
- GraphQL
- Async Programming
- Design Patterns
- Linux
- Kubernetes
- Cloud
- Infrastructure Automation
- MLOps
- LLMOps
- Observability
- Distributed Systems