---
title: "Building with Model-Context Protocol (MCP): Creating AI-Accessible APIs"
datePublished: Fri Apr 18 2025 07:15:12 GMT+0000 (Coordinated Universal Time)
cuid: cmd4xv2gs000302lberoo7pcp
slug: building-with-model-context-protocol-mcp-creating-ai-accessible-apis-0dcf5fdcc315
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1752608520847/6716c188-b594-4d13-a75c-6580b88f2eab.png

---

In the evolving landscape of AI integration, the Model- Context Protocol (MCP) stands out as a powerful paradigm for creating APIs that AI models can seamlessly interact with. Today, I’ll walk you through creating your own MCP implementation using the FastMCP library — a straightforward yet powerful tool for exposing your functions to AI systems.

### What Is Model-Context Protocol?

At its core, MCP provides a standardized way for AI models to discover, understand, and call functions within your applications. Think of it as building a bridge between the natural language capabilities of AI models and the computational functions of your software.

Unlike traditional APIs designed primarily for developer consumption, MCP-enabled endpoints are optimized for AI interaction — creating a new class of applications where language models can become active participants in your software ecosystem.

### Why MCP Matters

The implications are profound:

*   **Reducing AI hallucinations**: By providing structured access to real computational tools, MCPs help ground AI responses in factual data
*   **Enabling complex workflows**: Models can chain tool calls to accomplish multistep tasks
*   **Extending AI capabilities**: Language models gain abilities beyond their training data through tool access
*   **Simplifying integration**: Developers can expose functionality to AI models without complex prompt engineering

### Getting Started with FastMCP

Let’s dive into implementation. The FastMCP library makes creating MCP-compatible APIs remarkably straightforward. Here’s how to build one from scratch:

### 1\. Setting Up Your Environment

First, ensure you have the necessary dependencies:

pip install fastmcp fastapi uvicorn requests

Or create a `requirements.txt` file with:

fastmcp==2.1.2  
fastapi  
uvicorn  
requests

And install with:

pip install -r requirements.txt

### 2\. Creating Your MCP Server

The server component exposes your functions as tools that models can call. Let’s build a simple math operations server:

from fastmcp import FastMCP  
from fastapi import FastAPI, Body  
import uvicorn

\# Initialize FastAPI and FastMCP  
app = FastAPI()  
mcp = FastMCP("Math Operations Server")

\# Define a tool with the @mcp.tool() decorator  
@mcp.tool()  
def multiply(a: int, b: int) -> int:  
    """Multiplies two integers and returns the result."""  
    return a \* b

\# Expose the tool via a FastAPI endpoint  
@app.post("/multiply")  
def call\_multiply(data: dict=Body(...)):  
    return {"result": multiply(data.get("a", 0), data.get("b", 0))}  
      
@app.get("/")      
def home():  
    return {"message": "Welcome to the Math Operations Server!"}

\# Run the server  
if \_\_name\_\_ == "\_\_main\_\_":  
    uvicorn.run(app, host="0.0.0.0", port=8000)

This code does several important things:

1.  Creates a FastAPI application to handle HTTP requests
2.  Initializes a FastMCP instance with a descriptive name
3.  Defines a `multiply` function and registers it as an MCP tool
4.  Creates an API endpoint that accepts JSON data and calls our tool
5.  Launches the server on port 8000

The magic happens with the `@mcp.tool()` decorator, which registers your function in the MCP schema, making it discoverable by AI models.

### 3\. Building the Client

Now, let’s create a client to interact with our server:

import requests

def test\_multiply(a, b):  
    """Test the multiply endpoint."""  
    # Send POST request to the server  
    res = requests.post(  
        "http://localhost:8000/multiply",   
        json={"a": a, "b": b}  
    )  
      
    # Print request details for debugging  
    print("Request:", res.request.body)  
      
    # Handle the response  
    if res.status\_code == 200:  
        print("Multiply result:", res.json())  
    else:     
        print("Error:", res.status\_code, res.text)  
      
    return res.json()       

if \_\_name\_\_ == "\_\_main\_\_":  
    test\_multiply(9, 5)

This client:

1.  Sends a POST request to our server’s endpoint
2.  Includes parameters as JSON in the request body
3.  Processes and displays the response
4.  Returns the JSON response for further processing

### Enhancing Your MCP Implementation

The example above is just the beginning. Here’s how to expand your MCP capabilities:

### Adding More Complex Tools

Tools can perform complex operations and integrate with external services:

@mcp.tool()  
def fetch\_weather(location: str) -> dict:  
    """Get current weather for a location."""  
    \# Integration with weather API  
    \# ...  
    return weather\_data

@mcp.tool()  
def analyze\_sentiment(text: str) -> dict:  
    """Analyze the sentiment of provided text."""  
    # Sentiment analysis logic  
    # ...  
    return sentiment\_results

### Tool Documentation

The docstrings you provide for your tools serve a crucial purpose — they help the AI understand when and how to use each tool:

@mcp.tool()  
def currency\_convert(amount: float, from\_currency: str, to\_currency: str) -> float:  
    """  
    Convert an amount from one currency to another.  
      
    Parameters:  
        amount: The amount to convert  
        from\_currency: 3\-letter currency code to convert from (e.g., USD)  
        to\_currency: 3\-letter currency code to convert to (e.g., EUR)  
          
    Returns:  
        The converted amount in the target currency  
    """  
    # Conversion logic  
    # ...

### Structured Inputs and Outputs

For complex data structures, use Pydantic models to ensure proper validation:

from pydantic import BaseModel

class Product(BaseModel):  
    id: str  
    name: str  
    price: float  
      
class InventoryResult(BaseModel):  
    available: int  
    warehouse: str  
    eta\_days: int | None

@mcp.tool()  
def check\_inventory(product: Product) -> InventoryResult:  
    """Check inventory status for a product."""  
    # Inventory check logic  
    # ...

### Integrating with AI Models

Once your MCP server is running, you can connect it to AI systems that support tool calling. While the specifics depend on the AI platform you’re using, the general workflow is:

1.  Register your tools with the AI service
2.  Include tool definitions in your model requests
3.  Process tool calls in the model responses
4.  Execute the requested functions
5.  Return the results to continue the interaction

### Deployment Considerations

When deploying your MCP services to production, consider:

*   **Security**: Implement proper authentication and rate limiting
*   **Monitoring**: Track usage patterns and performance metrics
*   **Versioning**: Maintain backward compatibility as tools evolve
*   **Documentation**: Keep tool descriptions clear and comprehensive for AI consumption

### Beyond the Basics: Advanced MCP Patterns

As you become more familiar with MCP, you might explore:

*   **Tool composition**: Creating higher-level tools that call other tools
*   **Streaming responses**: Supporting progressive output for long-running operations
*   **Context management**: Maintaining state across multiple tool calls
*   **Fallback mechanisms**: Gracefully handling errors or edge cases

### Conclusion

The Model-Context Protocol represents a fundamental shift in how we integrate AI capabilities into our software systems. By creating well-defined, AI-accessible tools, we’re building a new layer of abstraction that enables more powerful and reliable AI applications.

FastMCP provides an elegant entry point into this ecosystem, allowing developers to quickly expose their functionality in a format that modern AI models can discover and leverage. As this paradigm continues to evolve, we can expect increasingly sophisticated interactions between language models and the computational tools at their disposal.

Whether you’re building internal productivity tools, customer-facing applications, or experimental AI interfaces, MCP offers a structured approach to extending AI capabilities beyond their inherent limitations — creating a more powerful, useful, and grounded AI experience.