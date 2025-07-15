---
title: "Building Shia: An Advanced E-Commerce Chatbot with Dialogflow CX🛒💬"
datePublished: Thu Mar 13 2025 17:16:54 GMT+0000 (Coordinated Universal Time)
cuid: cmd4xpfzo000302jxabkqfkof
slug: building-shia-an-advanced-e-commerce-chatbot-with-dialogflow-cx-17f9371c3ff4
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1752608258132/dd60ca7e-cd6b-422d-a9d1-80eb57de7303.jpeg

---

Shia- Ecommerce Conversation AI Solutions

[https://youtu.be/UDTbExwh4vY](https://youtu.be/UDTbExwh4vY)

When I first ventured into the world of e-commerce chatbots, I quickly realized that creating a genuinely helpful conversational shopping assistant requires more than just basic intent matching. It demands an architecture that can handle complex, multi-turn conversations while seamlessly connecting to product catalogs, order systems, and user profiles.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608253323/f9d8f18d-ef1f-4127-99fd-52713f884d5e.png)

Enter **Shia**, an advanced e-commerce chatbot that leverages the combined power of Dialogflow CX, Google Cloud Functions, and BigQuery to create truly meaningful shopping conversations. In this post, I’ll take you behind the scenes of this project’s architecture and implementation, sharing insights from our development journey

<iframe src="https://www.youtube.com/embed/UDTbExwh4vY" width="700" height="393" frameborder="0" scrolling="no"></iframe>

### 1\. Dialogflow CX: The Conversation Brain 🧠

Unlike its predecessor, Dialogflow CX introduces a state-based conversation model using a hub-and-spoke design. This is perfect for e-commerce, where conversations naturally branch into various flows:

*   **MAIN\_MENU**: The central hub directing users to specialized flows
*   **BROWSE\_PRODUCTS**: For discovery and recommendations
*   **ORDER\_STATUS**: For tracking packages
*   **COMPLAINT**: For handling issues
*   **MY\_ACCOUNT**: For profile management
*   **OFFER**: For promotions and deals

What makes this architecture powerful is how it mirrors real-life shopping assistant interactions. A customer might start by browsing products, then check if an item is in stock, then ask about delivery options — all within a single conversation.

The state-based model allows us to maintain context across these transitions, creating a more natural and less frustrating experience.

### 2\. Cloud Functions: The Logic Layer ⚡

When Shia needs to retrieve product information or check order status, it calls Cloud Functions that act as intermediaries between the conversation and backend systems. These lightweight, event-driven functions:

*   Handle webhook fulfillment for dynamic responses
*   Connect to inventory, order management, and payment systems
*   Process and transform data for both the database and conversation

### 3\. BigQuery: The Data Foundation 💾

E-commerce is fundamentally data-driven, and BigQuery provides the scalable foundation we need. Our schema includes:

*   Which products are being frequently requested but unavailable
*   Common points where conversations break down
*   User satisfaction patterns across different flows

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608254954/71f4f898-c0d9-42f2-8bb0-17656e909d9f.png)

### Implementation Insights: Building for Natural Conversation 🔍

While the architecture diagram makes everything look clean and simple, the reality of building conversational experiences is messier. Here are some key insights from our implementation:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608256295/93a71157-b494-450e-a6d2-eacbf7448539.png)