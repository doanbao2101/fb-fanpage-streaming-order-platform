# Facebook Fanpage Streaming Order

Stream and track order data from Facebook fanpages in real-time using AWS services for efficient processing and storage. This project integrates Facebook's Webhook, AWS API Gateway, Lambda, Kinesis, SQS, and S3.

## Architecture Overview

### **Main Architecture**

The order data flows through the following sequence:

1. **Facebook Webhook** 🦸‍♂️
   Receives events from Facebook fanpages (e.g., new order events).

2. **AWS API Gateway** 🌐
   Exposes an endpoint to receive incoming data from the Facebook Webhook.

3. **AWS Lambda (Webhook and PUT Data)** 🔧
   Processes the incoming data, formats it, and pushes it to the next service.

4. **Kinesis Streaming** 📡
   Streams the order data in real-time for further processing.

5. **Kinesis Firehose + AWS Lambda (for Processing)** 🔥💻
   Firehose delivers the stream to storage. Lambda processes and transforms the data before saving it.

6. **S3** 🗄️
   Stores the processed data in Amazon S3 for long-term storage and future analysis.

---

### **Alternative Architecture (Early Stage)**

In the initial stage, replace Kinesis Streaming and Firehose with AWS SQS for message queuing and AWS Lambda for processing:

1. **Facebook Webhook** 🦸‍♂️
   Same as above.

2. **AWS API Gateway** 🌐
   Same as above.

3. **AWS Lambda (Webhook and PUT Data)** 🔧
   Same as above.

4. **AWS SQS** 📬
   Queues the data for processing instead of using Kinesis Streaming.

5. **AWS Lambda (Processing)** 🧠
   Processes the queued data.

6. **S3** 🗄️
   Stores the processed data in Amazon S3 for long-term storage and analysis.

---

## Prerequisites

* Facebook Developer Account
* AWS Account with permissions for API Gateway, Lambda, Kinesis, SQS, and S3

---

## Getting Started

1. **Clone the repository:**

   ```bash
   git clone https://github.com/your-username/fb-fanpage-streaming-order.git
   ```

2. **Set up the necessary AWS services**
   Follow the instructions in the documentation to set up AWS API Gateway, Lambda functions, and S3 bucket.

3. **Configure the Facebook Webhook**
   Set up the Webhook URL in the Facebook Developer portal to point to your AWS API Gateway endpoint.

4. **Deploy the Lambda functions**
   Use AWS SAM or Serverless Framework for deployment.

