# CloudMicroservicesHub

## Description
**CloudMicroservicesHub** demonstrates a serverless microservices architecture on Google Cloud Platform (GCP). This project integrates Google Cloud Functions, Cloud Run, and Pub/Sub to build a scalable, event-driven application. It features a Cloud Function for message publishing, a Cloud Run service for message processing, and Pub/Sub for event handling.

## Table of Contents
- [Description](#description)
- [Installation](#installation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)
- [Acknowledgments](#acknowledgments)

## Installation
1. **Clone the Repository:**
   
   git clone https://github.com/your-username/CloudMicroservicesHub.git
   

2. **Navigate to the Project Directory:**
   
   cd CloudMicroservicesHub
   

## Usage

### Cloud Functions

**Deploy Cloud Function:**

1. Navigate to the `cloud-functions` directory:
   
   cd cloud-functions


2. Deploy the function:
   
   gcloud functions deploy publishMessage --runtime nodejs16 --trigger-http --allow-unauthenticated
   

**Test Cloud Function:**

Use the function URL to publish a message:
   
   curl -X POST https://us-central1-[PROJECT-ID].cloudfunctions.net/publishMessage \
   -H "Content-Type: application/json" \
   --data '{"message":"Hello, world!"}'
   

### Cloud Run

**Deploy Cloud Run Service:**

1. Navigate to the `process-service` directory:
   
   cd process-service
   

2. Build and deploy the container:
   
   gcloud builds submit --tag gcr.io/[PROJECT-ID]/process-service
   gcloud run deploy process-service --image gcr.io/[PROJECT-ID]/process-service --platform managed --allow-unauthenticated
   

**Test Cloud Run Service:**

Verify that the service is running by accessing the URL provided after deployment.

### Pub/Sub Integration

**Create Pub/Sub Topic and Subscription:**

1. Create a Pub/Sub topic:
   
   gcloud pubsub topics create my-topic
   

2. Create a subscription:
   
   gcloud pubsub subscriptions create my-subscription --topic=my-topic
   

**Push Subscription to Cloud Run:**

1. Create a push subscription:
   
   gcloud pubsub subscriptions create my-push-subscription --topic=my-topic --push-endpoint=https://process-service-uu4fqwwwgq-uc.a.run.app/process-message --ack-deadline=10
   

## Contributing
We welcome contributions to this project! To contribute:

1. **Fork the Repository**
2. **Create a Feature Branch:**
   
   git checkout -b feature/your-feature
   
3. **Make Your Changes**
4. **Commit Your Changes:**
   
   git commit -am 'Add new feature or fix'
   
5. **Push to Your Branch:**
   
   git push origin feature/your-feature
   
6. **Create a Pull Request**

## License
This project is licensed under the MIT License. See the LICENSE file for details.

## Acknowledgments
- [Google Cloud Documentation](https://cloud.google.com/docs)
- [Node.js Documentation](https://nodejs.org/en/docs/)


### Steps to Add This to Your `README.md`:

1. **Copy the Template**: Copy the entire text provided above.
2. **Open Your `README.md` File**: Open your `README.md` file using your preferred code editor (such as nano, VS Code, etc.).
3. **Paste the Template**: Paste the copied content into your `README.md` file.
4. **Replace Placeholders**: 
   - Replace `[PROJECT-ID]` with your actual Google Cloud project ID.
   - Replace `your-username` with your GitHub username.
5. **Save and Commit**: Save the file and commit the changes to your Git repository using:
   
   git add README.md
   git commit -m "Update README.md with detailed usage instructions"
   git push origin main
   

