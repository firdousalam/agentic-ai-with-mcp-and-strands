# Strands Agents: A Multi-Agent Framework for Building Intelligent Applications

Strands Agents is a powerful Python framework that enables developers to build sophisticated multi-agent systems with specialized capabilities including knowledge management, calculator functions, meta-tooling, and workflow orchestration. The framework provides seamless integration with external services and robust agent communication.

The framework offers a modular architecture where specialized agents can work together to handle complex tasks. Key features include:
- Multi-agent orchestration with specialized agents for different domains (math, language, computer science, etc.)
- Dynamic tool creation and management through meta-tooling capabilities
- Knowledge base integration for persistent information storage and retrieval
- Integration with external services like weather APIs and Amazon
- Built-in calculator functionality through MCP (Modular Communication Platform)
- Streamlit-based UI components for interactive applications

## Repository Structure
```
strands_agents/
├── mcp_examples/                    # Basic MCP server/client examples
│   ├── hello_world_mcp_client.py   # Example MCP client implementation
│   └── hello_world_mcp_server.py   # Example MCP server implementation
├── strands_calculator_mcp_agent/    # Calculator agent using MCP
├── strands_knowledgebase_agent/    # Knowledge storage and retrieval agent
├── strands_memory_agent/           # Memory management agent
├── strands_meta_tooling_agent/     # Dynamic tool creation agent
├── strands_multi_agent/            # Multi-agent orchestration examples
│   ├── teachers_assistant.py       # Main orchestrator agent
│   └── specialized agents/         # Domain-specific agents (math, language, etc.)
├── strands_nova/                   # Nova integration examples
├── strands_weather_agent/          # Weather service integration
├── strands_workflow_agent/         # Workflow orchestration agent
└── streamlit_examples/             # Streamlit UI integration examples
```

## Usage Instructions
### Prerequisites
- Python 3.10+
- uv or pip package manager
- Virtual environment (recommended)

Required Python packages:
```
boto3
mcp[cli]
nova-act
opensearch-py
pandas
retrying
strands-agents 
strands-agents-tools[mem0_memory]
streamlit
tqdm
uv
```

### Installation
```bash
# Create and activate virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Quick Start
1. Basic Agent Usage:
```python
from strands import Agent
from strands_tools import memory

# Create a simple agent
agent = Agent(tools=[memory])

# Use the agent
response = agent("Remember that my favorite color is blue")
```

2. Running the Calculator Example:
```bash
python strands_calculator_mcp_agent_example/mcp_calculator.py
```

3. Starting the Multi-Agent Teacher Assistant:
```bash
python strands_multi_agent_example/teachers_assistant.py
```

### More Detailed Examples
1. Knowledge Base Operations:
```python
from strands import Agent
from strands_tools import memory

agent = Agent(tools=[memory])

# Store information
agent.tool.memory(action="store", content="The capital of France is Paris")

# Retrieve information
result = agent.tool.memory(
    action="retrieve",
    query="What is the capital of France?",
    min_score=0.4
)
```

2. Weather Information:
```python
from strands_weather_agent_example.weather_forecaster import weather_agent

# Get weather forecast
response = weather_agent("What's the weather like in Seattle?")
```

### Troubleshooting
Common Issues:
1. MCP Connection Errors
   - Error: "Connection refused"
   - Solution: Ensure MCP server is running on the correct port
   - Debug: `netstat -an | grep 8000`

2. Memory Tool Issues
   - Error: "Knowledge base not found"
   - Solution: Set STRANDS_KNOWLEDGE_BASE_ID environment variable
   - Debug: `export STRANDS_KNOWLEDGE_BASE_ID=your_kb_id`

3. Agent Initialization Failures
   - Error: "No tools available"
   - Solution: Verify tool imports and initialization
   - Debug: Enable verbose logging with `STRANDS_DEBUG=1`

## Data Flow
The Strands Agents framework processes data through a coordinated multi-agent system with specialized components handling different aspects of the workflow.

```ascii
User Input → Orchestrator Agent → Specialized Agents → External Services
     ↑                                    ↓
     └────────────── Response ───────────┘
```

Key Component Interactions:
1. User queries are received by the orchestrator agent (e.g., TeachAssist)
2. Orchestrator analyzes the query and routes to appropriate specialized agents
3. Specialized agents process domain-specific tasks using their tools
4. External services (MCP, APIs) are accessed as needed
5. Results are aggregated and formatted by the orchestrator
6. Responses are returned to the user in a consistent format
7. Knowledge and context are maintained across interactions



Agentic AI with MCP and Strands SDK
This workshop has been designed to delivered at an AWS-led event using AWS-provided workshop accounts. It is not intended to be run in your own account, and may incur cost if it is.

Workshop Modules
You will complete the following 7 modules:

Module 1: Building with Model Context Protocol (MCP)
Start building with MCP, which allows models to interact with tools and environments. You'll learn how to create and use MCP servers to extend agent capabilities by implementing a calculator agent that can perform mathematical operations through the Model Context Protocol.

Module 2: Building Weather Agent with Strands
Create a weather forecasting agent that connects to the National Weather Service API. You'll learn how to use the HTTP request tool to retrieve and process real-time weather data, demonstrating how agents can interact with external APIs.

Module 3: Building Knowledge-Base Agent with Strands [Required for Modules 5 & 7]
Create an agent that can intelligently store and retrieve information from a knowledge base. You'll implement a code-defined decision-making workflow that routes user inputs to the appropriate knowledge base operations.

Module 4: Building Workflow Agent with Strands
Build a multi-agent research workflow where specialized agents collaborate to perform web research, fact-checking, and report generation. You'll learn how to orchestrate agent-to-agent communication in a sequential workflow to process complex information.

Module 5: Building Memory Agent with Strands
Develop an agent with persistent memory capabilities. You'll implement a system that can store, retrieve, and utilize memories to create more intelligent and contextual AI interactions, enabling personalized responses based on user history.

Module 6: Building Meta Tooling Agent with Strands
Explore advanced meta-tooling capabilities that allow agents to create new tools at runtime. You'll learn how agents can dynamically extend their own capabilities by generating and loading custom tools based on natural language descriptions.

Module 7: Building Multi-Agent with Strands
Implement a sophisticated multi-agent architecture where specialized agents work together under the coordination of a central orchestrator. You'll learn how to use natural language routing to direct queries to the most appropriate specialized agent based on subject matter expertise.

Module 8: Amazon Bedrock AgentCore
Learn about Amazon Bedrock AgentCore capabilities including runtime, identity, memory management, code interpretation, browsing, gateway services and observability.

Target Audience
This is a 300-level workshop targeted at software developers. Familiarity with using the terminal and Python coding will be important.

Prerequisites
Basic understanding of AWS services
Experience with Python programming and terminal usage
Attendees need to bring a WiFi-capable laptop with a modern browser (e.g. Chrome, Firefox)
An AWS Builder ID  is not required, unless you are using Q Developer as part of the workshop.
Cost
This workshop is intended to be run as part of an AWS event, using AWS-provided accounts, where the costs will be covered by AWS.

Time
This workshop can be completed within an estimated 4 hours (2 hours for the Strands SDK section - Modules 1-7 and 2 hours for the AgentCore section - Modules 8.1 to 8.8)

Learning Points
Upon completion of this workshop, participants will have:

For Modules 1-7

learned about the Model Context Protocol (MCP) and the Strands SDK
built basic tools using the Strands SDK and learned how to invoke those tools
created a Bedrock Knowledge Base and used it with the Strands SDK
orchestrated multi-agent workflows with the Strands SDK
build, run, and deploy a multi-agent capable Streamlit app
For Modules 8.1 to 8.8

learned about Amazon Bedrock AgentCore
familiarized with following Amazon Bedrock AgentCore services
Amazon Bedrock AgentCore Runtime
Amazon Bedrock AgentCore Identity
Amazon Bedrock AgentCore Memory
Amazon Bedrock AgentCore Code Interpreter
Amazon Bedrock AgentCore Browser
Amazon Bedrock AgentCore Gateway
Amazon Bedrock AgentCore Observability


Workshop Setup [REQUIRED]
Introduction
In this workshop we will building agentic workflows in Python. We will additionally use Amazon Q to help us to write code. Amazon Q is a Generative AI assistant that lives where you work, whether that be in the IDE or the console. Amazon Q can help with writing code, debugging issues and providing resources.

If operating at at AWS Event you will be using VSCode Code-Server, otherwise you may run on your own device.

VSCode (Code-Server) is through a web-based version called VSCode Code-Server. This method doesn't require any prerequisites other than a browser, and no configuration is necessary.

Running the workshop at an AWS Event
As a reminder, Amazon Q integrates with multiple IDEs—including JetBrains, Visual Studio Code, and others. In this workshop we will be using Visual Studio Code. In order to get to the hands-on-keyboard portion of the workshop as quickly as possible, we will be using Visual Studio via code-server , hosted on an Amazon EC2 Instance.

Accessing code-server
First we will access the code server we will use for the duration of the workshop. Please navigate to the Workshop Studio Event Outputs .
Once there, scroll down until you see the Event Outputs at the bottom of the page.
Copy the Password. You will need this in the next step.
Click on the URL to open VS Code Server.
If you get the an error that starts with the following text, "502 ERROR The request could not be satisfied. CloudFront attempted to establish ...", this could be because code-server is still deploying. Try waiting for a minute or so, and then refresh your browser:

Lab1 Architecture Diagram

Now, you will be prompted to enter a password. Paste the password that you copied earlier.
Lab1 Architecture Diagram

Click Submit. You should now see the VSCode IDE as shown below. The VS Code terminal window is shown at the bottom.
Lab1 Architecture Diagram

Clipboard Settings
It is assumed that your browser is not blocking access to your clipboard. This is important when copying and pasting text from this lab into code-server. In order to enable your browser to access your clipboard, you will need to configure the browser using the instructions below.

Verify Chrome Clipboard Settings
If you encounter clipboard permission issues on Chrome, you may wish to go to chrome://settings/content/clipboard. Next, choose the setting Sites can ask to see text and images on your clipboard, as shown in the screenshot below. You can also enable clipboard access only for the specific Cloudfront website where this lab's code-server is hosted.

Chrome Clipboard Settings

Verify Firefox Clipboard Settings
If you encounter clipboard permission issues on Firefox, you may wish to go to about:config. Search for dom.events.asyncClipboard.readText and dom.events.testing.asyncClipboard and set both of these to true. After this lab is completed, you can switch these back to their original settings.

Amazon Bedrock Setup
For this workshop we will use Amazon Bedrock which is a fully managed service that offers a choice of high-performing foundation models (FMs) from leading AI companies like Stability AI, Anthropic, and Meta, via a single API, along with a broad set of capabilities you need to build generative AI applications with security, privacy, and responsible AI.

Since Amazon Bedrock is serverless, you don't have to manage any infrastructure, and you can securely integrate and deploy generative AI capabilities into your applications using the AWS services you are already familiar with.

Before we can build our agents, we need to enable access to the models in our account.

AWS Account
If you are running this Workshop at an AWS event, make sure you are logged into the Workshop AWS Account. By Clicking the Open AWS Console button on the side menu.


Once logged in you should see your User as WSParticipantRole/Participant in the top right corner.

Model Access
Before we can start building with Bedrock, we will need to grant model access to our account.

Head to the Amazon Bedrock model access page 

Select the Enable specific models button.

Select the checkboxes listed below to activate the models. If running from your own account, there is no cost to activate the models - you only pay for what you use during the labs. See here for more information on supported models

Amazon (select Amazon to automatically select all Amazon models).
Anthropic: Claude 4 Sonnet, Claude 3.7 Sonnet, Claude 3.5 Sonnet v2, Claude 3.5 Haiku
Click Request model access to activate the models in your account.



Monitor the model access status. It may take a few minutes for the models to move from In Progress to Access granted status. You can use the Refresh button to periodically check for updates.

Verify that the model access status is Access granted for the previously selected models.


Strands SDK Setup
Go to the code-server instance that you launched earlier and open a terminal. Run the following commands

Install UV and Python 3.12
1
2
3
4
5
6
7
8
9
cd ~
curl -LsSf https://astral.sh/uv/install.sh | sh
if [ "$SHELL" = "/bin/bash" ]; then
  echo 'eval "$(uv generate-shell-completion bash)"' >> ~/.bashrc
  echo 'eval "$(uvx --generate-shell-completion bash)"' >> ~/.bashrc
fi
source ~/.bashrc
uv self update
uv python install 3.12

Setup Python Virtual Environment
Create the requirements.txt file:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
cat << EOF > requirements.txt
aws-opentelemetry-distro>=0.10.0
bedrock-agentcore
bedrock-agentcore-starter-toolkit
boto3
litellm
mcp[cli]
nova-act
opensearch-py
pandas
retrying
strands-agents 
strands-agents-tools[mem0_memory]
streamlit
tqdm
uv
EOF

The Python libraries bedrock-agentcore, bedrock-agentcore-starter-toolkit and aws-opentelemetry-distro>=0.10.0 are only required for the Bedrock AgentCore Module 8 in this workshop.

Install the Python libraries

1
2
3
uv venv
source ~/.venv/bin/activate
uv pip install -r requirements.txt

Setup Linux Tools (only required for Module 8)
Install the jq command line utility for JSON data manipulation as follows:

1
sudo apt install -y jq

Amazon Q Setup
In this section, we will set up Amazon Q in the VScode code-server using an AWS Builder ID, which is a new personal profile for everyone who builds on AWS.

1. MCP Server Setup for Amazon Q for Developers
Amazon Q for Developers supports MCP servers. To find out more, you may wish to refer to the documentation: Using MCP with Amazon Q Developer .

Some useful AWS MCP servers include the AWS Core MCP Server, AWS Documentation MCP Server, AWS Knowledge MCP Server, AWS CDK MCP Server (for CDK development) and the Strands Agents MCP Server. A full list of AWS MCP servers is available here here .

Create the file mcp.json as follows:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
mkdir -p ~/.aws/amazonq/
cat << EOF > ~/.aws/amazonq/mcp.json
{
  "mcpServers": {
    "awslabs.core-mcp-server": {
        "command": "uvx",
        "args": ["awslabs.core-mcp-server@latest"],
        "env": {
          "FASTMCP_LOG_LEVEL": "ERROR",
          "MCP_SETTINGS_PATH": "path to your mcp settings file"
        }
    },
    "awslabs.aws-documentation-mcp-server": {
        "command": "uvx",
        "args": ["awslabs.aws-documentation-mcp-server@latest"],
        "env": {
          "FASTMCP_LOG_LEVEL": "ERROR"
        },
        "disabled": false,
        "autoApprove": []
    },
    "aws-knowledge-mcp-server": {
        "command": "uvx",
        "args": [
            "mcp-proxy",
            "--transport",
            "streamablehttp",
            "https://knowledge-mcp.global.api.aws"
        ]
    },
    "awslabs.cdk-mcp-server": {
      "command": "uvx",
      "args": ["awslabs.cdk-mcp-server@latest"],
      "env": {
        "FASTMCP_LOG_LEVEL": "ERROR"
      }
    },
    "strands": {
      "command": "uvx",
      "args": ["strands-agents-mcp-server"]
    }
  }
}
EOF

Replace all occurrences of uvx with the full path /home/ubuntu/.venv/bin/uvx using the sed command:

1
sed -i "s/uvx/\/home\/ubuntu\/.venv\/bin\/uvx/g" ~/.aws/amazonq/mcp.json

2. Setting up Amazon Q for Developers
Installing the Amazon Q for Developers Extension

Check whether Amazon Q for Developers extension is installed.

There are two ways to install the extension.

To install it using the command line, run the following in a terminal window.

1
code-server --install-extension AmazonWebServices.amazon-q-vscode --force

Example output:

Installing extensions on d1oabc123z31a0.cloudfront.net...
Installing extension 'amazonwebservices.amazon-q-vscode'...
Extension 'amazonwebservices.amazon-q-vscode' v1.92.0 was successfully installed.
To install it using the user interface, inside VS Code, click on the extension tab, search for q and install the extension. Lab1 Architecture Diagram

Authentication

Next, we need to ensure we are authenticated with Amazon Q.

In the Amazon Q extension for Visual Studio Code, select Use for free. Choose continue.
Lab1 Architecture Diagram

At the prompt Confirm Code for AWS Builder ID choose Proceed to Browser. Note: if an additional prompt shows, please proceed by choosing Open.

At the prompt Do you want Code to open the external website?, choose Open.

A browser tab will open, displaying the Authorization requested window. The code should already populated. Choose Confirm and continue.

A browser tab will open to the Create AWS Builder ID  page. Enter your email address and choose Next.

A field for Your name will appear. Enter your name and choose Next.

AWS will send a confirmation code to your submitted email address. Enter the code on the email verification screen and choose Verify.

On the Choose your password screen, enter a password, confirm it, and choose Create AWS Builder ID.

A browser tab will open with a message asking you to allow Amazon Q extension for Visual Studio Code to access your data. Choose Allow.

Return to VS Code. If you have already authenticated into other AWS tools using IAM, you will be asked whether you want to use Builder ID for all AWS services. Choose the option that best suits your situation.

Module 1: Building with Model Context Protocol (MCP)
MCP Calculator - Model Context Protocol Integration Example
Model Context Protocol (MCP) is an open standard that enables large language models (LLMs) like Claude, Amazon Nova, and others to interact with tools and environments consistently. MCP creates a standardized interface between AI models and external tools, allowing models to:

Execute code and functions
Access external data sources
Control applications and services
Extend their capabilities without requiring custom integrations
MCP is still a developing standard, so expect changes and improvements as it evolves

Lab1 Architecture Diagram

Why MCP Matters
MCP solves several key challenges in AI agent development:

Standardization: Common interface for models to interact with any tool
Extensibility: Easily add new capabilities to any MCP-compatible model
Interoperability: Tools built for one model work with any other MCP-compatible model
Composability: Combine multiple tools to build complex workflows
Running a Basic MCP Server
In this exercise, you'll learn how to run a simple MCP server and client with basic tools. We'll use Python's FastMCP library to make this process straightforward.

This example  demonstrates how to integrate Strands agents with external tools using the Model Context Protocol (MCP). It shows how to create a simple MCP server that provides calculator functionality and connect a Strands agent to use these tools.

Overview
Feature	Description
Tool Used	MCPAgentTool
Protocol	Model Context Protocol (MCP)
Complexity	Intermediate
Agent Type	Single Agent
Interaction	Command Line Interface
Tool Overview
The Model Context Protocol (MCP) enables Strands agents to use tools provided by external servers, connecting conversational AI with specialized functionality. The SDK provides the MCPAgentTool class which adapts MCP tools to the agent framework's tool interface. The MCPAgentTool is loaded via an MCPClient, which represents a connection from Strands to an external server that provides tools for the agent to use.

Code Walkthrough
In this section, we will do a walkthrough of selected code blocks, that have been used to build mcp_calculator.py . This file is located in the folder strands_calculator_mcp_agent_example.

A simple MCP Server
The following code demonstrates how to create a simple MCP server that provides limited calculator functionality.

1
2
3
4
5
6
7
8
9
10
from mcp.server import FastMCP

mcp = FastMCP("Calculator Server")

@mcp.tool(description="Add two numbers together")
def add(x: int, y: int) -> int:
    """Add two numbers and return the result."""
    return x + y

mcp.run(transport="streamable-http")

Connecting the server to the Strands Agent
The following code shows how to create a Strands agent, and connect it to a MCP server:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
from mcp.client.streamable_http import streamablehttp_client
from strands import Agent
from strands.tools.mcp.mcp_client import MCPClient

def create_streamable_http_transport():
   return streamablehttp_client("http://localhost:8000/mcp/")

streamable_http_mcp_client = MCPClient(create_streamable_http_transport)

# Use the MCP server in a context manager
with streamable_http_mcp_client:
    # Get the tools from the MCP server
    tools = streamable_http_mcp_client.list_tools_sync()
    
    # Create an agent with the MCP tools
    agent = Agent(tools=tools)

At this point, the agent has successfully connected to the MCP server and retrieved the calculator tools. These MCP tools have been converted into standard AgentTools that the agent can use just like any other tools provided to it. The agent now has full access to the calculator functionality without needing to know the implementation details of the MCP server.

Using the Tool
Users can interact with the calculator tools through conversational queries:

1
2
3
4
# Let the agent handle the tool selection and parameter extraction
response = agent("What is 125 plus 375?")
response = agent("If I have 1000 and spend 246, how much do I have left?")
response = agent("What is 24 multiplied by 7 divided by 3?")

Direct Method Access
For developers who need programmatic control, Strands also supports direct tool invocation:

1
2
3
4
5
6
7
8
9
with streamable_http_mcp_client:
    result = streamable_http_mcp_client.call_tool_sync(
        tool_use_id="tool-123",
        name="add",
        arguments={"x": 125, "y": 375}
    )
    
    # Process the result
    print(f"Calculation result: {result['content'][0]['text']}")

Explicit Tool Call through Agent
1
2
3
4
5
6
with streamable_http_mcp_client:
   tools = streamable_http_mcp_client.list_tools_sync()

   # Create an agent with the MCP tools
   agent = Agent(tools=tools)
   agent.add(x=125, y=375)

Default Model for Strands Agents
In Strands Agents, the default model ID is us.anthropic.claude-sonnet-4-20250514-v1:0 (at the time of this writing). You can trace this through the Agent() class __init__() subroutine in agent.py  and in the BedrockModel() class __init__() subroutine in bedrock.py  which contains the definition DEFAULT_BEDROCK_MODEL_ID = "us.anthropic.claude-sonnet-4-20250514-v1:0".

Sample Queries and Responses
Let's run the code mcp_calculator.py:

1
2
cd ~/workshop/strands_calculator_mcp_agent_example
uv run mcp_calculator.py 

Try typing in the following queries. You may click the copy button next to the text indicated as inputs and paste the text into the command line. Please be careful not to accidentally enter any sensitive or PII data:

Query 1:

1
What is 16 times 16?

Example Response:

Thinking...

<thinking>The User wants to know the result of multiplying 16 by 16. I can use the 'multiply' tool to perform this calculation.</thinking>

Tool #1: multiply
INFO:     127.0.0.1:39762 - "POST /mcp/ HTTP/1.1" 307 Temporary Redirect
INFO:     127.0.0.1:39762 - "POST /mcp HTTP/1.1" 200 OK
The result of multiplying 16 by 16 is 256.
Answer: The result of multiplying 16 by 16 is 256.
Query 2:

1
If I have $1000 and spend $246, how much do I have left?

Example Response:

Thinking...

To determine how much money is left after spending $246 from $1000, we need to perform a subtraction. Here are the steps:

1. Identify the initial amount of money: $1000.
2. Identify the amount of money spent: $246.
3. Subtract the amount spent from the initial amount: $1000 - $246.

Let's perform the subtraction step by step:

- Subtract the units place: 0 - 6. Since we can't subtract 6 from 0, we need to borrow 1 from the tens place. This makes the 0 a 10 and the 0 in the tens place a 9. Now, 10 - 6 = 4.
- Subtract the tens place: 9 - 4 = 5.
- Subtract the hundreds place: 0 - 2 = -2. Since we can't subtract 2 from 0, we need to borrow 1 from the thousands place. This makes the 0 a 10 and the 1 in the thousands place a 9. Now, 10 - 2 = 8.
- Subtract the thousands place: 9 - 0 = 9.

Putting it all together, we get $754.

So, the amount of money left after spending $246 from $1000 is \boxed{754}.
Answer: To determine how much money is left after spending $246 from $1000, we need to perform a subtraction. Here are the steps:

1. Identify the initial amount of money: $1000.
2. Identify the amount of money spent: $246.
3. Subtract the amount spent from the initial amount: $1000 - $246.

Let's perform the subtraction step by step:

- Subtract the units place: 0 - 6. Since we can't subtract 6 from 0, we need to borrow 1 from the tens place. This makes the 0 a 10 and the 0 in the tens place a 9. Now, 10 - 6 = 4.
- Subtract the tens place: 9 - 4 = 5.
- Subtract the hundreds place: 0 - 2 = -2. Since we can't subtract 2 from 0, we need to borrow 1 from the thousands place. This makes the 0 a 10 and the 1 in the thousands place a 9. Now, 10 - 2 = 8.
- Subtract the thousands place: 9 - 0 = 9.

Putting it all together, we get $754.

So, the amount of money left after spending $246 from $1000 is \boxed{754}.
Query 3:

1
What is pi by 4?

Example Response:

The value of \(\pi\) (pi) is approximately 3.14159. When you divide \(\pi\) by 4, you get:

\[
\frac{\pi}{4} \approx \frac{3.14159}{4} \approx 0.7853975
\]

So, \(\pi\) divided by 4 is approximately 0.7854.
Answer: The value of \(\pi\) (pi) is approximately 3.14159. When you divide \(\pi\) by 4, you get:

\[
\frac{\pi}{4} \approx \frac{3.14159}{4} \approx 0.7853975
\]

So, \(\pi\) divided by 4 is approximately 0.7854.
Type exit at the next prompt to exit the application.

You can exit the Python app at any time by typing exit or pressing Ctrl+C.

Extending the Example
The MCP calculator example can be extended in several ways. You could implement additional calculator functions like square root or trigonometric functions. A web UI could be built that connects to the same MCP server. The system could be expanded to connect to multiple MCP servers that provide different tool sets. You might also implement a custom transport mechanism instead of Streamable HTTP or add authentication to the MCP server to control access to tools.

Conclusion
The Strands Agents SDK provides first-class support for the Model Context Protocol, making it easy to extend your agents with external tools. As demonstrated in this walkthrough, you can connect your agent to MCP servers with just a few lines of code. The SDK handles all the complexities of tool discovery, parameter extraction, and result formatting, allowing you to focus on building your application.

By leveraging the Strands Agents SDK's MCP support, you can rapidly extend your agent's capabilities with specialized tools while maintaining a clean separation between your agent logic and tool implementations.

Module 2: Building Weather Agent with Strands
Weather Forecaster - Strands Agents HTTP Integration Example
Open VSCode and locate the strands_weather_agent_example/weather_forecaster.py file in your workspace.

This example demonstrates how to integrate the Strands Agents SDK with tool use, specifically using the http_request tool to build a weather forecasting agent that connects with the National Weather Service API. It shows how to combine natural language understanding with API capabilities to retrieve and present weather information.

Overview
Feature	Description
Tool Used	http_request
API	National Weather Service API (no key required)
Complexity	Beginner
Agent Type	Single Agent
Interaction	Command Line Interface
Tool Overview
The http_request  tool enables Strands agents to connect with external web services and APIs, connecting conversational AI with data sources. This tool supports multiple HTTP methods (GET, POST, PUT, DELETE), handles URL encoding and response parsing, and returns structured data from web sources.

Code Structure and Implementation
The example demonstrates how to integrate the Strands Agents SDK with tools to create an intelligent weather agent:

Creating the Weather Agent
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
from strands import Agent
from strands_tools import http_request

# Define a weather-focused system prompt
WEATHER_SYSTEM_PROMPT = """You are a weather assistant with HTTP capabilities. You can:

1. Make HTTP requests to the National Weather Service API
2. Process and display weather forecast data
3. Provide weather information for locations in the United States

When retrieving weather information:
1. First get the coordinates or grid information using https://api.weather.gov/points/{latitude},{longitude} or https://api.weather.gov/points/{zipcode}
2. Then use the returned forecast URL to get the actual forecast

When displaying responses:
- Format weather data in a human-readable way
- Highlight important information like temperature, precipitation, and alerts
- Handle errors appropriately
- Convert technical terms to user-friendly language

Always explain the weather conditions clearly and provide context for the forecast.
"""

# Create an agent with HTTP capabilities
weather_agent = Agent(
    system_prompt=WEATHER_SYSTEM_PROMPT,
    tools=[http_request],  # Explicitly enable http_request tool
)

The system prompt is crucial as it:

Defines the agent's purpose and capabilities
Outlines the multi-step API workflow
Specifies response formatting expectations
Provides domain-specific instructions
Using the Weather Agent
The weather agent can be used in two primary ways:

1. Natural Language Instructions
Users can interact with the National Weather Service API through conversational queries:

1
2
3
4
# Let the agent handle the API details
response = weather_agent("What's the weather like in Seattle?")
response = weather_agent("Will it rain tomorrow in Miami?")
response = weather_agent("Compare the temperature in New York and Chicago this weekend")

Multi-Step API Workflow Behind the Scenes
When a user asks a weather question, the agent handles a multi-step process:

Step 1: Location Information Request
The agent:

Makes an HTTP GET request to https://api.weather.gov/points/{latitude},{longitude} or https://api.weather.gov/points/{zipcode}
Extracts key properties from the response JSON:
properties.forecast: URL for the forecast data
properties.forecastHourly: URL for hourly forecast data
properties.relativeLocation: Information about the nearest location name
properties.gridId, properties.gridX, properties.gridY: Grid identifiers
Step 2: Forecast Data Request
The agent then:

Uses the extracted forecast URL to make a second HTTP request
Processes the properties.periods array containing forecast periods with data like:
temperature and temperatureUnit
windSpeed and windDirection
shortForecast and detailedForecast descriptions
Timing information (startTime, endTime, isDaytime)
Step 3: Natural Language Processing
The agent transforms this technical data into conversational responses by:

Prioritizing relevant information based on the user's question
Converting technical terms to user-friendly language
Formatting the response in a readable structure
Adding context and recommendations when appropriate
2. Direct Tool Calls
For developers who need programmatic control, Strands also supports direct method calls to the same API:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
# Direct API method calls with Strands
location_response = weather_agent.tool.http_request(
    method="GET",
    url="https://api.weather.gov/points/47.6062,-122.3321"  # Seattle coordinates
)

# Process response as needed
import json
location_data = json.loads(location_response['body'])
forecast_url = location_data.get('properties', {}).get('forecast')

# Make a second request to get the forecast
forecast_response = weather_agent.tool.http_request(
    method="GET",
    url=forecast_url
)

Sample Queries and Responses
Let's run the code weather_forecaster.py:

1
2
cd ~/workshop/strands_weather_agent_example
uv run weather_forecaster.py

Try typing in the following queries (please be careful not to enter any sensitive or PII data):

Query 1:

1
What's the weather like in Seattle?

Response (this output will vary, depending on the actual weather forecast at the time of the query):

Tool #3: http_request


Now that I have the forecast URL, I'll get the actual weather forecast:
Tool #4: http_request


# Weather Report for Seattle, WA

## Today
- **Temperature:** 67°F
- **Conditions:** Slight chance of rain showers early, becoming mostly sunny
- **Wind:** Northwest 1 to 5 mph
- **Precipitation Chance:** 20% (before 7am)

It's shaping up to be a pleasant day in Seattle! There's just a slight chance of rain showers early this morning (20% chance before 7am), but it will become mostly sunny for the rest of the day with a comfortable high of 67°F and light northwest winds.

## Tonight
- **Low:** 47°F (rising to around 49°F overnight)
- **Conditions:** Partly cloudy
- **Wind:** Northeast around 5 mph

## Looking Ahead
- **Friday:** Mostly sunny, high near 67°F
- **Saturday:** Mostly sunny and warmer, high near 73°F
- **Sunday:** Sunny, high near 75°F with clear skies

The weekend looks great in Seattle with gradually warming temperatures and plenty of sunshine. Perfect weather for outdoor activities! There's a slight chance of rain returning Sunday night into Memorial Day, but overall the forecast is quite favorable with temperatures reaching the mid-70s.

# Weather Report for Seattle, WA

## Today
- **Temperature:** 67°F
- **Conditions:** Slight chance of rain showers early, becoming mostly sunny
- **Wind:** Northwest 1 to 5 mph
- **Precipitation Chance:** 20% (before 7am)

It's shaping up to be a pleasant day in Seattle! There's just a slight chance of rain showers early this morning (20% chance before 7am), but it will become mostly sunny for the rest of the day with a comfortable high of 67°F and light northwest winds.

## Tonight
- **Low:** 47°F (rising to around 49°F overnight)
- **Conditions:** Partly cloudy
- **Wind:** Northeast around 5 mph

## Looking Ahead
- **Friday:** Mostly sunny, high near 67°F
- **Saturday:** Mostly sunny and warmer, high near 73°F
- **Sunday:** Sunny, high near 75°F with clear skies

The weekend looks great in Seattle with gradually warming temperatures and plenty of sunshine. Perfect weather for outdoor activities! There's a slight chance of rain returning Sunday night into Memorial Day, but overall the forecast is quite favorable with temperatures reaching the mid-70s.
Query 2:

1
Will it rain tomorrow in Miami?

Response (this output will vary, depending on the actual weather forecast at the time of the query):

I'd be happy to check the weather forecast for Miami to see if rain is expected tomorrow. I'll need to make an API request to the National Weather Service to get this information for you.

First, let me get the coordinates for Miami, and then retrieve the forecast:
Tool #1: http_request


I need to use specific coordinates for Miami rather than just the city name. Let me use Miami's approximate coordinates:
Tool #2: http_request


Now I'll get the forecast for Miami using the forecast URL provided in the response:
Tool #3: http_request


Based on the National Weather Service forecast, here's the weather information for Miami tomorrow (Friday):

## Weather Forecast for Miami, FL - Tomorrow (Friday)

**Forecast Summary**: Yes, there is a good chance of rain tomorrow in Miami.

**Precipitation**: There's a **60% chance of precipitation** throughout the day, which is considered likely. The forecast indicates showers and thunderstorms are expected.

**Temperature**: High near 88°F

**Wind**: South wind around 8 mph

**Details**: The day will start mostly sunny, but there will be a chance of showers and thunderstorms throughout the day, becoming more likely as the day progresses. New rainfall amounts are expected to be between a tenth and quarter of an inch.

**Timeline**:
- Morning: Chance of showers and thunderstorms before 8am and between 8am-11am
- Afternoon: Chance of showers and thunderstorms between 11am-2pm
- Later in the day: Showers and thunderstorms likely

The rain chances continue into tomorrow night (Friday night) at 60%, with showers and thunderstorms likely before 8pm, then decreasing to a slight chance later in the night.

Would you like any additional information about the weather forecast for Miami?

Based on the National Weather Service forecast, here's the weather information for Miami tomorrow (Friday):

## Weather Forecast for Miami, FL - Tomorrow (Friday)

**Forecast Summary**: Yes, there is a good chance of rain tomorrow in Miami.

**Precipitation**: There's a **60% chance of precipitation** throughout the day, which is considered likely. The forecast indicates showers and thunderstorms are expected.

**Temperature**: High near 88°F

**Wind**: South wind around 8 mph

**Details**: The day will start mostly sunny, but there will be a chance of showers and thunderstorms throughout the day, becoming more likely as the day progresses. New rainfall amounts are expected to be between a tenth and quarter of an inch.

**Timeline**:
- Morning: Chance of showers and thunderstorms before 8am and between 8am-11am
- Afternoon: Chance of showers and thunderstorms between 11am-2pm
- Later in the day: Showers and thunderstorms likely

The rain chances continue into tomorrow night (Friday night) at 60%, with showers and thunderstorms likely before 8pm, then decreasing to a slight chance later in the night.

Would you like any additional information about the weather forecast for Miami?
Type exit to exit the application.

Extending the Example
Here are some ways you could extend this weather forecaster example:

Add location search: Implement geocoding to convert city names to coordinates
Support more weather data: Add hourly forecasts, alerts, or radar images
Improve response formatting: Create better formatted weather reports
Add caching: Implement caching to reduce API calls for frequent locations
Create a web interface: Build a web UI for the weather agent

Module 3: Building Knowledge-Base Agent with Strands
This module contains 3 parts:

Option 1 - Creating Bedrock KB (Knowledge Base) in the console
Option 2 - Quick Create Bedrock Knowledge Base with Python
Test Knowledge-Base Agent with Strands
If you would like to familiarize with the steps to create a Bedrock Knowledge Base with S3, using the AWS Console, use Option 1.

If you would like to create a Bedrock Knowledge Base with a Custom Data Store using the Python boto3 library, use Option 2

After you have completed Option 1 or Option 2, go to the section Test Knowledge-Base Agent with Strands.

Creation of the knowledge base is also pre-requisite for Module 5: Building Memory Agent with Strands and Module 7 / Steps 3 & 4. If you are short of time you can use Option 2 Quick Create Bedrock Knowledge Base with Python.

Option 1 - Creating Bedrock KB in the console
Create & populate S3 bucket
Go to the Amazon S3 console . Click Create bucket to create an S3 Bucket with a unique name.
Amazon S3 Console

Leave all the settings as default and click Create bucket.

Download and unzip the files from here . Click the Upload button to upload them to the created S3 bucket. You can drag and drop the files, and then click the Upload button.
Amazon S3 Console

Create Bedrock Knowledge Base
Go to the Amazon Bedrock console . In the left navigation pane under Builder tools, select Knowledge bases.
Bedrock Knowledge Base Console

In the Knowledge bases section, select Create and then Knowledge Base with vector store.
Bedrock Knowledge Base Console

On the Provide knowledge base details page, set up the following configurations:

a. In the Knowledge base details section, provide a name or description for your knowledge base or use default.

b. In the IAM permissions section, choose Create and use a new service role. THe Service role name will have IAM role that starts with AmazonBedrockExecutionRoleForKnowledgeBase_

c. Choose Custom as the data source.

d. Select Next.

Bedrock Knowledge Base Console

On the Configure data source page, leave everything as default:

a. Here we use the Amazon Bedrock default parser for parsing and use Default chunking for our Chunking strategy. Refer to this documentation  to learn more about other strategies.

Default chunking – By default, Amazon Bedrock automatically splits your source data into chunks, such that each chunk contains, at most, 300 tokens. If a document contains less than 300 tokens, then it is not split any further.

b. Under Advanced settings, we leave the settings as Use default KMS key.

c. Select Next.

Bedrock Knowledge Base Console

In the Configure data storage and processing section:

a. For the Embeddings model, choose Titan Text Embeddings v2. This is the embeddings model that will convert the knowledge base from your data into a vector embedding.

b. In the Vector store section, choose Quick create a new vector store. The Vector store type should be left at the default setting: Amazon OpenSearch Serverless. Amazon Bedrock creates an Amazon OpenSearch Serverless vector search collection, automatically configures the settings for embedding your data sources, and manages the collection for you.

c. Select Next.

Bedrock Knowledge Base Console

On the Review and create page, check the configuration and details of your knowledge base. Select Edit in any section that you need to modify. When you are satisfied, select Create knowledge base.

This step will take at least 5 minutes to provision the required infrastructure. Time for some ☕︎?

You will see the following when the creation is complete. Click on the data source in the Data Source section of the dashboard.

Bedrock Knowledge Base Console

In the following screen, click Add documents and select Add documents directly

Bedrock Knowledge Base Console

Add all the pdfs that were downloaded earlier.

Bedrock Knowledge Base Console Bedrock Knowledge Base Console

When the indexing is complete, you should see the following

Bedrock Knowledge Base Console

The time required depends on the amount of data you provided. When the knowledge base is finished being created, a green success banner appears and the Status of the knowledge base changes to Ready.

Submit retrieval queries to the Bedrock Knowledge Base
After you set up your knowledge base, you can test its behavior by sending queries and seeing the responses. When you are satisfied with your knowledge base's behavior, you can set up your application to query the knowledge base or attach the knowledge base to an agent.

AWS

Option 2 - Quick Create Bedrock KB with Python
Creating a Bedrock Knowledge Base using Python
You can use this section to set up a Bedrock Knowledge Base, as an alternative to Steps 1-3, earlier in this section. Some of the code here has been adapted from this Github repository: https://github.com/aws-samples/amazon-bedrock-samples/tree/main/agents-and-function-calling/bedrock-agents/features-examples/05-create-agent-with-knowledge-base-and-action-group 

Setup the Knowlege Base by running the following in the VS Code Terminal Window:

1
2
3
export AWS_DEFAULT_REGION="$AWS_REGION"
cd ~/workshop/
uv run create_knowledge_base.py

This operation takes approximately ~7-9 minutes to complete.

The Python code create_knowledge_base.py performs the following actions:

Downloads pets-kb-files.zip from https://d2qrbbbqnxtln.cloudfront.net/pets-kb-files.zip 
Unzips pets-kb-files.zip to the current folder
Creates an S3 bucket s3://bedrock-kb-bucket-{random_suffix} (where random_suffix is a series of 8 random characters)
Creates a Bedrock Knowledge Base, with a custom data source
Synchronizes the S3 bucket with the Bedrock Knowledge Base
Side note
You can also download and unzip pets-kb-files.zip via the command line, then create an S3 bucket and sync via AWS CLI:

1
2
3
4
5
6
7
curl -LO https://d2qrbbbqnxtln.cloudfront.net/pets-kb-files.zip
unzip pets-kb-files.zip

random_suffix=$(uuidgen | cut -c1-8 | tr '[:upper:]' '[:lower:]')
s3_bucket="bedrock-kb-bucket-${random_suffix}"
aws s3 mb "s3://${s3_bucket}"
aws s3 sync pets-kb-files/ "s3://${s3_bucket}"

Test Knowledge Base Agent with Strands
Knowledge Base Agent - Intelligent Information Storage and Retrieval
Open VSCode and locate the strands_knowledgebase_agent_example/knowledge_base_agent.py file in your workspace.

This example demonstrates how to create a Strands agent that determines whether to store information to a knowledge base or retrieve information from it based on the user's query. It showcases a code-defined decision-making workflow that routes user inputs to the appropriate action.

Setup Requirements
Save the Bedrock Knowledge Base ID, and the OpenSearch hostname

Store the Bedrock Knowledge Base ID in the environment variable $STRANDS_KNOWLEDGE_BASE_ID. Store the Open Search hostname (it should look something like this: ream22p9qxnb0zkc613c.us-west-2.aoss.amazonaws.com) in the environment variable $OPENSEARCH_HOST, for later use.

1
2
3
4
5
6
7
export STRANDS_KNOWLEDGE_BASE_ID=$(aws bedrock-agent list-knowledge-bases --region $AWS_REGION --query 'knowledgeBaseSummaries[].knowledgeBaseId' --output text)
export OPENSEARCH_COLLECTION_ID=$(aws opensearchserverless list-collections --query "collectionSummaries[].id" --output text)
export OPENSEARCH_ENDPOINT=$(aws opensearchserverless batch-get-collection --ids $OPENSEARCH_COLLECTION_ID --query 'collectionDetails[].collectionEndpoint' --output text)
export OPENSEARCH_HOST="${OPENSEARCH_ENDPOINT#https://*}"
echo "export STRANDS_KNOWLEDGE_BASE_ID=\"${STRANDS_KNOWLEDGE_BASE_ID}\"" >> ~/.bashrc
echo "export OPENSEARCH_HOST=\"$OPENSEARCH_HOST\"" >> ~/.bashrc
tail -2 ~/.bashrc

Example output:

export STRANDS_KNOWLEDGE_BASE_ID="LCQBOPKXCY"
export OPENSEARCH_HOST="ffcqjjuzn8bbr1wy60fi.us-west-2.aoss.amazonaws.com"
This module was tested using a Bedrock knowledge base. If you experience odd behavior or missing data, verify that you've properly initialized the STRANDS_KNOWLEDGE_BASE_ID and OPENSEARCH_HOST environment variables.

Overview
Feature	Description
Tools Used	use_llm, memory
Complexity	Beginner
Agent Type	Single Agent with Decision Workflow
Interaction	Command Line Interface
Key Focus	Knowledge Base Operations
Tool Overview
The knowledge base agent utilizes two primary tools:

memory: Enables storing and retrieving information from a knowledge base with capabilities for:

Storing text content with automatic indexing
Retrieving information based on semantic similarity
Setting relevance thresholds and result limits
use_llm: Provides language model capabilities for:

Determining whether a user query is asking to store or retrieve information
Generating natural language responses based on retrieved information
Code-Defined Agentic Workflow
This example demonstrates a workflow where the agent's behavior is explicitly defined in code rather than relying on the agent to determine which tools to use. This approach provides several advantages:

Actions
memory() (store)
memory() (retrieve)
use_llm()
User Input (Query)
Intent Classification
Conditional Execution Based on Intent
Key Workflow Components
Lets look at specific parts of the code in strands_knowledgebase_agent_example/knowledge_base_agent.py

Intent Classification Layer

The workflow begins with a dedicated classification step that uses the language model to determine user intent:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
def determine_action(agent, query):
    """Determine if the query is a store or retrieve action."""
    result = agent.tool.use_llm(
        prompt=f"Query: {query}",
        system_prompt=ACTION_SYSTEM_PROMPT
    )
    
    # Clean and extract the action
    action_text = str(result).lower().strip()
    
    # Default to retrieve if response isn't clear
    if "store" in action_text:
        return "store"
    else:
        return "retrieve"

This classification is performed with a specialized system prompt that focuses solely on distinguishing between storage and retrieval intents, making the classification more deterministic.

Conditional Execution Paths

Based on the classification result, the workflow follows one of two distinct execution paths:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
def run_kb_agent(query):
    ...

    # Determine the action - store or retrieve
    action = determine_action(agent, query)

    if action == "store":
        # Store path
        agent.tool.memory(action="store", content=query)
        print("\nI've stored this information.")
    else:
        # Retrieve path
        result = agent.tool.memory(action="retrieve", query=query, min_score=0.4, max_results=9)
        # Generate response from retrieved information
        answer = agent.use_llm(prompt=f"User question: \"{query}\"\n\nInformation from knowledge base:\n{result_str}...",
                               system_prompt=ANSWER_SYSTEM_PROMPT)

Tool Chaining for Retrieval

The retrieval path demonstrates tool chaining, where the output from one tool becomes the input to another:

User Query
memory() Retrieval
use_llm()
Response
This chaining allows the agent to:

First retrieve relevant information from the knowledge base
Then process that information to generate a natural, conversational response
Implementation Benefits
1. Deterministic Behavior
Explicitly defining the workflow in code ensures deterministic agent behavior rather than probabilistic outcomes. The developer precisely controls which tools are executed and in what sequence, eliminating the non-deterministic variability that occurs when an agent autonomously selects tools based on natural language understanding.

2. Optimized Tool Usage
Direct tool calls allow for precise parameter tuning:

1
2
3
4
5
6
7
# Optimized retrieval parameters
result = agent.tool.memory(
    action="retrieve", 
    query=query,
    min_score=0.1,  # Set minimum relevance threshold
    max_results=9   # Limit number of results
)

These parameters can be fine-tuned based on application needs without relying on the agent to discover optimal values.

3. Specialized System Prompts
The code-defined workflow enables the use of highly specialized system prompts for each task:

A focused classification prompt for intent determination
A separate response generation prompt for creating natural language answers
This specialization improves performance compared to using a single general-purpose prompt.

Example Interactions
1
2
cd ~/workshop/strands_knowledgebase_agent_example
uv run knowledge_base_agent.py

Try typing in the following queries (please be careful not to enter any sensitive or PII data):

Interaction 1: Retrieving information from the knowledge base

1
I am 41 years old

Example output:

Processing...
store
I've stored this information.
Interaction 2: Retrieving information from the knowledge base

1
What is my age?

Example output:

Processing...
retrieve

You're 41 years old.
If retrievals fail, you can decrease the value of min_score In knowledge_base_agent.py. Conversely, you can increase the value of min_score to reduce the likelihood of hallucinations.

Where is this information stored? You can browse to your Knowledge Base in the Bedrock Knowldge Bases console. If you click on the pets data source (named something like pets-kb-07c9967d), you can see the new documents that have been ingested.

KB - Custom Data Source - Memory

Extending the Example
Here are some ways to extend this knowledge base agent:

Multi-Step Reasoning: Add capabilities for complex queries requiring multiple retrieval steps
Information Updating: Implement functionality to update existing information
Multi-Modal Storage: Add support for storing and retrieving images or other media
Knowledge Organization: Implement categorization or tagging of stored information

Module 4: Building Workflow Agent with Strands
Agentic Workflow: Research Assistant - Multi-Agent Collaboration Example
Open VSCode and locate the strands_workflow_agent_example/agents_workflow.py file in your workspace.

This example shows how to create a multi-agent workflow using Strands agents to perform web research, fact-checking, and report generation. It demonstrates specialized agent roles working together in sequence to process information.

Overview
Feature	Description
Tools Used	http_request
Agent Structure	Multi-Agent Workflow (3 Agents)
Complexity	Intermediate
Interaction	Command Line Interface
Key Technique	Agent-to-Agent Communication
Tools Overview
http_request
The http_request tool enables the agent to make HTTP requests to retrieve information from the web. It supports GET, POST, PUT, and DELETE methods, handles URL encoding and response parsing, and returns structured data from web sources. While this tool is used in the example to gather information from the web, understanding its implementation details is not crucial to grasp the core concept of multi-agent workflows demonstrated in this example.

Workflow Architecture
The Research Assistant example implements a three-agent workflow where each agent has a specific role and work together to complete tasks that require multiple steps of processing:

Researcher Agent: Gathers information from web sources using http_request tool
Analyst Agent: Verifies facts and identifies key insights from research findings
Writer Agent: Creates a final report based on the analysis
Code Structure and Implementation
1. Agent Initialization
Each agent in the workflow is created with a system prompt that defines its role:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
def run_research_workflow(user_input):
    ...

    # Researcher Agent with web capabilities
    researcher_agent = Agent(
        system_prompt=(
            "You are a Researcher Agent that gathers information from the web. "
            "1. Determine if the input is a research query or factual claim "
            "2. Use your research tools (http_request, retrieve) to find relevant information "
            "3. Include source URLs and keep findings under 500 words"
        ),
        callback_handler=None,
        tools=[http_request]
    )
    ...

    # Analyst Agent for verification and insight extraction
    analyst_agent = Agent(
        callback_handler=None,
        system_prompt=(
            "You are an Analyst Agent that verifies information. "
            "1. For factual claims: Rate accuracy from 1-5 and correct if needed "
            "2. For research queries: Identify 3-5 key insights "
            "3. Evaluate source reliability and keep analysis under 400 words"
        ),
    )
    ...

    # Writer Agent for final report creation
    writer_agent = Agent(
        system_prompt=(
            "You are a Writer Agent that creates clear reports. "
            "1. For fact-checks: State whether claims are true or false "
            "2. For research: Present key insights in a logical structure "
            "3. Keep reports under 500 words with brief source mentions"
        )
    )
    ...

2. Workflow Orchestration
The workflow is orchestrated through a function that passes information between agents:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
def run_research_workflow(user_input):
    ...

    # Step 1: Researcher Agent gathers web information
    researcher_response = researcher_agent(
        f"Research: '{user_input}'. Use your available tools to gather information from reliable sources.",
    )
    research_findings = str(researcher_response)
    ...

    
    # Step 2: Analyst Agent verifies facts
    analyst_response = analyst_agent(
        f"Analyze these findings about '{user_input}':\n\n{research_findings}",
    )
    analysis = str(analyst_response)
    ...

    
    # Step 3: Writer Agent creates report
    final_report = writer_agent(
        f"Create a report on '{user_input}' based on this analysis:\n\n{analysis}"
    )
    
    return final_report

3. Output Suppression
The example suppresses intermediate outputs during the initialization of the agents, showing users only the final result from the Writer Agent:

1
2
3
4
5
6
7
8
9
10
researcher_agent = Agent(
    system_prompt=(
        "You are a Researcher Agent that gathers information from the web. "
        "1. Determine if the input is a research query or factual claim "
        "2. Use your research tools (http_request, retrieve) to find relevant information "
        "3. Include source URLs and keep findings under 500 words"
    ),
    callback_handler=None, # Suppresses output
    tools=[http_request]
)

Without this suppression, the default callback_handler  would print all outputs to stdout, creating a cluttered experience with duplicate information from each agent's thinking process and tool calls. Suppressing the output creates a clean user experience by preventing intermediate outputs while still allowing responses to be captured programmatically and enabling proper information flow between agents. Instead of verbose agent outputs, the code provides concise progress feedback through simple print statements:

1
2
3
4
print("\nProcessing: '{user_input}'")
print("\nStep 1: Researcher Agent gathering web information...")
print("Research complete")
print("Passing research findings to Analyst Agent...\n")

Sample Queries and Responses
1
2
cd ~/workshop/strands_workflow_agent_example
uv run agents_workflow.py

Try typing in the following queries (please be careful not to enter any sensitive or PII data):

Query 1:

1
What are quantum computers?

Example Response:

Processing: 'What are quantum computers?'

Step 1: Researcher Agent gathering web information...
Research complete
Passing research findings to Analyst Agent...

Step 2: Analyst Agent analyzing findings...
Analysis complete
Passing analysis to Writer Agent...

Step 3: Writer Agent creating final report...
### Report on Quantum Computers

**Fact-Check:**
The claims regarding quantum computers are true. Quantum computers utilize quantum mechanics principles, employ qubits that can exist in multiple states simultaneously, and have potential applications in various fields. The challenges of maintaining qubit coherence and error correction are also accurately described.

**Key Insights:**

1. **Quantum Mechanics Utilization**:
   Quantum computers leverage principles of quantum mechanics to perform computations. This allows them to process information in fundamentally different ways compared to classical computers, which rely on binary bits (0s and 1s).

2. **Qubits and Superposition**:
   Qubits, the fundamental units of quantum computers, can exist in multiple states at once due to the principle of superposition. This capability enables quantum computers to perform many calculations simultaneously, offering a significant advantage over classical computers.

3. **Potential Applications**:
   Quantum computers have the potential to revolutionize fields such as cryptography, optimization, and quantum system simulation. They can solve problems that are currently intractable for classical computers, such as factoring large numbers or simulating molecular interactions.

4. **Current Stage**:
   While several quantum computers have been built and demonstrate the fundamental principles, the technology is still in the experimental stage. They are not yet ready for widespread practical use but are being actively researched and developed.

5. **Challenges**:
   Significant challenges remain, including maintaining qubit coherence and developing effective error correction methods. These issues are critical for the practical deployment of quantum computers and are areas of ongoing research.

**Source Reliability:**
The information is sourced from Encyclopædia Britannica, a highly reliable authority known for its rigorous editorial standards and comprehensive coverage of scientific and technological topics.

**Summary:**
Quantum computers represent a significant advancement in computational technology, utilizing quantum mechanics to perform complex calculations more efficiently than classical computers. They use qubits that can exist in multiple states simultaneously, enabling parallel processing. Although the technology is still experimental, potential applications include cryptography, optimization, and quantum system simulation. Key challenges such as maintaining qubit coherence and error correction need to be addressed before quantum computers can be widely adopted. The provided information is accurate and sourced from a reliable authority.Report creation complete
Note: if you get the following error, this could be due to reasons such as throttling, wait a while, and try entering the query again.

...
urllib3.exceptions.ProtocolError: Response ended prematurely

An error occurred: Response ended prematurely
Please try a different request.
Query 2:

1
Lemon cures cancer

Example Response:

Processing: 'Lemon cures cancer'

Step 1: Researcher Agent gathering web information...
Research complete
Passing research findings to Analyst Agent...

Step 2: Analyst Agent analyzing findings...
Analysis complete
Passing analysis to Writer Agent...

Step 3: Writer Agent creating final report...
**Report on the Claim "Lemon Cures Cancer"**

**Factual Claims Accuracy: False**
The assertion that "Lemon cures cancer" is false. While lemons are rich in vitamin C and antioxidants, which can support immune function and overall health, there is no scientific evidence to substantiate the claim that lemons can cure cancer.

**Key Insights:**

1. **Nutritional Benefits of Lemons:**
   - **Vitamin C:** Lemons are a good source of vitamin C, which is essential for the immune system and skin health.
   - **Antioxidants:** They contain antioxidants that help combat oxidative stress in the body.

2. **Cancer Treatment:**
   - **Standard Treatments:** Effective cancer treatment typically includes surgery, chemotherapy, radiation therapy, immunotherapy, and targeted therapy.
   - **Medical Supervision:** These treatments are administered under the guidance of healthcare professionals.

3. **Diet and Cancer:**
   - **Supportive Role:** A healthy diet can support the body during cancer treatment but should complement, not replace, established medical treatments.
   - **Balanced Nutrition:** Incorporating a variety of fruits and vegetables, including lemons, can contribute to overall health.

4. **Misinformation Risks:**
   - **Delayed Treatment:** Believing in unverified claims about natural remedies curing cancer can lead to harmful delays in seeking proper medical care.
   - **Informed Decisions:** It is crucial to rely on evidence-based information and consult healthcare professionals for cancer treatment.

**Source Reliability:**
The information presented aligns with reputable health organizations such as the American Cancer Society, Mayo Clinic, and National Cancer Institute. These sources emphasize that no single food, including lemons, can cure cancer. They are authoritative in the fields of oncology and nutrition.

**Summary:**
The claim that lemons can cure cancer is unsupported by scientific evidence and is misleading. While lemons offer nutritional benefits, they should not be considered a cancer treatment. It is essential to consult healthcare professionals for accurate and effective cancer treatment options. 

**Sources:**
- American Cancer Society
- Mayo Clinic
- National Cancer InstituteReport creation complete
Example Query 3:

1
Interest rates have been decreasing recently.

(Note: this may take some time to process, feel free to try a different prompt, or to skip this step altogether)

Response:

Processing: 'Interest rates have been decreasing recently.'

Step 1: Researcher Agent gathering web information...
Research complete
Passing research findings to Analyst Agent...

Step 2: Analyst Agent analyzing findings...
Analysis complete
Passing analysis to Writer Agent...

Step 3: Writer Agent creating final report...
### Report on "Interest Rates Have Been Decreasing Recently"

#### Factual Claims Analysis

**Claim Accuracy: Mostly True**

The statement "interest rates have been decreasing recently" is mostly accurate. However, there is an error in the dates provided. The Federal Reserve Bank of St. Louis's FRED website does not provide data for May 21, 2025, as it is in the future. The most recent available data should be verified for accuracy.

**Correction:**
- The interest rate was 4.28% on May 19, 2023, and decreased to 4.24% on May 20, 2023 (most recent available data).

#### Research Insights

1. **Recent Decreasing Trend:**
   - The 3-Month Treasury Bill Secondary Market Rate (DTB3) has shown a slight decrease over a short period. This trend suggests potential shifts in monetary policy or market sentiment.

2. **Economic Indicators:**
   - A decrease in short-term interest rates can indicate various economic conditions, such as reduced inflation expectations or changes in the Federal Reserve's policy stance.

3. **Market Reactions:**
   - Investors and financial institutions may respond to these changes by adjusting their portfolios, which can affect borrowing costs and investment strategies.

#### Source Reliability

**Source: [FRED, Federal Reserve Bank of St. Louis](https://fred.stlouisfed.org/series/DTB3)**

**Reliability Evaluation:**
- **Credibility:** The Federal Reserve Economic Data (FRED) is a highly reliable source maintained by the Federal Reserve Bank of St. Louis, a reputable and authoritative economic data provider.
- **Timeliness:** FRED provides up-to-date economic data, although the most recent data might not always be immediately available.
- **Transparency:** The data is openly accessible, and methodologies for data collection and calculation are well-documented.

#### Summary

The claim about decreasing interest rates is largely accurate, with a minor correction needed regarding the dates. The insights highlight the significance of short-term interest rate movements in economic analysis. The source, FRED, is reliable and credible for economic data.Report creation complete
Type exit to exit the application.

Extending the Example
Here are some ways to extend this agents workflow example:

Add User Feedback Loop: Allow users to ask for more detail after receiving the report
Implement Parallel Research: Modify the Researcher Agent to gather information from multiple sources simultaneously
Add Visual Content: Enhance the Writer Agent to include images or charts in the report
Create a Web Interface: Build a web UI for the workflow
Add Memory: Implement session memory so the system remembers previous research sessions


Module 5: Building Memory Agent with Strands
🧠 Mem0 Memory Agent - Personalized Context Through Persistent Memory
Open VSCode and locate the strands_memory_agent_example/mem0_agent.py file in your workspace.

This example demonstrates how to create a Strands agent that leverages mem0.ai  to maintain context across conversations and provide personalized responses. It showcases how to store, retrieve, and utilize memories to create more intelligent and contextual AI interactions.

Overview
Feature	Description
Tools Used	mem0_memory, use_llm
Complexity	Intermediate
Agent Type	Single Agent with Memory Management
Interaction	Command Line Interface
Key Focus	Memory Operations & Contextual Responses
Tool Overview
The memory agent utilizes two primary tools:

memory: Enables storing and retrieving information with capabilities for:

Storing user-specific information persistently
Retrieving memories based on semantic relevance
Listing all stored memories for a user
Setting relevance thresholds and result limits
use_llm: Provides language model capabilities for:

Generating conversational responses based on retrieved memories
Creating natural, contextual answers using memory context
Memory-Enhanced Response Generation Workflow
This example demonstrates a workflow where memories are used to generate contextually relevant responses:

┌─────────────────┐     ┌─────────────────────────┐     ┌─────────────────────────┐
│                 │     │                         │     │                         │
│   User Query    │────▶│  Command Classification │────▶│  Conditional Execution  │
│                 │     │  (store/retrieve/list)  │     │  Based on Command Type  │
│                 │     │                         │     │                         │
└─────────────────┘     └─────────────────────────┘     └───────────┬─────────────┘
                                                                    │
                                                                    │
                                                                    ▼
                           ┌───────────────────────────────────────────────────────┐
                           │                                                       │
                           │  Store Action     List Action      Retrieve Action    │
                           │  ┌───────────┐    ┌───────────┐    ┌───────────────┐  │
                           │  │           │    │           │    │               │  │
                           │  │ mem0()    │    │ mem0()    │    │ mem0()        │  │
                           │  │ (store)   │    │ (list)    │    │ (retrieve)    │  │
                           │  │           │    │           │    │               │  │
                           │  └───────────┘    └───────────┘    └───────┬───────┘  │
                           │                                            │          │
                           │                                            ▼          │
                           │                                      ┌───────────┐    │
                           │                                      │           │    │
                           │                                      │ use_llm() │    │
                           │                                      │           │    │
                           │                                      └───────────┘    │
                           │                                                       │
                           └───────────────────────────────────────────────────────┘
Key Workflow Components
In memory_agent.py the mem0_memory tool is imported in the statement: from strands_tools import mem0_memory, use_llm. You can find the implementation details at https://github.com/strands-agents/tools/blob/main/src/strands_tools/mem0_memory.py .

Command Classification Layer

The workflow begins by looking at the user's input to determine the appropriate memory operation:

Excerpt from mem0_memory.py 

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
def mem0_memory(tool: ToolUse, **kwargs: Any) -> ToolResult:
    ...
    try:
        ...
        tool_input = tool.get("input", {})
        ...

        # Handle different actions
        action = tool_input["action"]
        ...

        if needs_confirmation:
            if action == "store":
                ...
            elif action == "delete":
                ...

        # Execute the requested action
        if action == "store":
           ...
        elif action == "get":
           ...
        elif action == "list":
           ...
        elif action == "retrieve":
           ...
        elif action == "delete":              
           ...
        elif action == "history":
           ...

The code above performs actions such as storing new information, listing existing memories, or retrieving relevant memories to answer a question.

Memory Retrieval and Response Generation

The workflow's most powerful feature is its ability to retrieve relevant memories and use them to generate contextual responses:

Excerpt from mem0_memory.py 

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
def mem0_memory(tool: ToolUse, **kwargs: Any) -> ToolResult:
    ...
     elif action == "retrieve":
         if not tool_input.get("query"):
             raise ValueError("query is required for retrieve action")

         memories = client.search_memories(
             tool_input["query"],
             tool_input.get("user_id"),
             tool_input.get("agent_id"),
         )
         panel = format_retrieve_response(memories)
         console.print(panel)
         return ToolResult(
             toolUseId=tool_use_id,
             status="success",
             content=[ToolResultContent(text=json.dumps(memories.get("results", []), indent=2))],
         )

Excerpt from use_llm.py 

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
def use_llm(tool: ToolUse, **kwargs: Any) -> ToolResult:
    ...
    tool_use_id = tool["toolUseId"]
    tool_input = tool["input"]

    prompt = tool_input["prompt"]
    tool_system_prompt = tool_input.get("system_prompt")
    ...
    # Initialize the new Agent with provided parameters
    agent = Agent(
        messages=[],
        tools=tools,
        system_prompt=tool_system_prompt,
        trace_attributes=trace_attributes,
        **extra_kwargs,
    )
    # Run the agent with the provided prompt
    result = agent(prompt)

    # Extract response
    assistant_response = str(result)
    ...
    return {
        "toolUseId": tool_use_id,
        "status": "success",
        "content": [
            {"text": f"Response: {assistant_response}"},
            {"text": f"Metrics: {metrics_text}"},
        ],
    }

This two-step process:

First retrieves the most semantically relevant memories using the memory tool
Then feeds those memories to an LLM to generate a natural, conversational response
Tool Chaining for Enhanced Responses

The retrieval path demonstrates tool chaining, where memory retrieval and LLM response generation work together:

┌───────────────┐     ┌───────────────────────┐     ┌───────────────┐
│               │     │                       │     │               │
│  User Query   │────▶│  memory() Retrieval   │────▶│  use_llm()    │────▶ Response
│               │     │                       │     │               │
└───────────────┘     └───────────────────────┘     └───────────────┘
                      (Finds relevant memories)     (Generates natural
                                                    language answer)
This chaining allows the agent to:

First retrieve memories that are semantically relevant to the user's query
Then process those memories to generate a natural, conversational response that directly addresses the query
Implementation Benefits
1. Object-Oriented Design
The Memory Agent is implemented as a class, providing encapsulation and clean organization of functionality:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
class Mem0ServiceClient:
    """Client for interacting with Mem0 service."""

    DEFAULT_CONFIG = {
        "embedder": {"provider": "aws_bedrock", "config": {"model": "amazon.titan-embed-text-v2:0"}},
        "llm": {
            "provider": "aws_bedrock",
            "config": {
                "model": "anthropic.claude-3-5-haiku-20241022-v1:0",
                "temperature": 0.1,
                "max_tokens": 2000,
            },
        },
        "vector_store": {
            "provider": "opensearch",
            "config": {
                "port": 443,
                "collection_name": "mem0_memories",
                "host": os.environ.get("OPENSEARCH_HOST"),
                "embedding_model_dims": 1024,
                "connection_class": RequestsHttpConnection,
                "pool_maxsize": 20,
                "use_ssl": True,
                "verify_certs": True,
            },
        },
    }

    def __init__(self, config: Optional[Dict] = None):
        ...

        # Check for required OPENSEARCH_HOST
        opensearch_host = os.environ.get("OPENSEARCH_HOST")
        ...

    def store_memory(
        self,
        content: str,
        user_id: Optional[str] = None,
        agent_id: Optional[str] = None,
        metadata: Optional[Dict] = None,
    ):
        # Implementation

    def get_memory(self, memory_id: str):
        # Implementation

    def list_memories(self, user_id: Optional[str] = None, agent_id: Optional[str] = None):
        # Implementation

    def search_memories(self, query: str, user_id: Optional[str] = None, agent_id: Optional[str] = None):
        # Implementation

    def delete_memory(self, memory_id: str):
        # Implementation

    def get_memory_history(self, memory_id: str):
        # Implementation

This design provides:

Clear separation of concerns
Reusable components
Easy extensibility
Clean interface for interacting with memory operations
2. Specialized System Prompts
You can use specialized system prompts for different tasks:

Memory Agent System Prompt: Focuses on general memory operations

1
2
3
MEMORY_SYSTEM_PROMPT = """You are a memory specialist agent. You help users store, 
retrieve, and manage memories. You maintain context across conversations by remembering
important information about users and their preferences...

Answer Generation System Prompt: Specialized for generating responses from memories

1
2
ANSWER_SYSTEM_PROMPT = """You are an assistant that creates helpful responses based on retrieved memories.
Use the provided memories to create a natural, conversational response to the user's question...

This specialization improves performance by focusing each prompt on a specific task rather than using a general-purpose prompt.

3. Explicit Memory Structure
The agent initializes with structured memories to demonstrate memory capabilities:

1
2
3
4
5
6
def initialize_demo_memories(memory_agent) -> None:
    init_memories = f"My name is {USER_ID}. I like to travel and stay in Airbnbs rather than hotels. I am planning a trip to Japan next spring. I enjoy hiking and outdoor photography as hobbies. I have a dog named Max. My favorite cuisine is Italian food."
    memory_agent.tool.mem0_memory(
        action = "store",
        content = init_memories
    )

These memories provide:

Examples of what can be stored
Demonstration data for retrieval operations
A baseline for testing functionality
Important Requirements
The memory tool requires either a user_id or agent_id for most operations:

Required for:

Storing new memories
Listing all memories
Retrieving memories via semantic search
Not required for:

Getting a specific memory by ID
Deleting a specific memory
Getting memory history
This ensures that memories are properly associated with specific users or agents and maintains data isolation between different users.

Example Interactions
We will need to make sure that the environment variable $OPENSEARCH_HOST is set properly, prior to running the Streamlit App. Let's make sure it's saved in ~/.bashrc, and we will load this value into our environment.

1
2
3
tail -3 ~/.bashrc
source ~/.bashrc
echo "OPENSEARCH_HOST=\"$OPENSEARCH_HOST\""

1
2
3
export USER_ID="Alex"  # Feel free to change this to another name
cd ~/workshop/strands_memory_agent_example/
uv run mem0_agent.py

Try typing in the following queries (please be careful not to enter any sensitive or PII data):

Interaction 1: Storing Information

1
My name is J, I am 34 years old, I like seafood, and I have a pet dog

(Note: if you see a message such as "Could you please provide your user_id so I can store this information about your age?", key in a user ID such as Alex)

Example output:

I'll help store this personal information as a memory. Since this is personal information about you, I'll store it using the mem0_memory tool with your identifier.
Tool #1: mem0_memory
╭──────────────────────────────────────────────────────────── Memory for user J ─────────────────────────────────────────────────────────────╮
│ J is 34 years old, likes seafood, and has a pet dog.                                                                                       │
╰────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
╭────────────────────────────────────────────────────────────── Memory Stored ───────────────────────────────────────────────────────────────╮
│                           Memory Stored                                                                                                    │
│ ┏━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┓                                                                         │
│ ┃ Operation ┃ Content                                            ┃                                                                         │
│ ┡━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┩                                                                         │
│ │ ADD       │ J is 34 years old                                  │                                                                         │
│ │ ADD       │ Likes seafood                                      │                                                                         │
│ │ ADD       │ Has a pet dog                                      │                                                                         │
│ └───────────┴────────────────────────────────────────────────────┘                                                                         │
╰────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
I've stored your personal information in the memory system. This will help me remember these details about you for future interactions. Is there anything else you'd like to share or would you like me to recall any of this information?
Interaction 2: Retrieving Information

1
What is my age?

Example output:

Let me search through the stored memories to find information about your age.
Tool #2: mem0_memory
╭────────────────────────────────────────────────────────────── Search Results ──────────────────────────────────────────────────────────────╮
│                                                               Search Results                                                               │
│ ┏━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━┳━━━━━━━━━━┓ │
│ ┃ ID                     ┃ Memory                                             ┃ Relevance  ┃ Created At             ┃ User ID ┃ Metadata ┃ │
│ ┡━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━╇━━━━━━━━━━┩ │
│ │ 612e1b6e-6d6f-4f87-b2… │ J is 34 years old                                  │ 0.6068592  │ 2025-08-08T22:15:39.8… │ J       │ None     │ │
│ │ c9c9a6b8-cf6f-40c2-aa… │ Likes seafood                                      │ 0.571997   │ 2025-08-08T22:15:40.0… │ J       │ None     │ │
│ │ 4d970791-701b-4d8e-a8… │ Has a pet dog                                      │ 0.54865587 │ 2025-08-08T22:15:40.3… │ J       │ None     │ │
│ └────────────────────────┴────────────────────────────────────────────────────┴────────────┴────────────────────────┴─────────┴──────────┘ │
╰────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
Based on the stored memory, you are 34 years old.
Interaction 3: Listing All Memories

1
Tell me everything that you know about me

I'll retrieve all stored memories about you.
Tool #3: mem0_memory
╭────────────────────────────────────────────────────────────── Memories List ───────────────────────────────────────────────────────────────╮
│                                                                  Memories                                                                  │
│ ┏━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━┳━━━━━━━━━┳━━━━━━━━━━┓ │
│ ┃ ID                           ┃ Memory                                             ┃ Created At                    ┃ User ID ┃ Metadata ┃ │
│ ┡━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━╇━━━━━━━━━╇━━━━━━━━━━┩ │
│ │ c9c9a6b8-cf6f-40c2-aac1-5ba… │ Likes seafood                                      │ 2025-08-08T22:15:40.083905-0… │ J       │ None     │ │
│ │ 612e1b6e-6d6f-4f87-b2c6-ae7… │ J is 34 years old                                  │ 2025-08-08T22:15:39.859347-0… │ J       │ None     │ │
│ │ 4d970791-701b-4d8e-a851-288… │ Has a pet dog                                      │ 2025-08-08T22:15:40.320217-0… │ J       │ None     │ │
│ └──────────────────────────────┴────────────────────────────────────────────────────┴───────────────────────────────┴─────────┴──────────┘ │
╰────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
Here's everything I know about you:
1. Your name is J
2. You are 34 years old
3. You like seafood
4. You have a pet dog
Type exit to exit the application.

Sample Output
Output from Memory Agent

Extending the Example
Here are some ways to extend this memory agent:

Memory Categories: Implement tagging or categorization of memories for better organization
Memory Prioritization: Add importance levels to memories to emphasize critical information
Memory Expiration: Implement time-based relevance for memories that may change over time
Multi-User Support: Enhance the system to manage memories for multiple users simultaneously
Memory Visualization: Create a visual interface to browse and manage memories
Proactive Memory Usage: Have the agent proactively suggest relevant memories in conversations
For more advanced memory management features and detailed documentation, visit Mem0 documentation .

Module 6: Building Meta Agent with Strands
Meta-Tooling Example - Strands Agent's Dynamic Tool Creation
Open VSCode and locate the strands_meta_tooling_agent_example/meta_tooling.py file in your workspace.

Meta-tooling refers to the ability of an AI system to create new tools at runtime, rather than being limited to a predefined set of capabilities. This example demonstrates Strands Agents' meta-tooling capabilities - allowing agents to create, load, and use custom tools at runtime.

Overview
Feature	Description
Tools Used	load_tool, shell, editor
Core Concept	Meta-Tooling (Dynamic Tool Creation)
Complexity	Advanced
Interaction	Command Line Interface
Key Technique	Runtime Tool Generation
Tools Used Overview
The meta-tooling agent use three primary tools to create and manage dynamic tools:

load_tool: enables dynamic loading of Python tools at runtime, registering new tools with the agent's registry, enabling hot-reloading of capabilities, and validating tool specifications before loading.
editor: allows creation and modification of tool code files with syntax highlighting, making precise string replacements in existing tools, inserting code at specific locations, finding and navigating to specific sections of code, and creating backups with undo capability before modifications.
shell: executes shell commands to debug tool creation and execution problems,supports sequential or parallel command execution, and manages working directory context for proper execution.
How Strands Agent Implements Meta-Tooling
This example showcases how Strands Agent achieves meta-tooling through key mechanisms:

Key Components
1. Agent is initialized with existing tools to help build new tools
The agent is initialized with the necessary tools for creating new tools:

1
2
3
4
5
agent = Agent(
    model=bedrock_model,
    system_prompt=TOOL_BUILDER_SYSTEM_PROMPT,
    tools=[load_tool, shell, editor]
)

editor: Tool used to write code directly to a file named "custom_tool_X.py", where "X" is the index of the tool being created.
load_tool: Tool used to load the tool so the Agent can use it.
shell: Tool used to execute the tool.
2. Agent System Prompt outlines a strict guideline for naming, structure, and creation of the new tools.
The system prompt guides the agent in proper tool creation. The TOOL_BUILDER_SYSTEM_PROMPT  outlines important elements to enable the agent achieve meta-tooling capabilities:

Tool Naming Convention: Provides the naming convention to use when building new custom tools.

Tool Structure: Enforces a standardized structure for all tools, making it possible for the agent to generate valid tools based on the TOOL_SPEC provided .

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
from typing import Any
from strands.types.tool_types import ToolUse, ToolResult

TOOL_SPEC = {
    "name": "tool_name",
    "description": "What the tool does",
    "inputSchema": { 
        "json": {
            "type": "object",
            "properties": {
                "param_name": {
                    "type": "string",
                    "description": "Parameter description"
                }
            },
            "required": ["param_name"]
        }
    }
}

def tool_name(tool_use: ToolUse, **kwargs: Any) -> ToolResult:
    # Tool function docstring
    tool_use_id = tool_use["toolUseId"]
    param_value = tool_use["input"]["param_name"]
    
    # Process inputs
    result = param_value  # Replace with actual processing
    
    return {
        "toolUseId": tool_use_id,
        "status": "success",
        "content": [{"text": f"Result: {result}"}]
    }

Tool Creation vs. Usage : Provides instructions for agent to distinguish between creating new tools vs. using existing tools.
2. Tool Creation through Natural Language Processing
By analyzing the natural language description, the agent uses a combination of its existing tools and the instructions in the system prompt to create additional tools dynamically.

"Create a tool that counts characters in text"
"Make a tool that converts between different units of measurement"
Example Interaction
1
2
cd ~/workshop/strands_meta_tooling_agent_example
uv run meta_tooling.py

Try typing in the following queries (please be careful not to enter any sensitive or PII data):

Step 1: Making a Custom Tool

Input:

1
Create a tool that counts characters in text

(Note: if prompted, type 'y' to proceed)

Output:

I'll help create a character counting tool. Let me handle this step by step.

1. First, I'll create a tool file named "count_characters.py" with the appropriate code:
Tool #1: editor
Do you want to proceed with the create operation? [y/*] y


I notice I need to specify a working directory. Let me try again with the shell command to create a directory first:
Tool #2: shell
Do you want to proceed with execution? [y/*] y


Now I'll create the tool file in the tools directory:
Tool #3: editor
Do you want to proceed with the create operation? [y/*] y


Now I'll load the tool:
Tool #4: load_tool


TOOL_CREATED: count_characters.py

The character counting tool has been successfully created and loaded! The tool:
1. Is named "count_characters"
2. Takes a "text" parameter as input
3. Returns the count of characters in the provided text

Let me demonstrate how to use it:
Tool #5: count_characters


The tool is now ready to use! You can provide any text and it will count the number of characters in it. Would you like to try it with different text?
Step 2: Using the Custom Tool

Input:

1
Count the characters in "Hello, Strands! How are you today?"

Output:

I notice that this request is actually asking to COUNT CHARACTERS in a specific text, not create a new tool. We already have the `count_characters` tool available that can do this task. Let me use it directly:
Tool #6: count_characters


I didn't create a new tool because:
1. We already have a `count_characters` tool that does exactly what's needed
2. The request appears to be asking to perform a character count operation rather than explicitly requesting tool creation
3. Creating another tool would be redundant

The existing tool handled the request perfectly by counting the characters in the text "Hello, Strands! How are you today?", showing it contains 34 characters.

Would you like to count characters in any other text? Or would you like to create a different kind of tool?
Type exit to exit the application.

Extending the Example
The Meta-Tooling example demonstrates a Strands agent's ability to extend its capabilities by creating new tools on demand to adapt to individual user needs.

Here are some ways to enhance this example:

Tool Version Control: Implement versioning for created tools to track changes over time

Tool Testing: Add automated testing for newly created tools to ensure reliability

Tool Improvement: Create tools to improve existing capabilities of existing tools.

Module 7: Building Multi-Agent with Strands
This module contains 4 parts:

Step 1 - Setting up Multi-Agent with Strands
Step 2 - Adding UI to Multi-Agent with Strands
Step 3 - Adding Knowledge Base to Multi-Agent with Strands
Step 4 - Adding Memory to Multi-Agent with Strands
If you would like to create a Bedrock Knowledge Base with S3 using the Python boto3 library, go to the section: [Notes] - Quick Create S3 and Knowledge Base

Creation of the knowledge base in Module 3 is a pre-requisite for Step 3 and Step 4. If you are short of time you can use the Quick Create option in Module 3: Building Knowledge-Base Agent with Strands.

Step 1 - Setting up Multi-Agent with Strands
Teacher's Assistant - Strands Multi-Agent Architecture Example
Open VSCode and locate the strands_multi_agent_example/teachers_assistant.py file in your workspace.

This example demonstrates how to implement a multi-agent architecture using Strands Agents, where specialized agents work together under the coordination of a central orchestrator. The system uses natural language routing to direct queries to the most appropriate specialized agent based on subject matter expertise.

Overview
Feature	Description
Tools Used	calculator, python_repl, shell, http_request, editor, file operations
Agent Structure	Multi-Agent Architecture
Complexity	Intermediate
Interaction	Command Line Interface
Key Technique	Dynamic Query Routing
Tools Used Overview
The multi-agent system utilizes several tools to provide specialized capabilities:

calculator: Advanced mathematical tool powered by SymPy that provides comprehensive calculation capabilities including expression evaluation, equation solving, differentiation, integration, limits, series expansions, and matrix operations.

python_repl: Executes Python code in a REPL environment with interactive PTY support and state persistence, allowing for running code snippets, data analysis, and complex logic execution.

shell: Interactive shell with PTY support for real-time command execution that supports single commands, multiple sequential commands, parallel execution, and error handling with live output.

http_request: Makes HTTP requests to external APIs with comprehensive authentication support including Bearer tokens, Basic auth, JWT, AWS SigV4, and enterprise authentication patterns.

editor: Advanced file editing tool that enables creating and modifying code files with syntax highlighting, precise string replacements, and code navigation capabilities.

file operations: Tools such as file_read and file_write for reading and writing files, enabling the agents to access and modify file content as needed.

Architecture Diagram
Teacher's Assistant
(Orchestrator)

Central coordinator that
routes queries to specialists
Query Classification & Routing
Math Assistant

Handles mathematical
calculations and concepts
English Assistant

Processes grammar and
language comprehension
Language Assistant

Manages translations and
language-related queries
Computer Science Assistant

Handles programming and
technical concepts
General Assistant

Processes queries outside
specialized domains
Calculator Tool

Advanced mathematical
operations with SymPy
Editor & File Tools

Text editing and
file manipulation
HTTP Request Tool

External API access
for translations
Python REPL, Shell & File Tools

Code execution and
file operations
No Specialized Tools

General knowledge
without specific tools
How It Works and Component Implementation
This example implements a multi-agent architecture where specialized agents work together under the coordination of a central orchestrator. Let's explore how this system works and how each component is implemented.

1. Teacher's Assistant (Orchestrator)
The teacher_assistant acts as the central coordinator that analyzes incoming natural language queries, determines the most appropriate specialized agent, and routes queries to that agent. All of this is accomplished through instructions outlined in the TEACHER_SYSTEM_PROMPT  for the agent. Furthermore, each specialized agent is part of the tools array for the orchestrator agent.

Implementation:

teacher_agent = Agent(
    system_prompt=TEACHER_SYSTEM_PROMPT,
    callback_handler=None,
    tools=[math_assistant, language_assistant, english_assistant, 
           computer_science_assistant, general_assistant],
)
The orchestrator suppresses its intermediate output by setting callback_handler to None. Without this suppression, the default PrintingStreamHandler would print all outputs to stdout, creating a cluttered experience with duplicate information from each agent's thinking process and tool calls.
2. Specialized Agents
Each specialized agent is implemented as a Strands tool using the with domain-specific capabilities. This type of architecture allows us to initialize each agent with focus on particular domains, have specialized knowledge, and use specific tools to process queries within their expertise. For example:

For Example:

The Math Assistant handles mathematical calculations, problems, and concepts using the calculator tool.

Implementation:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
@tool
def math_assistant(query: str) -> str:
    """
    Process and respond to math-related queries using a specialized math agent.
    """
    # Format the query for the math agent with clear instructions
    formatted_query = f"Please solve the following mathematical problem, showing all steps and explaining concepts clearly: {query}"
    
    try:
        print("Routed to Math Assistant")
        # Create the math agent with calculator capability
        math_agent = Agent(
            system_prompt=MATH_ASSISTANT_SYSTEM_PROMPT,
            tools=[calculator],
        )
        response = math_agent(formatted_query)
        
        # Extract and return the response text
        # (response processing code)
        
    except Exception as e:
        return f"Error processing your mathematical query: {str(e)}"

**Each specialized agent has a distinct system prompt, and tools in its inventory, and follows this general pattern.

Language Assistant  specializes in queries related to translation into different languages.
Computer Scince Assistant  specializes in queries related to writing, editing, running, code and explaining computer science concepts.
English Assistant  specializes in queries related to grammer, and english comprehension.
General Assistant  is a no specialty agent that aims to answer quries outside of the specific domains the agents are specialized in.
3. Tool-Agent Pattern
This example demonstrates the "Tool-Agent Pattern"  where Strands agents are wrapped as tools using the @tool decorator. These tools are then provided to another agent (the Teacher's Assistant), creating a system where agents can use other agents as tools.

Sample Interactions
1
2
cd ~/workshop/strands_multi_agent_example
uv run teachers_assistant.py

Try typing in the following queries (please be careful not to enter any sensitive or PII data):

Example 1: Mathematics Question

Input:

1
Solve the quadratic equation x^2 + 5x + 6 = 0

Example Output (Routed to Math Assistant):

Routed to Math Assistant
I'll solve the quadratic equation x² + 5x + 6 = 0 step by step, showing multiple methods and explaining the concepts clearly.
Tool #1: calculator
Perfect! Now let me explain this solution step by step using multiple approaches to help you understand the concepts.

## Solution to x² + 5x + 6 = 0

**The solutions are x = -3 and x = -2**

Let me show you different methods to solve this quadratic equation:

### Method 1: Factoring (Most Efficient for this equation)

**Step 1:** Identify the quadratic equation in standard form
- We have: x² + 5x + 6 = 0
- This is in the form ax² + bx + c = 0, where a = 1, b = 5, c = 6

**Step 2:** Look for two numbers that multiply to give 'c' and add to give 'b'
- We need two numbers that multiply to 6 and add to 5
- Let's list factor pairs of 6: (1,6), (2,3), (-1,-6), (-2,-3)
- Check which pair adds to 5:
  - 1 + 6 = 7 ❌
  - 2 + 3 = 5 ✓
  - (-1) + (-6) = -7 ❌
  - (-2) + (-3) = -5 ❌

**Step 3:** Factor the quadratic
- x² + 5x + 6 = (x + 2)(x + 3) = 0

**Step 4:** Apply the Zero Product Property
- If (x + 2)(x + 3) = 0, then either (x + 2) = 0 OR (x + 3) = 0
- From x + 2 = 0: x = -2
- From x + 3 = 0: x = -3

### Method 2: Quadratic Formula (Works for any quadratic)

Let me calculate using the quadratic formula to verify:
Tool #2: calculator

Tool #3: calculator
**Using the quadratic formula: x = (-b ± √(b² - 4ac))/(2a)**

- a = 1, b = 5, c = 6
- Discriminant: b² - 4ac = 5² - 4(1)(6) = 25 - 24 = 1
- Since the discriminant is positive, we have two real solutions

**Step 1:** Calculate the discriminant
- Δ = b² - 4ac = 25 - 24 = 1

**Step 2:** Apply the formula
- x = (-5 ± √1)/(2·1) = (-5 ± 1)/2

**Step 3:** Find both solutions
- x₁ = (-5 + 1)/2 = -4/2 = -2
- x₂ = (-5 - 1)/2 = -6/2 = -3

### Verification

Let me verify our solutions by substituting back into the original equation:
Tool #4: calculator

Tool #5: calculator
**For x = -2:**
(-2)² + 5(-2) + 6 = 4 - 10 + 6 = 0 ✓

**For x = -3:**
(-3)² + 5(-3) + 6 = 9 - 15 + 6 = 0 ✓

Both solutions check out!

### Key Concepts Explained

1. **Quadratic Equation**: An equation of the form ax² + bx + c = 0 where a ≠ 0
2. **Zero Product Property**: If AB = 0, then A = 0 or B = 0 (or both)
3. **Factoring**: Breaking down an expression into products of simpler expressions
4. **Discriminant**: The value b² - 4ac tells us about the nature of solutions:
   - If > 0: Two real solutions
   - If = 0: One real solution
   - If < 0: No real solutions (two complex solutions)

### Final Answer
**x = -3 and x = -2**

These are the x-intercepts of the parabola y = x² + 5x + 6, meaning the graph crosses the x-axis at points (-3, 0) and (-2, 0).The quadratic equation \( x^2 + 5x + 6 = 0 \) has been solved. The solutions are \( x = -3 \) and \( x = -2 \). These values are the x-intercepts of the parabola \( y = x^2 + 5x + 6 \), meaning the graph crosses the x-axis at points \((-3, 0)\) and \((-2, 0)\).

If you have any more questions or need further assistance, feel free to ask!
Example 2: Computer Science Question

Input:

1
Write a Python function to check if a string is a palindrome

Example Output (Routed to Computer Science Assistant):

Certainly! A palindrome is a string that reads the same backward as forward. Here's a simple Python function to check if a given string is a palindrome:

```python
def is_palindrome(s: str) -> bool:
    """
    Check if the given string is a palindrome.

    Parameters:
    s (str): The string to check.

    Returns:
    bool: True if the string is a palindrome, False otherwise.
    """
    # Remove any non-alphanumeric characters and convert to lowercase
    cleaned_string = ''.join(e for e in s if e.isalnum()).lower()
    
    # Check if the cleaned string is equal to its reverse
    return cleaned_string == cleaned_string[::-1]

# Example usage:
print(is_palindrome("A man, a plan, a canal, Panama"))  # True
print(is_palindrome("hello"))  # False
``

### Explanation:
1. Cleaning the String: 
   - The function first removes any non-alphanumeric characters (like punctuation and spaces) using a generator expression inside the `join` method.
   - It then converts the string to lowercase to ensure the comparison is case-insensitive.

2. Checking for Palindrome:
   - The function compares the cleaned string with its reverse (`cleaned_string[::-1]`).
   - If they are equal, the function returns `True`, indicating the string is a palindrome. Otherwise, it returns `False`.

### Example:
- `is_palindrome("A man, a plan, a canal, Panama")` returns `True`.
- `is_palindrome("hello")` returns `False`.
Example 3: Language Translation Request

Input:

1
Translate "Hello, how are you?" to Spanish

Example Output (Routed to Language Assistant):

The translation of "Hello, how are you?" to Spanish is "Hola, ¿cómo estás?" 

Here's a breakdown of the translation:
- "Hello" translates to "Hola."
- "how are you?" translates to "¿cómo estás?"

If you are speaking in a more formal context, you might use "¿cómo está usted?" instead of "¿cómo estás?". The phrase "usted" is a formal version of "you," often used when addressing someone with whom you are not familiar or in a professional setting.
Type exit to exit the application.

Extending the Example
Here are some ways you can extend this multi-agent example:

Add Memory: Implement session memory so the system remembers previous interactions
Add More Specialists: Create additional specialized agents for other domains
Implement Agent Collaboration: Enable multiple agents to collaborate on complex queries
Create a Web Interface: Build a simple web UI for the teacher's assistant
Add Evaluation: Implement a system to evaluate and improve routing accuracy

Step 2 - Adding UI to Multi-Agent with Strands
Creating a Hello World Streamlit App
Set up the Python environment, and switch to the workshop folder (if you have not already done so). You will also need to have Streamlit (installed using uv pip install streamlit or uv pip install -r requirements.txt which was performed at the beginning of this workshop).

1
2
source ~/.venv/bin/activate
cd ~/workshop/

[Option 1] Use Q Developer to create a Hello World Streamlit App
Open Q Developer in the left side panel and type:

1
Create a Streamlit hello world application

streamlit-01-hello-app.png

When Q Developer is complete, you will see something like the following

streamlit-02-hello-app-created.png

[Option 2] Create a Hello World Streamlit App
Create a hello world Streamlit app, named app.py as follows:

1
2
3
4
5
6
7
8
9
10
11
cat << EOF > app.py
import streamlit as st

st.title("Hello World!")
st.write("Welcome to my first Streamlit app.")

# Add a simple interactive element
name = st.text_input("Enter your name")
if name:
    st.write(f"Hello, {name}!")
EOF

Run the Streamlit app
1
streamlit run app.py

You will see a pop up in the bottom left corner, that says "Your application running on port 8501 is available". Click the button Open in Browser as shown in the screenshot below:

streamlit-03-open-in-browser

In the browser tab that pops up, type in something into the text box (please avoid entering any sensitive or PII information). You may see something simlar to the following.

streamlit-04-hello-app-ui.png

You can now stop the Streamlit app by pressing Ctrl-C.

Congratulations you have now created and deployed your Streamlit App!

Extending the Hello World Streamlit App with the Strands Multi-agent Example
Let's use Q for Developer to add new capabilities to the app.

In the Q Developer side panel, type something like:

1
Add the capabilities from `strands_multi_agent_example/teachers_assistant.py` to `app.py` to make it a Streamlit chatbot app

There may be some variability in the code generated using the above prompt. The following is the code generated from a similar prompt, during the creation of this workshop. To keep things consistent, let's create app.py directly, using the following code:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
34
35
36
37
38
39
40
41
42
43
44
45
46
47
48
49
50
51
52
53
54
55
56
57
58
59
60
61
62
63
64
65
66
67
68
69
70
71
72
73
74
75
76
77
78
79
80
81
82
83
84
85
86
87
88
89
90
91
92
93
94
95
96
97
98
99
100
101
102
103
104
import streamlit as st
from strands import Agent
from strands.models import BedrockModel

# Import the specialized assistants
from strands_multi_agent_example.computer_science_assistant import computer_science_assistant
from strands_multi_agent_example.english_assistant import english_assistant
from strands_multi_agent_example.language_assistant import language_assistant
from strands_multi_agent_example.math_assistant import math_assistant
from strands_multi_agent_example.no_expertise import general_assistant

# Define the teacher's assistant system prompt
TEACHER_SYSTEM_PROMPT = """
You are TeachAssist, a sophisticated educational orchestrator designed to coordinate educational support across multiple subjects. Your role is to:

1. Analyze incoming student queries and determine the most appropriate specialized agent to handle them:
   - Math Agent: For mathematical calculations, problems, and concepts
   - English Agent: For writing, grammar, literature, and composition
   - Language Agent: For translation and language-related queries
   - Computer Science Agent: For programming, algorithms, data structures, and code execution
   - General Assistant: For all other topics outside these specialized domains

2. Key Responsibilities:
   - Accurately classify student queries by subject area
   - Route requests to the appropriate specialized agent
   - Maintain context and coordinate multi-step problems
   - Ensure cohesive responses when multiple agents are needed

3. Decision Protocol:
   - If query involves calculations/numbers → Math Agent
   - If query involves writing/literature/grammar → English Agent
   - If query involves translation → Language Agent
   - If query involves programming/coding/algorithms/computer science → Computer Science Agent
   - If query is outside these specialized areas → General Assistant
   - For complex queries, coordinate multiple agents as needed

Always confirm your understanding before routing to ensure accurate assistance.
"""

# Set up the page
st.set_page_config(page_title="TeachAssist - Educational Assistant", layout="wide")
st.title("TeachAssist - Educational Assistant")
st.write("Ask a question in any subject area, and I'll route it to the appropriate specialist.")

# Initialize session state for conversation history
if "messages" not in st.session_state:
    st.session_state.messages = []

# Display conversation history
for message in st.session_state.messages:
    with st.chat_message(message["role"]):
        st.markdown(message["content"])

# Initialize the teacher agent
@st.cache_resource
def get_teacher_agent():
    # Specify the Bedrock ModelID
    bedrock_model = BedrockModel(
        model_id="us.amazon.nova-pro-v1:0",
        temperature=0.3,
    )
    
    # Create the teacher agent with specialized tools
    return Agent(
        model=bedrock_model,
        system_prompt=TEACHER_SYSTEM_PROMPT,
        callback_handler=None,
        tools=[math_assistant, language_assistant, english_assistant, computer_science_assistant, general_assistant],
    )

# Get user input
query = st.chat_input("Ask your question here...")

if query:
    # Add user message to chat history
    st.session_state.messages.append({"role": "user", "content": query})
    
    # Display user message
    with st.chat_message("user"):
        st.markdown(query)
    
    # Display assistant response
    with st.chat_message("assistant"):
        message_placeholder = st.empty()
        
        try:
            # Get the teacher agent
            teacher_agent = get_teacher_agent()
            
            # Process the query
            with st.spinner("Thinking..."):
                response = teacher_agent(query)
                content = str(response)
            
            # Display the response
            message_placeholder.markdown(content)
            
            # Add assistant response to chat history
            st.session_state.messages.append({"role": "assistant", "content": content})
            
        except Exception as e:
            error_message = f"An error occurred: {str(e)}"
            message_placeholder.markdown(error_message)
            st.session_state.messages.append({"role": "assistant", "content": error_message})

Now let's run app.py again:

1
streamlit run app.py

Example 1

Let's try one of the following prompts from the earlier section.

1
Solve the quadratic equation x^2 + 5x + 6 = 0

While waiting for the AI to respond, you may wish to watch the output in the VS Code terminal window. This may be useful in case of possible errors.

streamlit-05-multiagent-teacher

In the VSCode console, you'll also see some output simlar the following (middle portion has been truncated to keep things simple):

Routed to Math Assistant
I'll solve this quadratic equation step-by-step and explain the concepts clearly.

Let's solve the quadratic equation x^2 + 5x + 6 = 0 using the calculator function.
Tool #1: calculator


### Solving the Quadratic Equation x^2 + 5x + 6 = 0

A quadratic equation is in the standard form ax^2 + bx + c = 0, where a, b, and c are constants and a ≠ 0.

For our equation x^2 + 5x + 6 = 0:
- a = 1 (coefficient of x^2)
- b = 5 (coefficient of x)
- c = 6 (constant term)
.
.
.
.
.
Therefore, the solutions are x = -2 and x = -3.

#### Verification

We can verify these solutions by substituting them back into the original equation:

For x = -2:
(-2)^2 + 5(-2) + 6 = 4 - 10 + 6 = 0 ✓

For x = -3:
(-3)^2 + 5(-3) + 6 = 9 - 15 + 6 = 0 ✓

Both solutions check
Example 2

1
Write a Python function to check if a string is a palindrome

streamlit-06-multiagent-python

Example 3

1
Translate "Hello, how are you?" to Spanish

streamlit-07-multiagent-translator

Conclusion
Congratulations! You now have a running multi-agent Streamlit application!

Step 3 - Adding Knowledge Base to Multi-Agent with Strands
[Optional] Use Q Developer to update the Streamlit App
Open Q Developer in the left side panel and type:

1
2
3
In the Streamlit application `app.py`:
- add the `determine_action()` subroutine from `strands_knowledgebase_agent_example/knowledge_base_agent.py` and expand its capability to route requests to the teacher agent depending on the query.
- requests not routed to the teacher agent should go to the knowledge base agent, that is implemented in the `run_kb_agent()` subroutine.

When Q Developer is complete, you will see a list of changes made to app.py (note that there may be some variability in the code generation. The screenshots below show the outcome from the first attempt, during the preparation of this workshop):

qdeveloper-addkb-00-list-of-changes

Clicking through each of these 5 changes shows the changes that have been made, as shown in the subsequent screenshots. You have the option to click the Undo button to revert any of the changes.

Change 1: Adding the necessary imports for the knowledge base agent functionality

qdeveloper-addkb-01-imports

Change 2: Adding the necessary system prompts for determining actions and handling knowledge base operations

Observe how the system prompts have been modified, with multiple examples, in order to ensure that requests will be correctly routed.

qdeveloper-addkb-02-prompts

Change 3: Updating the app description to include knowledge base functionality

qdeveloper-addkb-03-app-description

Change 4: Adding the knowledge base agent initialization and implementing the determine_action() and run_kb_agent() functions

qdeveloper-addkb-04-add-kb-agent

Change 5: Updating the main application logic to route queries to either the teacher agent or knowledge base agent based on the determine_action() function

This last fix implements the new routing functionality.

qdeveloper-addkb-05-update-routine

Overwrite app.py with the earlier code generated by Q Developer
The output from the code generated during the process of creating this workshop has been saved as app_kb.py. There may be some variability between this version and the current app.py. If you prefer to use this version, you may copy the file over to replace app.py.

1
2
cd ~/workshop/
cp app_kb.py app.py

[Optional] Run the Streamlit app and test the same prompts again
Type the following to run the new Streamlit app, and click the Open in Browser button when it appears.

1
streamlit run app.py

We can test the earlier prompts again, to make sure that they still work (avoid entering any sensitive or PII data).

Example 1

1
Solve the quadratic equation x^2 + 5x + 6 = 0

streamlit-08-math

Example 2

1
Write a Python function to check if a string is a palindrome

streamlit-09-python

Example 3

1
Translate "Hello, how are you?" to Spanish


Conclusion
Congratulations! You now have a running multi-agent Streamlit application with Bedrock Knowledge Base functionality!

Step 4 - Adding Memory to Multi-Agent with Strands
[Optional] Use Q Developer to add the memory agent
Open Q Developer in the left side panel and type:

1
2
3
4
In the Streamlit application `app.py`:
- add the capabilities from `strands_memory_agent_example/mem0_agent.py`.
- users should be able to select between the current Bedrock Knowledge Base agent, and this new memory agent (with Open Search backend)
- if the `OPENSEARCH_HOST` variable is not defined, then disable the Open Search backend option.

When Q Developer is complete, you will see a list of changes made to app.py:

qdeveloper-addmemory-00-list-of-changes

Clicking through each of these 5 changes shows the changes that have been made, as shown in the subsequent screenshots. You have the option to click the Undo button to revert any of the changes.

Change 1: Adding the import for os and mem0_memory, and fixing the BedrockModel import

qdeveloper-addmemory-01-imports

Change 2: Adding the OpenSearch availability check and agent selection dropdown in the sidebar

qdeveloper-addmemory-02-agent-selection

Change 3: Adding the memory agent initialization function with OpenSearch backend

qdeveloper-addmemory-03-mem0-agent

Change 4: Adding the function to run the memory agent with OpenSearch backend

qdeveloper-addmemory-04-mem0-agent

Change 5: Completing the app.py file with the logic to handle different agent types and display responses

qdeveloper-addmemory-05-integrate-mem0-agent

[Optional] Use Q Developer to implement Side Panel
Open Q Developer in the left side panel and type:

1
2
3
In the Streamlit application `app.py`:
- add the ability to select from a list of Bedrock model IDs: us.amazon.nova-pro-v1:0, us.amazon.nova-lite-v1:0, us.amazon.nova-micro-v1:0, anthropic.claude-3-5-haiku-20241022-v1:0, anthropic.claude-3-7-sonnet-20250219-v1:0, and anthropic.claude-sonnet-4-20250514-v1:0
- for the teacher agent, users should be able to toggle on and off any of the teacher agents (math agent, language assistent, and computer science assistant, etc)

List of changes

Change 1: Adding model selection dropdown and teacher agent toggle checkboxes in the sidebar

Init side bar

Change 2: Updating the teacher agent initialization to use the selected model and only include the toggled teacher agents


Change 3: Updating the knowledge base agent to use the selected models


Change 4: Updating the memory agent to use the selected model


Overwrite app.py with earlier code generated by Q Developer
The output from the code generated during the process of creating this workshop has been saved as app_kb_mem.py. There may be some variability between this version and the current app.py. If you prefer to use this version, you may copy the file over to replace app.py.

1
2
cd ~/workshop/
cp app_kb_mem.py app.py

Run the Streamlit app
We will need to make sure that the environment variable $OPENSEARCH_HOST is set properly, prior to running the Streamlit App. Let's make sure it's saved in ~/.bashrc, and we will load this value into our environment.

1
2
3
tail -3 ~/.bashrc
source ~/.bashrc
echo "OPENSEARCH_HOST=\"$OPENSEARCH_HOST\""

Next, run the new Streamlit app, and click the Open in Browser button when it appears.

1
2
cd ~/workshop/
streamlit run app.py

Final App
You may test the app by entering something similar to the following:

1
Solve the equation 2x^2 - 5x - 3

Your final app should look something like the following:


Conclusion
Congratulations! You now have a running multi-agent Streamlit application with Bedrock Knowledge Base and Open Search functionality!

Deploy the Streamlit Application
1. Prepare the Streamlit Application
Clone the repository

1
2
3
4
cd ~/workshop/
git clone https://github.com/aws-samples/deploy-streamlit-app.git
FOLDER="deploy-streamlit-app/docker_app"
cd $FOLDER

Prepare requirements.txt

1
2
3
4
5
6
7
8
9
10
11
12
13
cat << EOF > requirements.txt
boto3
mcp[cli]
nova-act
opensearch-py
pandas
retrying
strands-agents 
strands-agents-tools[mem0_memory]
streamlit
streamlit-cognito-auth
ddgs
EOF

1
2
source ~/.venv/bin/activate
uv pip install -r requirements.txt

Copy the Streamlit app

1
2
3
4
5
mv app.py app.py.bak
cp ~/workshop/streamlit_app.py ./app.py
mkdir -p strands_multi_agent_example/ && cd strands_multi_agent_example/
cp -Rv ~/workshop/strands_multi_agent_example/*.py .
cd ..

Update the region in config_file.py to the workshop region. For example, if the region is us-west-2, you may use the following command to do an in-place text replacement of the region from us-east-1 to us-west-2.

1
sed -i "s/us-east-1/us-west-2/g" config_file.py

Update the CDK stack

1
cd ~/workshop/deploy-streamlit-app/cdk/

Look for the bedrock_policy line in cdk_stack.py, and edit it as follows:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
        bedrock_policy = iam.Policy(
            self,
            f"{prefix}BedrockPolicy",
            statements=[
                iam.PolicyStatement(
                    actions=[
                        "bedrock:InvokeModel",
                        "bedrock:InvokeModelWithResponseStream",
                        "bedrock:RetrieveAndGenerate",
                        "bedrock:Retrieve",
                        "ssm:GetParameter"
                    ],
                    resources=["*"]
                )
            ]
        )

Additional changes required for ARM platforms

The first line in the Dockerfile needs to be changed from FROM --platform=linux/amd64 python:3.12 to FROM --platform=linux/arm64 python:3.12. Running the following command checks whether the platform is ARM, and if so, performs an in-place replacement of the text in the Dockerfile (using the Linux sed command). You will not need to run this if you are on an x86 platform.

1
2
3
4
ARCH=$(uname -m)
if [ "$ARCH" = "aarch64" ]; then
sed -i 's/platform=linux\/amd64/platform=linux\/arm64/g' ~/workshop/deploy-streamlit-app/docker_app/Dockerfile
fi

To deploy the container image on ECS/Fargate with ARM architecture, you will also need to update the fargate_task_definition line in cdk_stack.py (in folder ~/workshop/deploy-streamlit-app/cdk/). Add the runtime_platform=ecs.RuntimePlatform(...) section, so that the Fargate task definition looks like the following:

1
2
3
4
5
6
7
8
9
10
        fargate_task_definition = ecs.FargateTaskDefinition(
            self,
            f"{prefix}WebappTaskDef",
            memory_limit_mib=512,
            cpu=256,
            runtime_platform=ecs.RuntimePlatform(
                cpu_architecture=ecs.CpuArchitecture.ARM64,
                operating_system_family=ecs.OperatingSystemFamily.LINUX
            )
        )

2. Setup and Bootstrap CDK
1
2
3
cd ~/workshop/deploy-streamlit-app/
uv pip install -r requirements.txt
cdk --version

Example response:

2.1017.1 (build 60506e5)
Run CDK Bootstrap (this may take perhaps 1-2 minutes)

1
2
3
export AWS_ACCOUNT_ID=$(aws sts get-caller-identity --query "Account" --output text)
echo "Running cdk bootstrap aws://${AWS_ACCOUNT_ID}/${AWS_REGION}"
cdk bootstrap aws://${AWS_ACCOUNT_ID}/${AWS_REGION}

3. Deploy the application with CDK
Run cdk synth

1
cdk synth

Run the following command to deploy the application

1
cdk deploy

If you are asked the question Do you wish to deploy these changes (y/n)?, type y.

The deployment process will take perhaps 10 minutes or so. When the deployment is complete, you should see something like the following:

CDK Deployment Complete

Take note of the CloudFrontDistributionURL above (d2c6wliwqw7xla.cloudfront.net in the example above) and the Cognito Pool Id (us-west-2_FeRHRaY5X).

4. Create an Amazon Cognito User
Go to Amazon Cognito, and click on User pools in the left side bar.

Cognito User Pools

In the left side bar, under User management, click on Users

Cognito User Dashboard

Click Create user. Choose Don't send an invitation. Fill in a user name and set a password. The email address is optional.

Cognito Create User

Click Create user

5. Go to the Streamlit App
Go to the CloudFront distribution URL that you saved earlier. If you are not able to locate it, you can also go to CloudFormation and look for the Streamlit stack. You can find the CloudFront distribution URL in the Outputs tab, as follows:

CloudFormation Outputs

Login to the application:

Streamlit Login Page

Change your password:

Streamlit Reset Password

Congratulations! You have successfully added Cognito authentication and deployed your Streamlit application using CDK

Streamlit App

Deploy the Streamlit Application
1. Prepare the Streamlit Application
Clone the repository

1
2
3
4
cd ~/workshop/
git clone https://github.com/aws-samples/deploy-streamlit-app.git
FOLDER="deploy-streamlit-app/docker_app"
cd $FOLDER

Prepare requirements.txt

1
2
3
4
5
6
7
8
9
10
11
12
13
cat << EOF > requirements.txt
boto3
mcp[cli]
nova-act
opensearch-py
pandas
retrying
strands-agents 
strands-agents-tools[mem0_memory]
streamlit
streamlit-cognito-auth
ddgs
EOF

1
2
source ~/.venv/bin/activate
uv pip install -r requirements.txt

Copy the Streamlit app

1
2
3
4
5
mv app.py app.py.bak
cp ~/workshop/streamlit_app.py ./app.py
mkdir -p strands_multi_agent_example/ && cd strands_multi_agent_example/
cp -Rv ~/workshop/strands_multi_agent_example/*.py .
cd ..

Update the region in config_file.py to the workshop region. For example, if the region is us-west-2, you may use the following command to do an in-place text replacement of the region from us-east-1 to us-west-2.

1
sed -i "s/us-east-1/us-west-2/g" config_file.py

Update the CDK stack

1
cd ~/workshop/deploy-streamlit-app/cdk/

Look for the bedrock_policy line in cdk_stack.py, and edit it as follows:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
        bedrock_policy = iam.Policy(
            self,
            f"{prefix}BedrockPolicy",
            statements=[
                iam.PolicyStatement(
                    actions=[
                        "bedrock:InvokeModel",
                        "bedrock:InvokeModelWithResponseStream",
                        "bedrock:RetrieveAndGenerate",
                        "bedrock:Retrieve",
                        "ssm:GetParameter"
                    ],
                    resources=["*"]
                )
            ]
        )

Additional changes required for ARM platforms

The first line in the Dockerfile needs to be changed from FROM --platform=linux/amd64 python:3.12 to FROM --platform=linux/arm64 python:3.12. Running the following command checks whether the platform is ARM, and if so, performs an in-place replacement of the text in the Dockerfile (using the Linux sed command). You will not need to run this if you are on an x86 platform.

1
2
3
4
ARCH=$(uname -m)
if [ "$ARCH" = "aarch64" ]; then
sed -i 's/platform=linux\/amd64/platform=linux\/arm64/g' ~/workshop/deploy-streamlit-app/docker_app/Dockerfile
fi

To deploy the container image on ECS/Fargate with ARM architecture, you will also need to update the fargate_task_definition line in cdk_stack.py (in folder ~/workshop/deploy-streamlit-app/cdk/). Add the runtime_platform=ecs.RuntimePlatform(...) section, so that the Fargate task definition looks like the following:

1
2
3
4
5
6
7
8
9
10
        fargate_task_definition = ecs.FargateTaskDefinition(
            self,
            f"{prefix}WebappTaskDef",
            memory_limit_mib=512,
            cpu=256,
            runtime_platform=ecs.RuntimePlatform(
                cpu_architecture=ecs.CpuArchitecture.ARM64,
                operating_system_family=ecs.OperatingSystemFamily.LINUX
            )
        )

2. Setup and Bootstrap CDK
1
2
3
cd ~/workshop/deploy-streamlit-app/
uv pip install -r requirements.txt
cdk --version

Example response:

2.1017.1 (build 60506e5)
Run CDK Bootstrap (this may take perhaps 1-2 minutes)

1
2
3
export AWS_ACCOUNT_ID=$(aws sts get-caller-identity --query "Account" --output text)
echo "Running cdk bootstrap aws://${AWS_ACCOUNT_ID}/${AWS_REGION}"
cdk bootstrap aws://${AWS_ACCOUNT_ID}/${AWS_REGION}

3. Deploy the application with CDK
Run cdk synth

1
cdk synth

Run the following command to deploy the application

1
cdk deploy

If you are asked the question Do you wish to deploy these changes (y/n)?, type y.

The deployment process will take perhaps 10 minutes or so. When the deployment is complete, you should see something like the following:

CDK Deployment Complete

Take note of the CloudFrontDistributionURL above (d2c6wliwqw7xla.cloudfront.net in the example above) and the Cognito Pool Id (us-west-2_FeRHRaY5X).

4. Create an Amazon Cognito User
Go to Amazon Cognito, and click on User pools in the left side bar.

Cognito User Pools

In the left side bar, under User management, click on Users

Cognito User Dashboard

Click Create user. Choose Don't send an invitation. Fill in a user name and set a password. The email address is optional.

Cognito Create User

Click Create user

5. Go to the Streamlit App
Go to the CloudFront distribution URL that you saved earlier. If you are not able to locate it, you can also go to CloudFormation and look for the Streamlit stack. You can find the CloudFront distribution URL in the Outputs tab, as follows:

CloudFormation Outputs

Login to the application:

Streamlit Login Page

Change your password:

Streamlit Reset Password

Congratulations! You have successfully added Cognito authentication and deployed your Streamlit application using CDK

Streamlit App

Module 8: Amazon Bedrock AgentCore
Welcome to the comprehensive workshop on Amazon Bedrock AgentCore , a fully managed service that enables you to deploy and operate highly capable AI agents securely at scale. AgentCore provides purpose-built infrastructure for dynamic agent workloads, powerful tools to enhance agent capabilities, and essential enterprise controls for production deployment.

AgentCore's modular architecture is designed to work seamlessly together or as individual components, providing the flexibility to integrate with any open-source frameworks while maintaining enterprise-grade security and observability.

AgentCore Overview

Amazon Bedrock AgentCore includes the following modular Services that you can use together or independently:

Amazon Bedrock AgentCore Runtime
Amazon Bedrock AgentCore Identity
Amazon Bedrock AgentCore Gateway
Amazon Bedrock AgentCore Memory
Amazon Bedrock AgentCore Observability
Amazon Bedrock AgentCore Code Interpreter
Amazon Bedrock AgentCore Browser
Reference: Amazon Bedrock AgentCore Documentation 

8.1 Amazon Bedrock AgentCore Fundamentals
Welcome to the Amazon Bedrock AgentCore Workshop! This workshop will give you an overview of AgentCore, with in-depth explanations alongside code samples in Jupyter notebooks.

The need to innovate quickly has become paramount. Within just a few years, we've seen the evolution of foundation models (FMs) and generative AI workflows - from being used primarily to generate a response to a user’s prompt (like answering a question or summarizing a document), to powering robust AI agents solutions that leverage FMs to reason, plan, act, learn, adapt, and orchestrate multi-agent collaboration in pursuit of user-deﬁned goals with little human oversight. This new wave of agentic AI is further propelled by the emergence of standardized protocols such as Model Context Protocol (MCP)  and Agent2Agent (A2A)  that simplify and standardize how agents connect with tools and systems.

Building AI agents that can reliably perform complex tasks has become increasingly accessible thanks to open source frameworks like Strands Agents , LangGraph , CrewAI , and LlamaIndex  . However, moving from a promising proof-of-concept to a production-ready agent that can scale to thousands of users presents significant challenges. Instead of being able to focus on the core features of the agent, developers and AI engineers have to spend months building foundational infrastructure for session management, identity controls, memory systems, and observability - while at the same time supporting security and compliance.

Here's where AgentCore comes in. Amazon Bedrock AgentCore  is an enterprise-grade suite of services designed to accelerate moving your agentic applications from POC to Production. AgentCore enables you to deploy and operate agents securely, at scale. AgentCore services can be used together or independently and work with any framework including Strands Agents, LangGraph, CrewAI, and LlamaIndex, as well as any foundation model in or outside of Amazon Bedrock, giving you the ultimate flexibility. It serves developers and enterprises who need 1) robust, secure, and scalable infrastructure to support dynamic execution paths at runtime, 2) controls to monitor behavior, 3) powerful tools to enhance agents, and 4) the flexibility to adapt as the landscape evolves. Amazon Bedrock AgentCore services are composable and work with popular open-source frameworks and any model, so you don’t have to choose between open-source flexibility and enterprise-grade security and reliability. AgentCore Runtime offers:

Amazon Bedrock AgentCore eliminates the undifferentiated heavy lifting of building specialized agent infrastructure, and was designed to give you:

Faster time to value: Accelerate from prototype to production with fully-managed services that eliminate infrastructure complexity, so you can bring groundbreaking agentic solutions to market faster.
Flexibility and choice: Build agents your way using any framework, model, or tool — while maintaining complete control over how your agents operate and integrate with existing systems.
Security and trust: Deploy with confidence using enterprise-grade security, complete session isolation, and comprehensive controls that help your agents operate reliably and securely at scale.
Key Components of Amazon Bedrock AgentCore
Amazon Bedrock AgentCore includes the following modular services that you can use together or independently:

Agentcore Fundamentals

Amazon Bedrock AgentCore Runtime
AgentCore Runtime is a secure, serverless runtime purpose-built for deploying and scaling dynamic AI agents and tools using any open-source framework (including Strands Agents, LangGraph, and CrewAI), any protocol, and any model. Runtime was built to work for agentic workloads with industry-leading extended runtime support, fast cold starts, true session isolation, built-in identity, and support for multi-modal payloads. Developers can focus on innovation while Amazon Bedrock AgentCore Runtime handles infrastructure and security—accelerating time-to-market.

Amazon Bedrock AgentCore Identity
AgentCore Identity provides a secure, scalable agent identity and access management capability accelerating AI agent development. It is compatible with existing identity providers, eliminating needs for user migration or rebuilding authentication flows. AgentCore Identity's helps to minimize consent fatigue with a secure token vault and allows you to build streamlined AI agent experiences. Just-enough access and secure permission delegation allow agents to securely access AWS resources and third-party tools and services.

Amazon Bedrock AgentCore Gateway
AgentCore Gateway provides a secure way for agents to discover and use tools along with easy transformation of APIs, Lambda functions, and existing services into agent-compatible tools. Gateway eliminates weeks of custom code development, infrastructure provisioning, and security implementation so developers can focus on building innovative agent applications. AgentCore Gateway's powerful built-in semantic search capability helps agents effectively search tools to find the most appropriate ones for specific contexts, allowing agents to take advantage of thousands of tools while minimizing prompt size and reducing latency.

Amazon Bedrock AgentCore Code Interpreter
The AgentCore Code Interpreter tool enables agents to securely execute code in isolated sandbox environments. It offers advanced configuration support and seamless integration with popular frameworks. Developers can build powerful agents for complex workflows and data analysis while meeting enterprise security requirements.

Amazon Bedrock AgentCore Browser
The AgentCore Browser tool provides a fast, secure, cloud-based browser runtime to enable AI agents to interact with websites at scale. It provides enterprise-grade security, comprehensive observability features, and automatically scales— all without infrastructure management overhead.

Amazon Bedrock AgentCore Memory
AgentCore Memory makes it easy for developers to build context aware agents by eliminating complex memory infrastructure management while providing full control over what the AI agent remembers. Memory provides industry-leading accuracy along with support for both short-term memory for multi-turn conversations and long-term memory that can be shared across agents and sessions.

Amazon Bedrock AgentCore Observability
AgentCore Observability helps developers trace, debug, and monitor agent performance in production through unified operational dashboards. With support for OpenTelemetry compatible telemetry and detailed visualizations of each step of the agent workflow, AgentCore enables developers to easily gain visibility into agent behavior and maintain quality standards at scale.

Let's dive into them one-by-one!

Resources
Introducing Amazon Bedrock AgentCore: Securely deploy and operate AI agents at any scale (preview) 
Amazon Bedrock AgentCore Developer Guide 
Amazon Bedrock AgentCore Starter Toolkit 
Amazon Bedrock AgentCore (Preview) FAQs 
8.2 Amazon Bedrock AgentCore Runtime
Amazon Bedrock AgentCore Runtime provides a secure, serverless and purpose-built hosting environment for deploying and running AI agents or tools, shortening the time to value from experiments to production-grade agents.

How it works
AgentCore Runtime

Container ingestion: The developer pushes an ARM64 container image to Amazon ECR. Runtime stores the image digest alongside metadata describing required ports (8080 for HTTP, 8000 for MCP).

Runtime creation: CreateAgentRuntime registers the image, assigns a workload identity, and stamps Version 1. A DEFAULT endpoint is generated that targets V1.

Session bootstrap: On the first InvokeAgentRuntime with a new runtimeSessionId, the control plane provisions an isolated execution environment. The bootstrap time is minimized through cached image digests and lazy layer extraction.

Invocation handling: The request payload (up to 100 MB) is streamed into the container. The agent produces either a JSON document or a Server‑Sent Events stream. Runtime relays those bytes directly to the caller while simultaneously capturing observability data.

Health negotiation: AgentCore Runtime polls the /ping route. The agent replies with Healthy when idle or HealthyBusy while processing background tasks—allowing long‑running workflows to persist across await points.

Credential exchange: If the agent calls an external tool requiring OAuth, it exchanges its workload token for a scoped access token via AgentCore Identity. Tokens are short‑lived and bound to the invoking user where applicable.

Termination: After 15 minutes of inactivity or eight hours total runtime, the environment is terminated. Memory pages are wiped, temporary storage is discarded, and the session ID no longer maps to that environment.

Version update: Publishing a new image triggers Version n+1. Updating an endpoint redirects new sessions to the new version while existing sessions on the previous version continue until they naturally terminate.

Learn more about how AgentCore Runtime works 

8.2 Amazon Bedrock AgentCore Runtime
Amazon Bedrock AgentCore Runtime provides a secure, serverless and purpose-built hosting environment for deploying and running AI agents or tools, shortening the time to value from experiments to production-grade agents.

How it works
AgentCore Runtime

Container ingestion: The developer pushes an ARM64 container image to Amazon ECR. Runtime stores the image digest alongside metadata describing required ports (8080 for HTTP, 8000 for MCP).

Runtime creation: CreateAgentRuntime registers the image, assigns a workload identity, and stamps Version 1. A DEFAULT endpoint is generated that targets V1.

Session bootstrap: On the first InvokeAgentRuntime with a new runtimeSessionId, the control plane provisions an isolated execution environment. The bootstrap time is minimized through cached image digests and lazy layer extraction.

Invocation handling: The request payload (up to 100 MB) is streamed into the container. The agent produces either a JSON document or a Server‑Sent Events stream. Runtime relays those bytes directly to the caller while simultaneously capturing observability data.

Health negotiation: AgentCore Runtime polls the /ping route. The agent replies with Healthy when idle or HealthyBusy while processing background tasks—allowing long‑running workflows to persist across await points.

Credential exchange: If the agent calls an external tool requiring OAuth, it exchanges its workload token for a scoped access token via AgentCore Identity. Tokens are short‑lived and bound to the invoking user where applicable.

Termination: After 15 minutes of inactivity or eight hours total runtime, the environment is terminated. Memory pages are wiped, temporary storage is discarded, and the session ID no longer maps to that environment.

Version update: Publishing a new image triggers Version n+1. Updating an endpoint redirects new sessions to the new version while existing sessions on the previous version continue until they naturally terminate.

Learn more about how AgentCore Runtime works 

8.2.1 Amazon Bedrock AgentCore Runtime - Hosting Agent
AgentCore Runtime is a secure, serverless runtime purpose-built for deploying and scaling dynamic AI agents and tools using any open-source framework including LangGraph, CrewAI, and Strands Agents, any protocol, and any model. Runtime was built to work for agentic workloads with industry-leading extended runtime support, fast cold starts, true session isolation, built-in identity, and support for multi-modal payloads. Developers can focus on innovation while Amazon Bedrock AgentCore Runtime handles infrastructure and security—accelerating time-to-market

Reference: Amazon Bedrock AgentCore Documentation 

AgentCore Runtime offers:

Framework agnostic (use frameworks like LangGraph, Strands, and CrewAI)
Model flexibility (use models offered by Amazon Bedrock, Anthropic Claude, Google Gemini, and OpenAI)
Protocol support (communicate with other agents and tools via Model Context Protocol)
Extended execution time (supports real-time interactions and long-running workloads up to 8 hours)
Enhanced payload handling (process 100MB payloads in multiple modalities - text, images, audio, and video)
Session isolation (each user session runs in a dedicated microVM with isolated CPU, memory, and filesystem resources)
Consumption-based pricing model
Built-in authentication (integration with corporate identity providers such as Okta, Microsoft Entra ID, or Amazon Cognito)
Agent-specific observability (specialized built-in tracing that captures agent reasoning steps, tool invocations, and model interactions)
Unified set of agent-specific capabilities (single, comprehensive SDK that provides streamlined access to the complete Amazon Bedrock AgentCore capabilities including Memory, Tools, and Gateway)
1. Code changes required for deployment to AgentCore
To convert an existing agent function into a Amazon Bedrock AgentCore-compatible service, you will need to make the following changes (on lines 1, 5, 7, and 14 below) to your code:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
from bedrock_agentcore.runtime import BedrockAgentCoreApp
.
.
.
app = BedrockAgentCoreApp()

@app.entrypoint
def invoke_agent(payload):
    user_input = payload.get("prompt")
    response = agent(user_input)
    return response

if __name__ == "__main__":
    app.run()

In the above code, we have:

imported BedrockAgentCoreApp
added app = BedrockAgentCoreApp()
prefixed the agent function with @app.entrypoint
invoked app.run()
If we apply these changes to weather_forecaster.py from Module 1, we will see the following modifications as shown in the screenshot below.

Agent Core Code Changes

2. Environment setup for AgentCore
Amazon Bedrock AgentCore requires additional Python libraries, which we will install here. Run the following in the code-server terminal window:

1
2
3
4
5
6
7
8
9
10
cd ~/workshop/agentcore/runtime/
cat << EOF > requirements.txt
strands-agents
strands-agents-tools
uv
boto3
bedrock-agentcore
bedrock-agentcore-starter-toolkit
EOF
uv pip install -r requirements.txt

3. Deploying a Python script to the Bedrock AgentCore runtime
3.1 [Optional] Test the agent locally
Run the following in a terminal window

1
uv run weather_agentcore.py --port 8082

Open a separate terminal window and run the following

1
2
3
curl -X POST http://localhost:8082/invocations \
-H "Content-Type: application/json" \
-d '{"prompt": "What is the weather like in New York?"}'

Sample output (middle portion truncated):

data: {"init_event_loop": true}

data: {"start": true}

data: {"start_event_loop": true}
.
.
.
data: "{'result': AgentResult(stop_reason='end_turn', message={'role': 'assistant', 'content': [{'text': \"## 🌤️ Weather Forecast for New York City\\n\\n**Current Conditions (Overnight Sunday into Monday):**\\n- **Temperature**: Currently around 71°F, rising to 73°F overnight\\n- **Conditions**: Mostly clear skies\\n- **Wind**: Southwest at 7 mph\\n- **Precipitation**: 0% chance of rain\\n\\n**Today (Monday, August 11th):**\\n- **High**: 84°F (cooling to around 82°F in the afternoon)\\n- **Conditions**: ☀️ **Sunny**\\n- **Wind**: Southwest 5-10 mph\\n- **Precipitation**: No rain expected\\n\\n**This Week's Outlook:**\\n\\n**Tuesday**: Sunny and warmer with a high of 86°F, overnight low of 75°F\\n\\n**Wednesday**: Partly sunny with a **50% chance of showers and thunderstorms** developing in the afternoon. High of 86°F, becoming mostly cloudy overnight with continued storm chances.\\n\\n**Thursday**: Partly sunny with a **30% chance of rain showers** early, then possible thunderstorms. High of 85°F.\\n\\n**Weekend**: Beautiful weather returns! Sunny skies with highs in the low 80s (Friday-Saturday) climbing back to 86°F on Sunday.\\n\\n**Summary**: Excellent weather to start the week with sunshine and comfortable temperatures! Mid-week brings a chance for some much-needed rain and storms, but the weekend looks perfect for outdoor activities. Temperatures will remain pleasant in the 80s throughout the week.\\n\\nThe forecast is provided by the National Weather Service and covers the Manhattan area of New York City.\"}]}, metrics=EventLoopMetrics(cycle_count=3, tool_metrics={'http_request': ToolMetrics(tool={'toolUseId': 'tooluse_RQRhCCRrSbm2TeUjlsLPdQ', 'name': 'http_request', 'input': {'method': 'GET', 'url': 'https://api.weather.gov/gridpoints/OKX/33,35/forecast'}}, call_count=2, success_count=2, error_count=0, total_time=0.17731499671936035)}, cycle_durations=[9.282775163650513], traces=[<strands.telemetry.metrics.Trace object at 0xe82b218ab290>, <strands.telemetry.metrics.Trace object at 0xe82b218aa4b0>, <strands.telemetry.metrics.Trace object at 0xe82b218aa8a0>], accumulated_usage={'inputTokens': 11050, 'outputTokens': 609, 'totalTokens': 11659}, accumulated_metrics={'latencyMs': 13711}), state={})}"
You can also curl the /ping endpoint, which is implemented for health checks:

1
curl http://localhost:8082/ping

Press Ctrl^C to stop. Sample output:

{“status”:“Healthy”,“time_of_last_update”:1755787369}
In the first terminal, press Ctrl^C as well, to stop the locally-deployed agent.

3.2 Deploy the agent remotely
The following subroutine deploy_to_agentcore.py handles the deployment of a Python script to the AgentCore runtime.

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
def deploy_agentcore(agent_name: str, entry_point: str, requirements_file: str = 'requirements.txt', local_build: bool = False):
    """
    Deploy an Amazon Bedrock Agent Core runtime with the specified configuration.

    Args:
        agent_name (str): Name of the agent to deploy
        entry_point (str): Path to the entry point file for the agent
        requirements_file (str, optional): Path to requirements.txt file. Defaults to 'requirements.txt'
        local_build (bool, optional): Whether to build the container locally. Defaults to False
    .
    .
    .
    """
    response = agentcore_runtime.configure(
        entrypoint=entry_point,
        auto_create_execution_role=True,
        auto_create_ecr=True,
        requirements_file=requirements_file,
        region=region,
        agent_name=agent_name
    )
    launch_result = agentcore_runtime.launch(
        local_build=local_build
    )

In a terminal window run the following to deploy the weather agent script to the Bedrock AgentCore runtime:

1
2
3
4
5
cd ~/workshop/agentcore/runtime/
uv run ~/workshop/agentcore/deploy_to_agentcore.py \
    --agent_name weather_agent \
    --local_build \
    --entry_point weather_agentcore.py

The --local_build flag has been added to build the container image locally on the arm64 vs-code-server instance. This allows the build process to complete much more quickly (typically in less than a minute). However, this isn't possible on an x86 instance, in which case the default option (CodeBuild) should be used. With CodeBuild, it will take a few minutes to deploy the AgentCore Runtime.

In a successful deployment, you will see output similar to the following (middle portion has been truncated):

Entrypoint parsed: file=/home/ubuntu/workshop/agentcore/weather_agentcore.py, bedrock_agentcore_name=weather_agentcore
Configuring BedrockAgentCore agent: weather_agent1
Generated Dockerfile: /home/ubuntu/workshop/agentcore/Dockerfile
Generated .dockerignore: /home/ubuntu/workshop/agentcore/.dockerignore
.
.
.
Deployed to cloud: arn:aws:bedrock-agentcore:us-west-2:<account-id>:runtime/weather_agent-p6BtjX2eAO
ECR image: <account-id>.dkr.ecr.us-west-2.amazonaws.com/bedrock-agentcore-weather_agent
🔍 Agent logs available at:
   /aws/bedrock-agentcore/runtimes/weather_agent-p6BtjX2eAO-DEFAULT
   /aws/bedrock-agentcore/runtimes/weather_agent-p6BtjX2eAO-DEFAULT/runtime-logs
💡 Tail logs with: aws logs tail /aws/bedrock-agentcore/runtimes/weather_agent-p6BtjX2eAO-DEFAULT --follow
💡 Or view recent logs: aws logs tail /aws/bedrock-agentcore/runtimes/weather_agent-p6BtjX2eAO-DEFAULT --since 1h
You may wish to take note of the ARN listed above (arn:aws:bedrock-agentcore:us-west-2:<account-id>:runtime/weather_agent-p6BtjX2eAO).

4. Invoking Bedrock AgentCore runtime
Run the following to invoke the AgentCore runtime

1
uv run invoke_agent.py --prompt "What is the weather like in New York?"

Sample output:

Using region: us-west-2
--------------------------------------------------------------------------------
Agent Name: weather_agent
ARN: arn:aws:bedrock-agentcore:us-west-2:<account-id>:runtime/weather_agent-eQP730Bst9
--------------------------------------------------------------------------------
Invoking agent with payload:
{"prompt": "What is the weather like in New York?"}

I'll help you get the weather forecast for New York. Let me start by getting the location information from the National Weather Service API, and then retrieve the current weather forecast.Great! I've got the location information for New York City. Now let me get the current weather forecast using the forecast URL.# Weather Forecast for New York City 🌤️

Based on the National Weather Service data, here's the current weather outlook for New York City:

## **Current Conditions & Today (Monday)**
- **Today**: Sunny and pleasant with a high of **84°F** 
- **Tonight**: Mostly clear with a low around **72°F**
- **Wind**: Southwest winds 5-10 mph
- **Precipitation**: 0% chance of rain

## **Extended Forecast**

### **Tuesday**
- ☀️ **Sunny** with a high near **86°F**
- Mostly clear tonight, low around **75°F**
- Very slight chance of precipitation (3%)

### **Wednesday**
- ⛈️ **Weather changes** - Chance of rain showers and thunderstorms
- High near **86°F**, but **50% chance of precipitation**
- Showers possible between 8am-2pm, then thunderstorms later
- Overnight low around **77°F** with continued storm chances

### **Thursday**
- 🌦️ **Partly sunny** with chance of morning showers
- High near **85°F**, 30% chance of precipitation
- Conditions improving with low around **73°F**

### **Weekend**
- **Friday-Sunday**: **Sunny and pleasant** 
- Highs in the low-to-mid **80s°F**
- Lows around **72°F**
- Minimal precipitation expected

## **Summary**
New York is experiencing beautiful summer weather with sunny skies and comfortable temperatures in the 80s. The only weather concern is Wednesday, when there's a 50% chance of showers and thunderstorms. Otherwise, it's excellent weather for outdoor activities through the week and weekend!

The forecast is provided by the National Weather Service office in Upton, NY (OKX), covering the New York City area.
5. [Optional] Notes on Response Streaming
Note that in weather_agentcore.py, we can switch between streaming outputs and non-streaming outputs in the invoke_agent() subroutine:

Without Streaming

1
2
3
4
5
@app.entrypoint
async def invoke_agent(payload):
    prompt = payload.get("prompt")
    response = weather_agent(user_input)
    return response

With Streaming

1
2
3
4
5
6
7
@app.entrypoint
async def invoke_agent(payload):
    prompt = payload.get("prompt")
    stream = weather_agent.stream_async(prompt)
    async for event in stream:
        print(event)
        yield (event)

You can read more about Response Streaming here:

Creating an Agent with Response Streaming: https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/response-streaming.html 
Invoking an Agent capable of Response Streaming: https://docs.aws.amazon.com/bedrock-agentcore/latest/devguide/runtime-invoke-agent.html 
6. [Optional] Notes on Docker containers
AgentCore creates a Dockerfile as part of the deployment process. You can view the Dockerfile with the following command (the optional sed command below compresses multiple blank lines into a single blank line for clarity):

1
cat ~/workshop/agentcore/runtime/Dockerfile | sed '/^$/N;/^\n$/D'

Sample Output (extra newlines removed)

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
31
32
33
FROM ghcr.io/astral-sh/uv:python3.12-bookworm-slim
WORKDIR /app

# Configure UV for container environment
ENV UV_SYSTEM_PYTHON=1 UV_COMPILE_BYTECODE=1

COPY requirements.txt requirements.txt
# Install from requirements file
RUN uv pip install -r requirements.txt

RUN uv pip install aws-opentelemetry-distro>=0.10.1

# Set AWS region environment variable

ENV AWS_REGION=us-west-2
ENV AWS_DEFAULT_REGION=us-west-2

# Signal that this is running in Docker for host binding logic
ENV DOCKER_CONTAINER=1

# Create non-root user
RUN useradd -m -u 1000 bedrock_agentcore
USER bedrock_agentcore

EXPOSE 8080
EXPOSE 8000

# Copy entire project (respecting .dockerignore)
COPY . .

# Use the full module path

CMD ["opentelemetry-instrument", "python", "-m", "weather_agentcore"]

This Dockerfile sets up a Python 3.12 container for running a weather agent application. It uses uv (a fast Python package manager) with Python 3.12 on Debian bookworm-slim for system-wide Python installation with bytecode compilation.

Dependencies are based on packages from requirements.txt and AWS OpenTelemetry instrumentation for monitoring/tracing. The AWS region is configured as us-west-2, and the container ports 8080 and 8000 are made accessible. For security, a non-root user, bedrock_agentcore (UID 1000), is used. The runtime project files are copied from the current directory (filtered by .dockerignore), and in the last line, we invoke the weather agent module with OpenTelemetry instrumentation enabled.

7. [Optional] Notes on .bedrock_agentcore.yaml Configuration File
AgentCore also creates a file .bedrock_agentcore.yaml. You can view this file as follows:

1
cat ~/workshop/agentcore/runtime/.bedrock_agentcore.yaml

Sample output (AWS Account ID replaced by <account-id>)

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
24
25
26
27
28
29
30
default_agent: weather_agent
agents:
  weather_agent:
    name: weather_agent
    entrypoint: /home/ubuntu/workshop/agentcore/weather_agentcore.py
    platform: linux/arm64
    container_runtime: docker
    aws:
      execution_role: arn:aws:iam::<account-id>:role/AmazonBedrockAgentCoreSDKRuntime-us-west-2-425e274c35
      execution_role_auto_create: false
      account: '<account-id>'
      region: us-west-2
      ecr_repository: <account-id>.dkr.ecr.us-west-2.amazonaws.com/bedrock-agentcore-weather_agent
      ecr_auto_create: false
      network_configuration:
        network_mode: PUBLIC
      protocol_configuration:
        server_protocol: HTTP
      observability:
        enabled: true
    bedrock_agentcore:
      agent_id: weather_agent-iBFTbS5huv
      agent_arn: arn:aws:bedrock-agentcore:us-west-2:<account-id>:runtime/weather_agent-iBFTbS5huv
      agent_session_id: null
    codebuild:
      project_name: bedrock-agentcore-weather_agent-builder
      execution_role: arn:aws:iam::<account-id>:role/AmazonBedrockAgentCoreSDKCodeBuild-us-west-2-425e274c35
      source_bucket: bedrock-agentcore-codebuild-sources-<account-id>-us-west-2
    authorizer_configuration: null
    oauth_configuration: null

8. Cleanup
Run the following to delete the AgentCore runtimes that were created.

1
2
cd ~/workshop/agentcore/
uv run cleanup_agents.py

You can also run rm ~/workshop/agentcore/runtime/.bedrock_agentcore.yaml if you have no more agents deployed.

8.2.2 Amazon Bedrock AgentCore Runtime II - Hosting MCP Server
This section covers deploying a Model Control Plane (MCP) server in Amazon Bedrock AgentCore Runtime. The code here is based on the following Amazon Bedrock AgentCore Documentation 

1. Introduction
The following files in ~/workshop/agentcore/runtime are used in this module:

agentcore/runtime/
├── mcp_server.py
├── mcp_client_local.py
├── mcp_client_remote.py
└── setup_cognito.sh
The MCP server (mcp_server.py) exposes three tools via the FastMCP  Python library:

add_numbers: Adds two integers together
multiply_numbers: Multiplies two integers together
greet_user: Returns a personalized greeting string
The server runs on port 8000 using streamable HTTP transport

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
21
22
23
from mcp.server.fastmcp import FastMCP
from starlette.responses import JSONResponse

mcp = FastMCP(host="0.0.0.0", stateless_http=True)

@mcp.tool()
def add_numbers(a: int, b: int) -> int:
    """Add two numbers together"""
    return a + b

@mcp.tool()
def multiply_numbers(a: int, b: int) -> int:
    """Multiply two numbers together"""
    return a * b

@mcp.tool()
def greet_user(name: str) -> str:
    """Greet a user by name"""
    return f"Hello, {name}! Nice to meet you."

if __name__ == "__main__":
    # The server runs on port 8000 using streamable HTTP transport
    mcp.run(transport="streamable-http")

The MCP client (mcp_client_local.py) connects to a Model Control Plane (MCP) server running locally on port 8000. It establishes a streamable HTTP connection and initializes a client session. The client then lists all available tools exposed by the MCP server and prints their details - this includes the tool names, descriptions, input/output schemas and other metadata

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
17
18
19
20
import asyncio

from mcp import ClientSession
from mcp.client.streamable_http import streamablehttp_client

async def main():
    mcp_url = "http://localhost:8000/mcp"
    headers = {}

    async with streamablehttp_client(mcp_url, headers, timeout=120, terminate_on_close=False) as (
        read_stream,
        write_stream,
        _,
    ):
        async with ClientSession(read_stream, write_stream) as session:
            await session.initialize()
            tool_result = await session.list_tools()
            print(tool_result)

asyncio.run(main())

2. Run the MCP server and client locally
In a first terminal window, start the MCP server

1
2
cd ~/workshop/agentcore/runtime
uv run mcp_server.py

In a separate terminal window, run the MCP client

1
2
3
source ~/.venv/bin/activate
cd ~/workshop/agentcore/runtime
uv pip install -r requirements.txt

1
uv run mcp_client_local.py

Sample output:

meta=None nextCursor=None tools=[Tool(name='add_numbers', title=None, description='Add two numbers together', inputSchema={'properties': {'a': {'title': 'A', 'type': 'integer'}, 'b': {'title': 'B', 'type': 'integer'}}, 'required': ['a', 'b'], 'title': 'add_numbersArguments', 'type': 'object'}, outputSchema={'properties': {'result': {'title': 'Result', 'type': 'integer'}}, 'required': ['result'], 'title': 'add_numbersOutput', 'type': 'object'}, annotations=None, meta=None), Tool(name='multiply_numbers', title=None, description='Multiply two numbers together', inputSchema={'properties': {'a': {'title': 'A', 'type': 'integer'}, 'b': {'title': 'B', 'type': 'integer'}}, 'required': ['a', 'b'], 'title': 'multiply_numbersArguments', 'type': 'object'}, outputSchema={'properties': {'result': {'title': 'Result', 'type': 'integer'}}, 'required': ['result'], 'title': 'multiply_numbersOutput', 'type': 'object'}, annotations=None, meta=None), Tool(name='greet_user', title=None, description='Greet a user by name', inputSchema={'properties': {'name': {'title': 'Name', 'type': 'string'}}, 'required': ['name'], 'title': 'greet_userArguments', 'type': 'object'}, outputSchema={'properties': {'result': {'title': 'Result', 'type': 'string'}}, 'required': ['result'], 'title': 'greet_userOutput', 'type': 'object'}, annotations=None, meta=None)]
3. Setup Amazon Cognito
First, edit the file setup_cognito.sh and replace TEMP_PASSWORD and PERMANENT_PASSWORD with passwords of your choosing.

Next run the following command in the terminal:

1
bash setup_cognito.sh

You should see something similar to the following (verify that the POOL_ID and DISCOVERY_URL are configured for us-west-2, the deployment region for this lab):

Using region us-west-2
Pool id: us-west-2_sI1JhVabc
Client ID: 24itvh9p3rbv4p7jfkbftfrabc
Cognito user created
Cognito user password set
----- Environment variables saved in .env -----
POOL_ID=us-west-2_sI1JhVabc
DISCOVERY_URL=https://cognito-idp.us-west-2.amazonaws.com/us-west-2_sI1JhVabc/.well-known/openid-configuration
CLIENT_ID=24itvh9p3rbv4p7jfkbftfrabc
You will need these outputs for the next section.

3. Configure Bedrock AgentCore
In this section, we'll demonstrate a different approach to deploy agents. Instead of using Python scripts, we will be using the CLI.

In a terminal window, run the following command to configure AgentCore

1
agentcore configure -e mcp_server.py --protocol MCP

When prompted:

Press Enter to auto-create the Execution role, auto-create the ECR repository, and to use the detected requirements.txt file.
When asked if you would like to configure the OAuth authorizer, type yes.
When asked to enter the OAuth discovery URL, copy and paste the value for DISCOVERY_URL from the earlier output (it should look similar to the following: https://cognito-idp.${REGION}.amazonaws.com/${REGION}_H4LTvbF0I/.well-known/openid-configuration).
When asked to enter the allowed OAuth client IDs, copy and paste the value for CLIENT_ID from the earlier output.
When asked to enter the allowed OAuth audience, press Enter.
Sample output (AWS Account ID replaced with ):

Configuring Bedrock AgentCore...
Entrypoint parsed: file=/home/ubuntu/workshop/agentcore/mcp_server.py, bedrock_agentcore_name=mcp_server
Agent name: mcp_server

🔐 Execution Role
Press **Enter** to auto-create execution role, or provide execution role ARN/name to use existing
Previously configured: arn:aws:iam::<account-id>:role/AmazonBedrockAgentCoreSDKRuntime-us-west-2-8e3d21fabc
Execution role ARN/name (or press Enter to auto-create):
✓ Will auto-create execution role

🏗️  ECR Repository
Press **Enter** to auto-create ECR repository, or provide ECR Repository URI to use existing
Previously configured: <account-id>.dkr.ecr.us-west-2.amazonaws.com/bedrock-agentcore-weather_agent
ECR Repository URI (or press Enter to auto-create):
✓ Will auto-create ECR repository

🔍 Detected dependency file: requirements.txt
Press **Enter** to use this file, or type a different path (use Tab for autocomplete):
Path or Press Enter to use detected dependency file:
✓ Using detected file: requirements.txt

🔐 Authorization Configuration
By default, Bedrock AgentCore uses IAM authorization.
Configure OAuth authorizer instead? (yes/no) [no]: yes

📋 OAuth Configuration
Enter OAuth discovery URL: https://cognito-idp.us-west-2.amazonaws.com/us-west-2_sI1JhVabc/.well-known/openid-configuration
Enter allowed OAuth client IDs (comma-separated): 24itvh9p3rbv4p7jfkbftfrabc
Enter allowed OAuth audience (comma-separated):
✓ OAuth authorizer configuration created
Configuring BedrockAgentCore agent: mcp_server
Generated Dockerfile: /home/ubuntu/workshop/agentcore/Dockerfile
Generated .dockerignore: /home/ubuntu/workshop/agentcore/.dockerignore
Changing default agent from 'weather_agent' to 'mcp_server'
╭───────────────────────────────── Configuration Success ───────────────────────────────────╮
│ Configuration Complete                                                                    │
│                                                                                           │
│ Agent Details:                                                                            │
│ Agent Name: mcp_server                                                                    │
│ Runtime: Docker                                                                           │
│ Region: us-west-2                                                                         │
│ Account: <account-id>                                                                     │
│                                                                                           │
│ Configuration:                                                                            │
│ Execution Role: None                                                                      │
│ ECR Repository: Auto-create                                                               │
│ Authorization: OAuth (customJWTAuthorizer)                                                │
│                                                                                           │
│ 📄 Config saved to: /home/ubuntu/workshop/agentcore/runtime/.bedrock_agentcore.yaml       │
│                                                                                           │
│ Next Steps:                                                                               │
│    agentcore launch                                                                       │
╰───────────────────────────────────────────────────────────────────────────────────────────╯
To understand what will be deployed, you may wish to take a look at the configuration file /home/ubuntu/workshop/agentcore/runtime/.bedrock_agentcore.yaml before proceeding.

4. Deploy the Bedrock AgentCore Runtime
Run the following in a terminal window to deploy the AgentCore Runtime. This builds the container image locally and deploys it to cloud.

1
agentcore launch --local-build

Remember to run agentcore launch without the --local_build flag if you are on x86 platform. This will use the default CodeBuild option to build the arm64 container image (here, the build process will take a few minutes--unlike the --local-build option which will be significantly faster)

Sample output

🚀 Launching Bedrock AgentCore (codebuild mode - RECOMMENDED)...
   • Build ARM64 containers in the cloud with CodeBuild
   • No local Docker required (DEFAULT behavior)
   • Production-ready deployment

💡 Deployment options:
   • agentcore launch                → CodeBuild (current)
   • agentcore launch --local        → Local development
   • agentcore launch --local-build  → Local build + cloud deploy

Starting CodeBuild ARM64 deployment for agent 'mcp_server' to account <account-id> (us-west-2)
.
.
.
╭──────────────────────────────────────── CodeBuild Deployment Complete ────────────────────────────────────────╮
│ CodeBuild ARM64 Deployment Successful!                                                                        │
│                                                                                                               │
│ Agent Name: mcp_server                                                                                        │
│ CodeBuild ID: bedrock-agentcore-mcp_server-builder:eb4b109a-c098-41d8-a57d-c0b6e5106abc                       │
│ Agent ARN: arn:aws:bedrock-agentcore:us-west-2:<account-id>:runtime/mcp_server-TppBVw7abc                     │
│ ECR URI: <account-id>.dkr.ecr.us-west-2.amazonaws.com/bedrock-agentcore-mcp_server:latest                     │
│                                                                                                               │
│ ARM64 container deployed to Bedrock AgentCore.                                                                │
│                                                                                                               │
│ You can now check the status of your Bedrock AgentCore endpoint with:                                         │
│ agentcore status                                                                                              │
│                                                                                                               │
│ You can now invoke your Bedrock AgentCore endpoint with:                                                      │
│ agentcore invoke '{"prompt": "Hello"}'                                                                        │
│                                                                                                               │
│ 📋 Agent logs available at:                                                                                   │
│    /aws/bedrock-agentcore/runtimes/mcp_server-TppBVw7abc-DEFAULT                                              │
│    /aws/bedrock-agentcore/runtimes/mcp_server-TppBVw7abc-DEFAULT/runtime-logs                                 │
│                                                                                                               │
│ 💡 Tail logs with:                                                                                            │
│    aws logs tail /aws/bedrock-agentcore/runtimes/mcp_server-TppBVw7abc-DEFAULT --follow                       │
│    aws logs tail /aws/bedrock-agentcore/runtimes/mcp_server-TppBVw7abc-DEFAULT --since 1h                     │
╰───────────────────────────────────────────────────────────────────────────────────────────────────────────────╯
5. Invoke the Bedrock AgentCore Runtime
Run the following in a terminal window. Note that the bearer token expires rather quickly, so it is important to generate it immediately before invoking mcp_client_remote.py:

1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
16
# Load environment variables from .env file
source .env

# Verify CLIENT_ID was loaded correctly
echo "CLIENT_ID: $CLIENT_ID"

# Execute AWS Cognito authentication
export BEARER_TOKEN=$(aws cognito-idp initiate-auth \
  --client-id "$CLIENT_ID" \
  --auth-flow USER_PASSWORD_AUTH \
  --auth-parameters USERNAME='testuser',PASSWORD='PERMANENT_PASSWORD' \
  --region $AWS_REGION | jq -r '.AuthenticationResult.AccessToken')

echo "Bearer Token: $BEARER_TOKEN"

uv run mcp_client_remote.py

Sample output (truncated):

CLIENT_ID: 412b6cop6om8l3p4tj05r2b8fv
Bearer Token: eyJ... (truncated)
Using region: us-west-2
Using the first agent ARN: arn:aws:bedrock-agentcore:us-west-2:<account-id>:runtime/mcp_server2-FBg0PE5Sk3
Agent ARN: arn:aws:bedrock-agentcore:us-west-2:<account-id>:runtime/mcp_server2-FBg0PE5Sk3
Bearer Token: eyJ... (truncated)
Invoking: https://bedrock-agentcore.us-west-2.amazonaws.com/runtimes/arn%3Aaws%3Abedrock-agentcore%3Aus-west-2%3A874595112745%3Aruntime%2Fmcp_server2-FBg0PE5Sk3/invocations?qualifier=DEFAULT,
with headers: {'authorization': 'Bearer eyJ... (truncated)', 'Content-Type': 'application/json'}

meta=None nextCursor=None tools=[Tool(name='add_numbers', title=None, description='Add two numbers together', inputSchema={'properties': {'a': {'title': 'A', 'type': 'integer'}, 'b': {'title': 'B', 'type': 'integer'}}, 'required': ['a', 'b'], 'title': 'add_numbersArguments', 'type': 'object'}, outputSchema={'properties': {'result': {'title': 'Result', 'type': 'integer'}}, 'required': ['result'], 'title': 'add_numbersOutput', 'type': 'object'}, annotations=None, meta=None), Tool(name='multiply_numbers', title=None, description='Multiply two numbers together', inputSchema={'properties': {'a': {'title': 'A', 'type': 'integer'}, 'b': {'title': 'B', 'type': 'integer'}}, 'required': ['a', 'b'], 'title': 'multiply_numbersArguments', 'type': 'object'}, outputSchema={'properties': {'result': {'title': 'Result', 'type': 'integer'}}, 'required': ['result'], 'title': 'multiply_numbersOutput', 'type': 'object'}, annotations=None, meta=None), Tool(name='greet_user', title=None, description='Greet a user by name', inputSchema={'properties': {'name': {'title': 'Name', 'type': 'string'}}, 'required': ['name'], 'title': 'greet_userArguments', 'type': 'object'}, outputSchema={'properties': {'result': {'title': 'Result', 'type': 'string'}}, 'required': ['result'], 'title': 'greet_userOutput', 'type': 'object'}, annotations=None, meta=None)]
6. [Optional] Cleanup
Run the following to delete the AgentCore runtimes that were created.

1
2
cd ~/workshop/agentcore/
uv run cleanup_agents.py

You can also run rm ~/workshop/agentcore/runtime/.bedrock_agentcore.yaml if you have no more agents deployed.


