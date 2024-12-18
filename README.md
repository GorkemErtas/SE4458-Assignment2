Payment and Notification API
This project implements a payment processing and notification system using RabbitMQ to handle message queues for payments and notifications. The system consists of three main components:

Payment API - A RESTful API that accepts payment details (e.g., user, payment type, and card number) and sends the payment information to a RabbitMQ payment queue.
Payment Service - A service that consumes messages from the payment queue, processes the payment, and then sends a notification message to a RabbitMQ notification queue.
Notification Service - A service that consumes messages from the notification queue and sends notifications to users about their payment status.
Project Workflow
Payment API:

Receives payment details from users via a POST request to the /make-payment endpoint.
Validates the payment details and sends the payment information to the RabbitMQ payment queue.
Payment Service:

Consumes messages from the payment queue.
Processes the payment and, once successful, sends a notification message to the notification queue.
Notification Service:

Consumes messages from the notification queue.
Sends a notification to users confirming that their payment has been successfully processed.
Technology Stack
Node.js: Backend framework for building the API and services.
RabbitMQ: Message broker for handling communication between the services.
Docker (optional): Can be used for containerizing the services.
System Components
Payment API (payment-api.js): A REST API that accepts payment data and pushes it to RabbitMQ.
Payment Service (payment-service.js): A service that processes payments from the RabbitMQ payment queue and sends notifications.
Notification Service (notification-service.js): A service that sends notifications from the RabbitMQ notification queue.
Key Features
Message Queues: Payments and notifications are processed asynchronously using RabbitMQ message queues.
Persistent Storage: RabbitMQ ensures that messages are not lost even if the consumer services are temporarily unavailable.
Scalable: The services can be scaled independently to handle increased load.
Architecture Overview
The Payment API serves as the entry point for users to submit payment details.
The Payment Service processes payments and triggers notifications.
The Notification Service notifies users about the successful processing of their payments.
