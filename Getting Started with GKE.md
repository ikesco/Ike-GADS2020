<!DOCTYPE html []>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="author" content="MarkdownViewer++" />
    <title>Getting Started with GKE.txt</title>
    <style type="text/css">
            
/* Avoid page breaks inside the most common attributes, especially for exports (i.e. PDF) */
td, h1, h2, h3, h4, h5, p, ul, ol, li {
    page-break-inside: avoid; 
}

        </style>
  </head>
  <body>
    <h1 id="google-cloud-fundamentals-getting-started-with-gke">Google Cloud Fundamentals: Getting Started with GKE</h1>
    <h3 id="objectives">Objectives</h3>
    <p>In this lab, you learn how to perform the following tasks:</p>
    <ul>
      <li>Provision a Kubernetes cluster using Kubernetes Engine.</li>
      <li>Deploy and manage Docker containers using kubectl.</li>
    </ul>
    <h2 id="task-1-sign-in-to-the-google-cloud-platform-gcp-console-sdk">Task 1:  Sign in to the Google Cloud Platform (GCP) Console/ SDK</h2>
    <pre>
      <code>	gcloud init
	gcloud config set account [ACCOUNT]
	gcloud config set project [PROJECT_ID]
</code>
    </pre>
    <p>1 Make sure you signed into Qwiklabs using an incognito window.</p>
    <p>2 Note the lab's access time</p>
    <p>3 When ready, click [start_lab]</p>
    <p>4 Note your lab credentials. You will use them to sign in to Cloud Platform Console.</p>
    <p>5 Click Open Google Console.</p>
    <p>6 Click Use another account and copy/paste credentials for this lab into the prompts.</p>
    <p>7 Accept the terms and skip the recovery resource page.</p>
    <h2 id="task-2-confirm-that-needed-apis-are-enabled">Task 2: Confirm that needed APIs are enabled</h2>
    <p>1 Make a note of the name of your GCP project. This value is shown in the top bar of the Google Cloud Platform Console. It will be of the form qwiklabs-gcp- followed by hexadecimal numbers.</p>
    <p>2 In the GCP Console, on the Navigation menu, click APIs &amp; Services</p>
    <p>3 Scroll down in the list of enabled APIs, and confirm that both of these APIs are enabled:</p>
    <ul>
      <li>
        <p>Kubernetes Engine API</p>
      </li>
      <li>
        <p>Container Registry API</p>
        <pre>
          <code>gcloud services list --enabled
gcloud services enable kubernetes-engine-api container-registry-api
</code>
        </pre>
      </li>
    </ul>
    <h2 id="task-3-start-a-kubernetes-engine-cluster">Task 3: Start a Kubernetes Engine cluster</h2>
    <p>1 In GCP console, on the top right toolbar, click the Open Cloud Shell button</p>
    <p>2 Click Continue</p>
    <p>3 For convenience, place the zone that Qwiklabs assigned you to into an environment variable called MY_ZONE. At the Cloud Shell prompt, type this partial command:</p>
    <pre>
      <code>	export MY_ZONE=us-central1-a
</code>
    </pre>
    <p>4 Start a Kubernetes cluster managed by Kubernetes Engine. Name the cluster webfrontend and configure it to run 2 nodes:</p>
    <pre>
      <code>	gcloud container clusters create webfrontend --zone $MY_ZONE --num-nodes 2
</code>
    </pre>
    <p>5 After the cluster is created, check your installed version of Kubernetes using the kubectl version command:</p>
    <pre>
      <code>	kubectl version
</code>
    </pre>
    <p>6 View your running nodes in the GCP Console. On the Navigation menu, click Compute Engine &gt; VM Instances.</p>
    <pre>
      <code>	gcloud compute instances list
</code>
    </pre>
    <h2 id="task-4-run-and-deploy-a-container">Task 4: Run and deploy a container</h2>
    <p>1 From your Cloud Shell prompt, launch a single instance of the nginx container. (Nginx is a popular web server.)</p>
    <pre>
      <code>	kubectl create deploy nginx --image=nginx:1.17.10
</code>
    </pre>
    <p>2 View the pod running the nginx container:</p>
    <pre>
      <code>	kubectl get pods
</code>
    </pre>
    <p>3 Expose the nginx container to the Internet:</p>
    <pre>
      <code>	kubectl expose deployment nginx --port 80 --type LoadBalancer
</code>
    </pre>
    <p>4 View the new service:</p>
    <pre>
      <code>	kubectl get services
</code>
    </pre>
    <p>5 Open a new web browser tab and paste your cluster's external IP address into the address bar. The default home page of the Nginx browser is displayed.</p>
    <p>6 Scale up the number of pods running on your service:</p>
    <pre>
      <code>	kubectl scale deployment nginx --replicas 3
</code>
    </pre>
    <p>7 Confirm that Kubernetes has updated the number of pods:</p>
    <pre>
      <code>	kubectl get pods
</code>
    </pre>
    <p>8 Confirm that your external IP address has not changed:</p>
    <pre>
      <code>	kubectl get services
</code>
    </pre>
    <p>9 Return to the web browser tab in which you viewed your cluster's external IP address. Refresh the page to confirm that the nginx web server is still responding.</p>
    <h1 id="congratulations">Congratulations!</h1>
  </body>
</html>
