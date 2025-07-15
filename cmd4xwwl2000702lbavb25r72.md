---
title: "Build Generative Agents with API Integrations: Challenge Lab"
datePublished: Wed Mar 12 2025 05:16:00 GMT+0000 (Coordinated Universal Time)
cuid: cmd4xwwl2000702lbavb25r72
slug: build-generative-agents-with-api-integrations-challenge-lab-a6348d9f0470
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1752608605882/6da92e36-7e96-45fd-9c7c-c5d0a25d3832.png

---

### The Challenge: Building a Tech Support Scheduling Agent

Our mission: deploy a chatbot for Cymbal Shops (a fictional retail chain) that helps customers schedule tech support appointments. This challenge requires not just basic conversational capabilities, but also integration with external systems and knowledge bases.

The lab has three main objectives:

1.  Build a generative conversational agent using Vertex AI Agent Builder
2.  Create a Cloud Run Function and expose it as an OpenAPI Tool
3.  Add a Data Store for enhanced product knowledge

Let’s tackle each one systematically.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608603034/941354c1-ff62-44a1-a20a-20eafe035849.png)

### Task 1: Building a Conversational Agent with Vertex AI Agent Builder

Creating a conversational agent is our first step. Here’s how to accomplish it:

Step 1: Enable Required APIs

\# Enable required APIs  
gcloud services enable dialogflow.googleapis.com  
gcloud services enable discoveryengine.googleapis.com

### Step 2: Create the Agent

Navigate to the Vertex AI Agent Builder console and create a new app of type “Conversational agent” with the following specifications:

*   **Name**: Agent Name
*   **Region**: global
*   **Conversation start type**: Playbook

### Step 3: Configure Agent Settings

In the agent-level Settings menu, enable:

*   Cloud Logging
*   Conversation history Logging

### Step 4: Set Agent Goal and Instructions

Define the agent’s purpose and behavior:

**Goal**: Help users book a tech support appointment

\- Greet the user.  
\- Gather appointment details.  
 - Ask for a location  
 - Ask for a day of the week  
\- Coordinate a time based on available slots. Available slots are:  
 - Monday 9 am to 11 am  
 - Tuesday 10 am to 1 pm  
\- Ask for the user's name for the appointment.  
\- Confirm the appointment.

Step 1: Set Up IAM Permissions

\# Find the Dialogflow Service Agent email  
SERVICE\_AGENT=$(gcloud projects get-iam-policy $GOOGLE\_CLOUD\_PROJECT \\  
  --filter="(bindings.role:roles/dialogflow.serviceAgent)" \\  
  --format="value(bindings.members)")  
  
\# Grant Cloud Run Invoker role  
gcloud projects add-iam-policy-binding $GOOGLE\_CLOUD\_PROJECT \\  
  --member="$SERVICE\_AGENT" \\  
  --role="roles/run.invoker"

### Step 2: Create the Cloud Run Function

Create a function named “Cloud Function Name” in the specified region:

import functions\_framework  
from flask import jsonify  
  
@functions\_framework.http  
def get\_available\_slots(request):  
    """  
    Cloud Run Function to return available appointment time slots  
    based on the day of the week.  
      
    Args:  
        request (flask.Request): HTTP request object containing a JSON  
        payload with a 'day' field  
          
    Returns:  
        JSON response with available appointment time slots  
    """  
    \# Set CORS headers for preflight requests  
    if request.method == 'OPTIONS':  
        headers = {  
            'Access-Control-Allow-Origin': '\*',  
            'Access-Control-Allow-Methods': 'POST',  
            'Access-Control-Allow-Headers': 'Content-Type',  
            'Access-Control-Max-Age': '3600'  
        }  
        return ('', 204, headers)  
      
    \# Set CORS headers for main request  
    headers = {  
        'Access-Control-Allow-Origin': '\*'  
    }  
      
    \# Get the request JSON  
    request\_json = request.get\_json(silent=True)  
      
    \# Check if request contains the required 'day' field  
    if not request\_json or 'day' not in request\_json:  
        return (jsonify({  
            'error': 'Missing day parameter in request'  
        }), 400, headers)  
      
    \# Get the day from the request  
    day = request\_json\['day'\].lower()  
      
    \# Define available appointment slots  
    availability = {  
        'monday': \['9:00 AM - 11:00 AM'\],  
        'tuesday': \['10:00 AM - 1:00 PM'\],  
        'wednesday': \[\],  
        'thursday': \[\],  
        'friday': \[\],  
        'saturday': \[\],  
        'sunday': \[\]  
    }  
      
    \# Return the available slots for the requested day  
    if day in availability:  
        return (jsonify({  
            'day': day.capitalize(),  
            'available\_slots': availability\[day\]  
        }), 200, headers)  
    else:  
        return (jsonify({  
            'error': f"Invalid day: {day}. Please provide a valid day of the week."  
        }), 400, headers)  
  

### Step 3: Create an OpenAPI Tool

In the Conversational Agents dashboard, create a Tool:

*   **Name**: OpenAPI Tool Name
*   **Type**: OpenAPI
*   **OpenAPI Spec**:

openapi: 3.0.0  
info:  
  title: Appointment Scheduler API  
  description: API to retrieve available appointment time slots  
  version: 1.0.0  
servers:  
  \- url: 'https://cymshops-reservation-564591385813.us-west1.run.app'  
paths:  
  /:  
    post:  
      summary: Get available appointment slots by day  
      operationId: getAvailableSlots  
      requestBody:  
        description: Day for which to check appointment availability  
        required: true  
        content:  
          application/json:  
            schema:  
              $ref: '#/components/schemas/AppointmentRequest'  
      responses:  
        '200':  
          description: Successful operation  
          content:  
            application/json:  
              schema:  
                $ref: '#/components/schemas/AppointmentResponse'  
        '400':  
          description: Invalid input  
components:  
  schemas:  
    AppointmentRequest:  
      type: object  
      required:  
        \- day  
      properties:  
        day:  
          type: string  
          description: Day of the week to check availability  
    AppointmentResponse:  
      type: object  
      properties:  
        day:  
          type: string  
          description: Day of the week (capitalized)  
        available\_slots:  
          type: array  
          items:  
            type: string  
          description: List of available time slots for the requested day

### Step 4: Update Agent Instructions

Modify the agent’s instructions to use the OpenAPI Tool:

\- Greet the user.  
\- Gather appointment details:  
    \- Ask for a location  
    \- Ask for a day of the week  
\- Check available time slots using ${TOOL:cymbal-integration-tool}  
\- Ask the user to choose from available time slots  
\- Ask for the user's name for the appointment.  
\- Confirm the appointment.  
\- If the user asks a question about products:  
    \- Use the ${TOOL:Google Datastore} to find relevant product information  
    \- Provide a clear, concise answer based on the information in the Data Store  
\- Always maintain a helpful, professional tone.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608604433/b5271e21-a991-459b-a82a-7804f9213af8.png)