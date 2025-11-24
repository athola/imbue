---
name: mage-doc-review
description: Evaluate and refine documentation, docheaders, and code comments. Focus on clarity, removing AI-generated content, and establishing a professional tone.
category: documentation-refinement
tags: [documentation, writing, AI-slop, tone, clarity, style]
dependencies: []
tools: [] # This skill uses internal capabilities rather than external tools directly
usage_patterns:
  - documentation-cleanup
  - style-consistency
  - AI-content-review
complexity: intermediate
estimated_tokens: 2000
---

# Documentation Refinement

## Overview
This skill refines documentation, docheaders, and inline comments to improve clarity and remove AI-generated "slop." It focuses on creating a professional tone that is clear, precise, and follows specific style guidelines.

## When to Employ This Skill
- When documentation needs to be polished for clarity and professionalism, not just to convey information.
- When removing common AI-generated phrases and rhetorical excesses to foster a grounded and specific voice.
- When integrating new text into an existing codebase that requires a consistent, high-quality tone.
- During project handovers or auditing, to ensure explanatory texts reflect deliberate thought and a consistent perspective.

## Core Principles of Refinement
1.  **Grounded Voice**: Explain *why* concepts matter, using practical insights and acknowledging trade-offs, instead of abstract benefits or unsubstantiated claims.
2.  **Concise Expression**: Eliminate superfluous language, rhetorical flourishes, and formulaic structures. Deliver information directly and efficiently.
3.  **Specific Detail**: Prioritize concrete examples, numerical data, filenames, and direct commands over vague adjectives or generalized statements.
4.  **Narrative Balance**: Weave actionable bullet points with explanatory paragraphs, providing nuance without overwhelming lists.
5.  **Linguistic Precision**: Scrutinize for repetitive phrasing, excessive punctuation (e.g., em dashes), and overly complex sentence structures. Text should flow naturally and purposefully.
6.  **Authorial Perspective**: Discuss deliberate decision-making, risks, choices, and their rationale to establish a consistent, authentic voice.
7.  **Clarity Over Cliche**: Avoid ambiguous expressions and overused jargon. Favor direct and succinct language.
8.  **Mindful Terminology**: Prefer terms like "default" or "secondary" over "fallback" to prevent misinterpretation, and use humanizing language only when genuinely applicable.
9.  **Incremental Transformation**: For extensive documents, process changes section by section, allowing for review and confirmation at each stage.

## Process of Refinement
1.  **Initial Assessment**: Read the target document to understand its current content, structure, and tone.
2.  **Identify "Slop"**: Pinpoint patterns indicating AI generation, such as vague generalities, rhetorical crutches, and repetitive phrasing.
3.  **Enhance Language**: Reword sentences for precision, replace weak verbs, and clarify ambiguous statements.
4.  **Adjust Tone**: Modify vocabulary and sentence structure to introduce a professional and clear undertone, without compromising readability.
5.  **Optimize Structure**: Reorganize content for better flow, balancing narrative and bulleted information.
6.  **User Review**: Present refined sections or entire documents for human review and approval, confirming alignment with user intent and maintaining tone balance.

## Before/After Examples

### Example 1: Function Documentation

**Before (AI-Generated):**
```python
def calculate_total(items):
    """
    This powerful function takes a list of items and skillfully computes the total sum.
    It leverages Python's built-in sum function to efficiently iterate through the
    provided collection and return the calculated total. This is incredibly useful
    for various scenarios where you need to aggregate numerical values.

    Args:
        items: A list of numerical values that you want to sum up

    Returns:
        The total sum of all the values in the items list

    Raises:
        TypeError: If non-numerical values are encountered
    """
    return sum(items)
```

**After (Refined):**
```python
def calculate_total(items):
    """Calculate the sum of numerical values in a list.

    Args:
        items (list[float|int]): List of numbers to sum

    Returns:
        float|int: Sum of all values in the list

    Raises:
        TypeError: If items contain non-numerical values
    """
    return sum(items)
```

### Example 2: README Section

**Before (AI-Generated):**
```
## Installation

Embarking on your journey with our amazing library is incredibly straightforward!
We've designed the installation process to be as seamless as possible, ensuring
that you can get up and running in no time. Follow these simple steps and you'll
be harnessing the full power of our cutting-edge solution in just moments!

### Prerequisites

Before diving in, make sure you have the following foundational elements in place:
- Python 3.7 or higher (the backbone of our implementation)
- pip (your trusted package manager)
- A sense of adventure! (optional but recommended)
```

**After (Refined):**
```
## Installation

Install the package using pip:

```bash
pip install library-name
```

### Prerequisites
- Python 3.7+
- pip package manager

For development setup with optional dependencies:
```bash
pip install library-name[dev]
```
```

### Example 3: API Documentation

**Before (AI-Generated):**
```
## User Authentication Endpoint

This revolutionary endpoint provides comprehensive authentication capabilities
that transform how users interact with our system. By leveraging state-of-the-art
security protocols, it ensures robust protection while delivering an exceptionally
smooth user experience that sets new industry standards.

**Endpoint:** POST /api/auth/login
**Description:** Authenticate user credentials with military-grade security

**Request Body (JSON):**
```
{
  "username": "your_username_here",  // The user's unique identifier
  "password": "your_secure_password",  // The user's secret password (encrypted)
  "remember_me": true  // Optional flag for session persistence
}
```

**Success Response (200 OK):**
```
{
  "token": "jwt_token_string",  // Authentication token for subsequent requests
  "user_id": 12345,  // Unique user identifier
  "expires_in": 3600  // Token lifetime in seconds
}
```
```

**After (Refined):**
```
## User Authentication

POST /api/auth/login

Authenticates a user with username and password credentials.

**Request Body:**
```json
{
  "username": "string",
  "password": "string",
  "remember_me": "boolean (optional)"
}
```

**Response (200 OK):**
```json
{
  "token": "string",
  "user_id": "integer",
  "expires_in": "integer"
}
```

**Error Responses:**
- 400 Invalid credentials
- 429 Rate limit exceeded
```

## Deliverables
-   Updated documentation files (e.g., Markdown, reStructuredText, plain text).
-   Refined docheaders and function/method comments.
-   A codebase where textual content shows enhanced clarity, consistency, and a professional tone.

## Risks & Mitigations
-   **Over-Stylization**:
    -   **Mitigation**: Maintain vigilance to ensure the tone remains professional and does not detract from clear, technical communication. User feedback is essential for balancing this.
-   **Loss of Original Intent**:
    -   **Mitigation**: A thorough initial assessment combined with iterative, user-approved revisions to preserve the core message and technical accuracy.
