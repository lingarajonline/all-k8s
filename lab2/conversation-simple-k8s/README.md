# Kubernetes Secret example

This repo is a companion to the developerWorks Mailbag video [Using Kubernetes secrets to manage credentials](https://developer.ibm.com/tv/using-kubernetes-secrets-manage-credentials/).

You'll find everything you need to:

* Build a Docker image from the Rameses II chatbot app
* Create a Kubernetes secret to store the credentials for the app
* Deploy the app to a Kubernetes cluster.

## Acknowledgements

This repo is based on the Watson Developer Cloud team's awesome 
[conversation-simple application](https://github.com/watson-developer-cloud/conversation-simple). Many thanks to that team for their excellent work.

## Before you begin

* Get on the IBM Cloud
    * [Sign up](https://console.bluemix.net/registration/?cm_sp=dw-bluemix-_-dwtv-dwMailbag-_-show&cm_sp=dw-bluemix-_-tv-_-devcenter) in the IBM Cloud console or use your existing account. Your account must have available space for at least 1 service and 1 cluster.
* Make sure that you've installed the following things:
    * The [Node.js runtime](https://nodejs.org/#download), including the [NPM package manager](https://npmjs.com)
    * The [Bluemix (`bx`) command-line client](https://console.bluemix.net/docs/cli/index.html#downloads). Once you've got that installed:
      * Type `bx plugin install container-registry -r Bluemix` to install the
        container registry plugin
      * Type `bx plugin install container-service -r Bluemix` to install the
        container service plugin
    * [Docker Community Edition](https://www.docker.com/get-docker)
    * The [Kubernetes `kubectl` command-line tool](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

## Some background, if you want it

All of the steps involved in creating the chatbot app, building the docker
image, and creating the Kubernetes cluster are covered in the following
developerWorks Mailbag videos:

* Building chatbots in the IBM Cloud - [Part 1](https://developer.ibm.com/tv/dw-mailbag-chatbots-part-1/) |
[Part 2](https://developer.ibm.com/tv/dw-mailbag-chatbots-part-2/)
* [Using Docker containers and images on your machine](https://developer.ibm.com/tv/dw-mailbag-docker-intro/)
* [Building a Kubernetes cluster in the IBM Cloud](https://developer.ibm.com/tv/dw-mailbag-kubernetes-clusters/)

If you go through all the exercises in those videos, you'll have the same
starting point as the companion video for this repo. _However_, you can use
the techniques we cover with any Docker image containing any application you choose.
Feel free to use your own app instead.

## Setting up the Conversation service

You can use an existing instance of the Conversation service if you have one.
If you want a guided tour for creating a new service, the developerWorks Mailbag
video [Building chatbots in the IBM Cloud - Part 1](https://developer.ibm.com/tv/dw-mailbag-chatbots-part-1/) covers this around the 2:00 mark.

### Importing the Conversation workspace

From [the IBM Cloud console](https://console.ng.bluemix.net/dashboard/services), click on your
Conversation Service in the list of services, then click the Import icon to
import the file `RoyalValet.json` into the service. Be sure to import everything, including the entities, intents, and dialogs.

Details of importing data into a Conversation Service are in the video [Building chatbots in the IBM Cloud - Part 1](https://developer.ibm.com/tv/dw-mailbag-chatbots-part-1/) around the 9:05 mark.

## The preliminaries

Before you go through the steps in this video, we assume you have a Docker image that contains an app that needs credentials.
If you've followed the video series, you've done the following steps:

1. Built a Docker image from the code in the repo. The repo contains a `Dockerfile` and a `.dockerignore` file to make this easy.
1. Uploaded that Docker image to your IBM Cloud repository.
1. Used the IBM Cloud console to get the credentials for your conversation service.
You'll need the values for `WORKSPACE_ID`, `CONVERSATION_USERNAME`, and `CONVERSATION_PASSWORD`.
1. Used the IBM Cloud console to create a cluster. (If you'd like to continue your
tour of dW Mailbag videos, you can find the cluster creation details around the 1:50 mark of [Building a Kubernetes cluster in the IBM Cloud](https://developer.ibm.com/tv/dw-mailbag-kubernetes-clusters/).)
1. Configured the `kubectl` command to point to your cluster. (If you need to see how to do that, the details are at the 5:45 mark in the [Building a Kubernetes cluster in the IBM Cloud](https://developer.ibm.com/tv/dw-mailbag-kubernetes-clusters/) video.)

## Der plan

Whew. In a nutshell, here's what you'll do:

1. Create a **Kubernetes secret** that contains the credentials of your conversation service. You'll create this
with the `convo-secret.yaml` file.
1. Deploy the Docker image containing your app to your cluster using the `convo-deployment.yaml` file.
1. Do some magic (covered in the video) with the `kubectl` command.
1. Have fun with your chatbot, now running live on the web.
1. Share the URL with your friends and family so they can share your joy.

## License

This sample code is licensed under Apache 2.0.
Full license text is available in [LICENSE](LICENSE).

## Contributing

See [CONTRIBUTING](CONTRIBUTING.md).

## Open Source @ IBM

Find more open source projects on the
[IBM Github Page](http://ibm.github.io/).


[cf_docs]: (https://console.bluemix.net/docs/services/watson/getting-started-cf.html)
[cloud_foundry]: https://github.com/cloudfoundry/cli#downloads
[demo_url]: http://conversation-simple.ng.bluemix.net/
[doc_intents]: (https://console.bluemix.net/docs/services/conversation/intents-entities.html#planning-your-entities)
[docs]: https://console.bluemix.net/docs/services/conversation/index.html
[docs_landing]: (https://console.bluemix.net/docs/services/conversation/index.html)
[node_link]: (http://nodejs.org/)
[npm_link]: (https://www.npmjs.com/)
[sign_up]: bluemix.net/registration
