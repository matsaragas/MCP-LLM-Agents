# MCP-LLM-Agents

The goal here is to build an LLM Agent using Model Context Protocol (MCP), an open standard introduced by Anthropic

### What is MCP?
It is an open protocol that enables seamless integration between LLM applications and 
external data sources and tools. MCP provides a standardized way to connect LLMs with the context they need.

### Why MCP?

MCP helps you build agents and complex workflows on top of LLMs. LLMs frequently need to integrate with data and tools, and 
MCP provide:

* A growing list of pre-built integration that your LLM can directly plug into
* The flexibility to switch between LLM providers and vendors
* Best practices for securing you data within your infrastructure


### General Architecture:

It follows a client-server architecture where a host application can connect to 
multiple servers [(Anthropic Architecture)](https://modelcontextprotocol.io/introduction#general-architecture):

![Alt text](images/mcp_architecture.png)

1) MCP Hosts: Programs like Claude Desktop, IDEs, or AI tools that want to access data through MCP
2) MCP Clients: Protocol clients that maintain 1:1 connections with servers
3) MCP Server: Lightweight programs that each expose specific capabilities through the standardized Model Context Protocol
4) Local Data Sources: Your computer’s files, databases, and services that MCP servers can securely access
5) Remote Services: External systems available over the internet (e.g., through APIs) that MCP servers can connect to

### Benefits of MCP

Before MCP, many LLM frameworks already enabled LLMs to have access to function calling, so what is the 
extra benefit? MCP simplify this by acting as a universal adapter, allowing AI model to connect with various data sources
and tools thorugh a standardized protocol:

* An open-source community-based library that supports FastAPI servers that can work with OpenAI spec directly.
* Developers can access a growing library of pre-built MCP servers for services like GitHub, Slack, and PostgreSQL, eliminate the need 
to write custom integration code.
* A standard JSON-RPC 2.0 protocol to define consistent, model-agnostic interface between LLMs and 
external tools


## FastMCP Server

Regardless what agent library you use (LangChain, Llama Index and etc.), we need to establish an MCP Server 
first. [FastMCP](https://gofastmcp.com/getting-started/welcome) is a Python library that simplifies the creation of MCP servers by alowing us to 
define tools using decorators.


##Examples

1) In this [example](FastMCP/examples/langraph_mcp_example/README.md), we use [FastMCP](https://gofastmcp.com/getting-started/welcome) and [LangGraph]((https://github.com/langchain-ai/langgraph)) to call multiple **MCP** tools


<!--## Financial Reasoning


How to generate comprehensive Financial Reports 

1) We need an orchestrator which coordinates the entire workflow. 
managing the flow of data between agents and ensuring each step completes successfully.
   
2) Research Agent & Research Evaluator: Work together in a feedback loop where the Research Agent 
collects data, and the research evaluator assesses its quality. 
   
3) Evaluator Optimizer (Research Quality Controller): Manages the feedback loop, evaluating outputs
and directing the Research Agent to improve data until reaching Excellent quality.
   
4) Analyst Agent: Analyzes the verified data to identify key financial insights.
5) Report Writer



   
