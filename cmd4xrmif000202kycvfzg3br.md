---
title: "The Evolution of Activation Functions in Deep Learning: From Sigmoid to SwiGLU 🧠"
datePublished: Wed Mar 19 2025 16:01:22 GMT+0000 (Coordinated Universal Time)
cuid: cmd4xrmif000202kycvfzg3br
slug: activation-function-1373b06615ea
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1752608359888/dfa2b00c-0581-4be6-9897-c8b2e5c1204f.png

---

When I first started exploring deep learning, I was overwhelmed by the seemingly endless array of activation functions. Why so many options? What makes ReLU better than sigmoid in certain situations? And what in the world is a SwiGLU?

In this deep dive, I’ll take you through the fascinating evolution of activation functions — the unsung heroes that give neural networks their power to learn complex patterns. We’ll trace their development from the early days of neural networks to today’s cutting-edge language models, understanding not just how they work, but *why* they matter.

The journey begins in 1943 with Warren McCulloch and Walter Pitts, who created the first mathematical model of a neural network. Their work laid the foundation by demonstrating how simple neural units could perform logical operations.

Then came Frank Rosenblatt’s Perceptron in 1957 — a breakthrough that introduced weighted connections and demonstrated machines could learn from examples rather than being explicitly programmed.

But progress wasn’t linear. In 1969, Marvin Minsky and Seymour Papert published “Perceptrons,” proving that single-layer perceptrons couldn’t solve non-linearly separable problems like XOR. This triggered the first “AI winter,” nearly ending neural network research for two decades.

The renaissance arrived in the late 1980s with the development of efficient backpropagation algorithms and the proof of the Universal Approximation Theorem, which showed that even a single hidden layer could, in theory, approximate any continuous function.

### Why Activation Functions Matter 🔑

At their core, neural networks are just fancy function approximators. They take inputs, apply weights, add biases, and then… this is where activation functions enter the picture.

Without activation functions, neural networks would just be glorified linear regression models. Here’s why:

*   **Non-linearity**: They introduce non-linear properties, allowing networks to learn complex patterns
*   **Decision boundaries**: They help create sophisticated decision boundaries beyond simple straight lines
*   **Gradient flow**: They influence how gradients flow backward during training
*   **Representation capacity**: They determine what kinds of relationships the network can model

As one of my mentors put it: “If weights and biases are the knobs and dials of your neural network, activation functions are the engines that generate its power.”

### The Classic Era: Sigmoid and Tanh 📊

### Sigmoid: The Original S-Curve

The sigmoid function dominated early neural networks. It squashes any input into a range between 0 and 1, creating that characteristic S-shaped curve:

Its elegance comes from its derivative:

This mathematical beauty made backpropagation calculations cleaner. Plus, its output could be interpreted as a probability, making it perfect for binary classification.

But beauty came with drawbacks:

1.  **Vanishing gradient problem**: For inputs with large magnitude, the gradient becomes nearly zero, causing learning to stall
2.  **Not zero-centered**: Outputs are always positive, causing zigzag trajectories during gradient descent
3.  **Computational expense**: Exponential functions are relatively costly to compute

### Tanh: The Zero-Centered Upgrade

Tanh emerged as sigmoid’s sophisticated cousin, offering a similar S-shape but ranging from -1 to 1:

This zero-centering addressed one of sigmoid’s key weaknesses, often resulting in faster convergence. But the vanishing gradient problem remained.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608344738/cc2377bf-4f9d-43a9-847d-a29e325a15df.png)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608346066/ff14cd57-384d-459e-9363-de930167d8db.png)

### ReLU: The Game-Changer

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608347433/7a2a6f6d-fe54-4b41-9929-a328306e1e95.png)

Just like that — if the input is positive, it passes through; if negative, it becomes zero. No complex exponential computations, just a simple threshold.

Despite (or perhaps because of) this simplicity, ReLU solved several critical problems:

1.  **Computational efficiency**: Just a max operation, no expensive exponentials
2.  **Sparsity**: By zeroing out negative inputs, ReLU creates naturally sparse representations
3.  **No saturation for positive values**: The gradient remains constant for all positive inputs

The impact was immediate and profound. Training time for deep networks dropped dramatically — sometimes by 6x — and suddenly, training truly deep architectures became practical. AlexNet’s victory in the 2012 ImageNet competition using ReLU activation marked a turning point in deep learning history.

But ReLU had its own Achilles’ heel — the “dying ReLU” problem. If a neuron consistently receives negative inputs, it outputs zero, its gradient becomes zero, and it essentially “dies” during training, never to be revived.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608348985/2a0a1ee6-6737-4423-8644-51029bb85215.png)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608350320/fc4a82f6-1222-4112-99ff-ab888acc550f.png)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608351527/e294d9ab-c860-4287-bdb5-8d6414908f28.png)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608352941/b124e247-f0f6-485b-8746-5b7c8429d284.png)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608354251/6062ddbb-1a64-4376-9f54-9d6d1a35ddd3.png)

### The Transformer Era: GELU, Swish, and Beyond 🌟

### GELU: Gaussian Error Linear Unit

As transformer architectures like BERT and GPT emerged, so did new activation functions optimized for these models. GELU (Gaussian Error Linear Unit) quickly became the preferred choice:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608355882/b12e636c-9b19-46c5-8a1f-730e96095285.png)

Where Φ(x) is the cumulative distribution function of the standard normal distribution.

GELU can be viewed as a smooth approximation of ReLU, but with probabilistic properties. It’s as if each neuron has a probability of being active, similar to dropout regularization, but baked directly into the activation function.

### Swish/SiLU: The Self-Gated Function

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608357054/ab7e20db-277a-4882-a9d9-097e24932633.png)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1752608358426/06474dd5-64f8-4dc9-afc8-e4c95e3bb487.png)

Simultaneously discovered by different research groups (named Swish by Google and SiLU by others), this function combines sigmoid and linear components:

Remarkably, this function was discovered using automated search techniques — essentially using AI to find better building blocks for AI. It has proven particularly effective in computer vision models like EfficientNet and MobileNetV3.

### GLU and SwiGLU: The Gating Revolution

Gated Linear Unit (GLU) introduced a fundamentally different approach — using part of the input to gate another part:

Where the input x is split into A and B, and ⊗ represents element-wise multiplication.

This gating mechanism allows selective information flow and has become central to many state-of-the-art language models.

SwiGLU combines Swish with GLU:

It’s now a core component in cutting-edge models like PaLM, LLaMA, and likely GPT-4, offering superior performance and better parameter efficiency.