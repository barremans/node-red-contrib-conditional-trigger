# node-red-contrib-conditional-trigger

**A Node-RED subflow for triggering conditional events based on multiple input messages.**

This subflow evaluates two incoming messages to determine if they meet specific conditions (e.g., both `msg.input` values are `true`). It routes the results to different outputs based on the evaluation. Ideal for automation workflows, IoT event processing, and decision-making systems.

---

## Features
- **Multi-Input Evaluation**: Processes multiple incoming messages.
- **Conditional Logic**: Triggers events only if specific conditions are met.
- **Flexible Outputs**: Routes messages to different outputs based on conditions.
- **Debug-Friendly**: Includes outputs to monitor the flow's logic.

---

## Installation

To use this subflow, you can install it via npm in your Node-RED environment:

1. Navigate to your Node-RED user directory:
   ```bash
   cd ~/.node-red


## How It Works

This subflow expects two input messages with the following structure:

### Input 1:
- `msg.input = true | false`
- `msg.topic = "input1"`

### Input 2:
- `msg.input = true | false`
- `msg.topic = "input2"`

The subflow combines these messages, evaluates their conditions, and routes the result to the appropriate output.

### Outputs:
- **Output 1**: Triggered if both inputs are `true`.
- **Output 2**: Triggered if one or both inputs are not `true`.

---

## Example Usage

Here’s an example flow to test the subflow:

```json
[
    {
        "id": "1cba32ac7aea14fd",
        "type": "inject",
        "name": "Input 1: True",
        "props": [
            {
                "p": "input",
                "v": "true",
                "vt": "bool"
            },
            {
                "p": "topic",
                "v": "input1",
                "vt": "str"
            }
        ],
        "wires": [["conditional-trigger"]]
    },
    {
        "id": "c88fe6573e26cabc",
        "type": "inject",
        "name": "Input 2: True",
        "props": [
            {
                "p": "input",
                "v": "true",
                "vt": "bool"
            },
            {
                "p": "topic",
                "v": "input2",
                "vt": "str"
            }
        ],
        "wires": [["conditional-trigger"]]
    },
    {
        "id": "conditional-trigger",
        "type": "subflow:conditional-trigger",
        "name": "Conditional Trigger Subflow"
    },
    {
        "id": "debug1",
        "type": "debug",
        "name": "Output 1: Event Triggered",
        "wires": []
    },
    {
        "id": "debug2",
        "type": "debug",
        "name": "Output 2: Alternate Event",
        "wires": []
    }
]
```
## Use Cases

- **IoT Automation:** Trigger actions when sensor states meet conditions.
- **Workflow Validation:** Ensure prerequisites are satisfied before progressing.
- **Multi-State Processing:** Handle logic requiring multiple inputs.
