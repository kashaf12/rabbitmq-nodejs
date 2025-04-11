# RabbitMQ Examples

This project demonstrates various messaging patterns using RabbitMQ and Node.js. Each example showcases a different messaging pattern, such as work queues, publish/subscribe, routing, topics, and RPC.

## Project Structure

```
.gitignore
package.json
README.md
src/
    hello_world/
        receive.js
        send.js
    pub_sub/
        emit_log.js
        receive_logs.js
    routing/
        emit_log_direct.js
        receive_logs_direct.js
    rpc/
        rpc_client.js
        rpc_server.js
    topics/
        emit_log_topic.js
        receive_logs_topic.js
    work_queues/
        new_task.js
        shell.sh
        worker.js
```

### Examples Overview

1. **Hello World** (`src/hello_world/`)

   - Basic example of sending and receiving messages using a simple queue.
   - Files:
     - `send.js`: Sends a "Hello World!" message to the queue.
     - `receive.js`: Receives and logs messages from the queue.

2. **Work Queues** (`src/work_queues/`)

   - Demonstrates distributing tasks among multiple workers.
   - Files:
     - `new_task.js`: Sends tasks to the queue.
     - `worker.js`: Processes tasks from the queue.
     - `shell.sh`: Script to send multiple tasks.

3. **Publish/Subscribe** (`src/pub_sub/`)

   - Demonstrates broadcasting messages to multiple consumers using a fanout exchange.
   - Files:
     - `emit_log.js`: Publishes log messages.
     - `receive_logs.js`: Receives log messages.

4. **Routing** (`src/routing/`)

   - Demonstrates routing messages to specific consumers based on severity using a direct exchange.
   - Files:
     - `emit_log_direct.js`: Publishes log messages with a severity.
     - `receive_logs_direct.js`: Receives log messages based on severity.

5. **Topics** (`src/topics/`)

   - Demonstrates routing messages based on patterns using a topic exchange.
   - Files:
     - `emit_log_topic.js`: Publishes log messages with a routing key.
     - `receive_logs_topic.js`: Receives log messages based on routing key patterns.

6. **RPC (Remote Procedure Call)** (`src/rpc/`)
   - Demonstrates implementing an RPC system using RabbitMQ.
   - Files:
     - `rpc_client.js`: Sends RPC requests and receives responses.
     - `rpc_server.js`: Processes RPC requests and sends responses.

## Prerequisites

- [Node.js](https://nodejs.org/) installed on your system.
- RabbitMQ server running locally or accessible via `amqp://localhost`.

## Installation

1. Clone the repository:

   ```bash
   git clone git@github.com:kashaf12/rabbitmq-nodejs.git
   cd rabbitmq-nodejs
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

## Usage

### Running Examples

1. **Hello World**

   - Start the receiver:
     ```bash
     node src/hello_world/receive.js
     ```
   - Send messages:
     ```bash
     node src/hello_world/send.js
     ```

2. **Work Queues**

   - Start one or more workers:
     ```bash
     node src/work_queues/worker.js
     ```
   - Send tasks:
     ```bash
     node src/work_queues/new_task.js "Task message"
     ```

3. **Publish/Subscribe**

   - Start one or more receivers:
     ```bash
     node src/pub_sub/receive_logs.js
     ```
   - Publish logs:
     ```bash
     node src/pub_sub/emit_log.js "Log message"
     ```

4. **Routing**

   - Start one or more receivers with severities:
     ```bash
     node src/routing/receive_logs_direct.js info warning
     ```
   - Publish logs with severity:
     ```bash
     node src/routing/emit_log_direct.js warning "Warning message"
     ```

5. **Topics**

   - Start one or more receivers with patterns:
     ```bash
     node src/topics/receive_logs_topic.js "*.error"
     ```
   - Publish logs with a routing key:
     ```bash
     node src/topics/emit_log_topic.js "kern.critical" "Critical kernel error"
     ```

6. **RPC**
   - Start the server:
     ```bash
     node src/rpc/rpc_server.js
     ```
   - Send an RPC request:
     ```bash
     node src/rpc/rpc_client.js 30
     ```

## License

This project is licensed under the ISC License. See the [LICENSE](LICENSE) file for details.
