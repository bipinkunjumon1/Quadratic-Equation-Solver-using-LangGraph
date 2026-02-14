```markdown
# Quadratic Equation Solver using LangGraph

A Python-based solver for quadratic equations, built using LangGraph. This project demonstrates how to structure a computational workflow as a stateful graph with conditional branching, transitioning from input coefficients to equation display, discriminant calculation, and root determination.

## Project Overview

This project utilizes langgraph to create a directed graph that:

1. Initializes State: Accepts coefficients a, b, and c.

2. Shows Equation: Generates the quadratic equation string.

3. Calculates Discriminant: Computes the discriminant value.

4. Conditional Branching: Based on discriminant, determines if there are real roots, repeated roots, or no real roots.

5. Computes Result: Executes the appropriate node to calculate and format the roots or result message.

## Features

* State Management: Uses TypedDict to maintain a consistent state across nodes.

* Modular Logic: Separate nodes for equation display, discriminant calculation, and root types.

* Conditional Workflow: Uses conditional edges to branch based on discriminant value.

* Graph Visualization: Includes code to render the graph structure using Mermaid.

## Technical Stack

* Language: Python

* Orchestration: LangGraph

* Data Handling: typing.TypedDict

## Installation

1. Clone the repository:

   ```
   git clone https://github.com/your-username/quadratic-langgraph.git
   cd quadratic-langgraph
   ```

2. Install dependencies:

   ```
   pip install langgraph
   ```

## How It Works

### The State

The QuadState keeps track of the coefficients, equation, discriminant, and result:

```python
class QuadState(TypedDict):
    a: int
    b: int
    c: int

    equation: str
    result: str
    discriminant: float
```

### The Graph Logic

The workflow follows a linear path to discriminant, then branches conditionally:

* START → show_equation → calculate_discriminant → [conditional: real_root | repeated_roots | no_realroots] → END

## Usage

Run the script to see the output for a sample input:

```python
initial_state = {
    'a': 4,
    'b': 2,
    'c': 4
}
final_state = workflow.invoke(initial_state)
print(final_state)
# Output: {'a': 4, 'b': 2, 'c': 4, 'equation': '4x² + 2x + 4', 'result': ' no real  roots ', 'discriminant': -60}
```

## Visualization

The project includes a utility to display the graph structure:

```python
from IPython.display import Image
Image(workflow.get_graph().draw_mermaid_png())
```
```
