When you develop a generative AI app, you need to integrate language models into your application. To be able to use a language model, you need to deploy the model. Let's explore how to deploy language models in the Azure AI Foundry, after first understanding why to deploy a model.

## Understand why to deploy a model

Language models, like traditional machine learning models, are designed to generate output based on some input. To benefit from a model, you want a solution that can send input to a model, which the model processes, and then visualize the output somewhere.

With generative AI apps, you have a chat application that expects input from a user, often in the form of a question. You want the model to process that input, and to generate a response that you can send back, through the chat application, to your user. To integrate a language model that can process input data and generate output data, you need the model to be deployed to an **endpoint**.

An endpoint is a specific URL where a deployed model or service can be accessed. It acts as a gateway for users to send their requests to the model and receive the results. Each model deployment typically has its own unique endpoint, which allows different applications to communicate with the model through an **API** (**Application Programming Interface**).

When you deploy a language model from the model catalog with the Azure AI Foundry, you get an endpoint, which consists of a **target URI** (Uniform Resource Identifier) and a unique **key**. For example, a target URI for a deployed GPT-3.5 model can be:

`https://ai-aihubdevdemo.openai.azure.com/openai/deployments/gpt-35-turbo/chat/completions?api-version=2023-03-15-preview`

The URI includes your AI hub name, your deployed model name, and it specifies what you want the model to do. In the example, the GPT-3.5 model is used for chat completion.

To protect your deployed models, each deployment comes with a key. You're only authorized to send and receive requests to and from the target URI, if you also provide the key to authenticate.

To use a deployed model, you typically make an API call. You can make an API call using code like Python or C#, or a tool like Azure AI Foundry or [Postman](https://www.postman.com/?azure-portal=true). An API call involves sending a request to the model's endpoint using the API. The request usually includes the input data that you want the model to process. The model then processes the data and sends back a response with the results. This way, you can interact with the deployed model and utilize its capabilities in your applications.

Now that you understand why you want to deploy a model, let's explore the deployment options with Azure AI Foundry.

## Deploy a language model with Azure AI Foundry

When you deploy a language model with Azure AI Foundry, you have several types available, which depend on the model you want to deploy:

- Azure OpenAI service to deploy [Azure OpenAI models](/azure/ai-services/openai/concepts/models?azure-portal=true).
- Azure AI model inference to deploy [Azure OpenAI models and Models as a Service](/azure/ai-foundry/model-inference/concepts/models?azure-portal=true).
- Serverless APIs to deploy [Models as a Service](/azure/ai-foundry/how-to/model-catalog-overview#content-safety-for-models-deployed-via-serverless-apis?azure-portal=true).
- Managed compute to deploy [open-source and custom models](/azure/ai-foundry/how-to/model-catalog-overview#availability-of-models-for-deployment-as-managed-compute?azure-portal=true).

The associated cost will depend on the type of model you deploy, which deployment option you choose, and what you are doing with the model:

|Activity|Azure OpenAI models|Azure AI model inference|Models deployed as Serverless APIs (pay-as-you-go)|Models deployed with user-managed compute|
|---|---|---|---|---|
|Deploy the model|No, you aren't billed for deploying an Azure OpenAI model to your project.|No, you aren't billed for deploying an Azure OpenAI model to your project.|Yes, you're billed minimally per the infrastructure of the endpoint.|Yes, you're billed for the infrastructure hosting the model per minute.|
|Call the endpoint|Yes, you're billed based on your token usage.|Yes, you're billed based on your token usage.|Yes, you're billed based on your token usage.|None.|
