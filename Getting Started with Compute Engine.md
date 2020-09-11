<!DOCTYPE html []>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="author" content="MarkdownViewer++" />
    <title>Getting Started with Compute Engine.txt</title>
    <style type="text/css">
            
/* Avoid page breaks inside the most common attributes, especially for exports (i.e. PDF) */
td, h1, h2, h3, h4, h5, p, ul, ol, li {
    page-break-inside: avoid; 
}

        </style>
  </head>
  <body>
    <h1 id="google-cloud-fundamentals-getting-started-with-compute-engine">Google Cloud Fundamentals: Getting Started with Compute Engine</h1>
    <h3 id="objectives">Objectives</h3>
    <p>In this lab, you will learn how to perform the following tasks:</p>
    <ul>
      <li>Create a Compute Engine virtual machine using the Google Cloud Platform (GCP) Console.</li>
      <li>Create a Compute Engine virtual machine using the gcloud command-line interface.</li>
      <li>Connect between the two instances.</li>
    </ul>
    <h2 id="task-1-sign-in-to-the-google-cloud-platform-gcp-console">Task 1: Sign in to the Google Cloud Platform (GCP) Console</h2>
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
    <h2 id="task-2-create-a-virtual-machine-using-the-gcp-console">Task 2: Create a virtual machine using the GCP Console</h2>
    <p>1 In the Navigation menu, click Compute Engine &gt; VM instances.</p>
    <p>2 Click Create.</p>
    <p>3 On the Create an Instance page, for Name, type my-vm-1</p>
    <p>4 For Region and Zone, select the region and zone assigned by Qwiklabs.</p>
    <p>5 For Machine type, accept the default.</p>
    <p>6 For Boot disk, if the Image shown is not Debian GNU/Linux 9 (stretch), click Change and select Debian GNU/Linux 9 (stretch).</p>
    <p>7 Leave the defaults for Identity and API access unmodified.</p>
    <pre>
      <code>	gcloud compute instances create my-vm-1 --machine-type "n1-standard-1" --image=debian-9-stretch-v20200902 --image-project=debian-cloud --boot-disk-size=10GB --subnet "default" --tags http
</code>
    </pre>
    <p>8 For Firewall, click Allow HTTP traffic.</p>
    <pre>
      <code>	gcloud compute firewall-rules create allow-http --action=Allow --destination=INGRESS --rules=http:80 --target-tags=http
	
</code>
    </pre>
    <p>9 Leave all other defaults unmodified.</p>
    <p>10 To create and launch the VM, click Create.</p>
    <h2 id="task-3-create-a-virtual-machine-using-the-gcloud-command-line">Task 3: Create a virtual machine using the gcloud command line</h2>
    <p>1 In GCP console, on the top right toolbar, click the Open Cloud Shell button.</p>
    <p>2 Click Continue.</p>
    <p>3 To display a list of all the zones in the region to which Qwiklabs assigned you, enter this partial command gcloud compute zones list | grep followed by the region that Qwiklabs or your instructor assigned you to.</p>
    <pre>
      <code>	gcloud compute zones list | grep us-central1
</code>
    </pre>
    <p>4 Choose a zone from that list other than the zone to which Qwiklabs assigned you. For example, if Qwiklabs assigned you to region us-central1 and zone us-central1-a you might choose zone us-central1-b.</p>
    <p>5 To set your default zone to the one you just chose, enter this partial command gcloud config set compute/zone followed by the zone you chose.</p>
    <pre>
      <code>	gcloud config set compute/zone us-central1-b
</code>
    </pre>
    <p>6 To create a VM instance called my-vm-2 in that zone, execute this command:</p>
    <pre>
      <code>	gcloud compute instances create "my-vm-2" --machine-type "n1-standard-1" --image-project "debian-cloud" \
	--image "debian-9-stretch-v20190213" --subnet "default"
</code>
    </pre>
    <p>7 To close the Cloud Shell, execute the following command:</p>
    <h2 id="task-4-connect-between-vm-instances">Task 4: Connect between VM instances</h2>
    <p>1 In the Navigation menu (Navigation menu), click Compute Engine &gt; VM instances.
You will see the two VM instances you created, each in a different zone.</p>
    <pre>
      <code>	gcloud compute instances list
</code>
    </pre>
    <p>Notice that the Internal IP addresses of these two instances share the first three bytes in common. They reside on the same subnet in their Google Cloud VPC even though they are in different zones.</p>
    <p>2 To open a command prompt on the my-vm-2 instance, click SSH in its row in the VM instances list.</p>
    <pre>
      <code>	gcloud compute ssh my-vm-2
</code>
    </pre>
    <p>3 Use the ping command to confirm that my-vm-2 can reach my-vm-1 over the network:</p>
    <pre>
      <code>	ping -c 4 my-vm-1
</code>
    </pre>
    <p>4 Press Ctrl+C to abort the ping command.</p>
    <p>5 Use the ssh command to open a command prompt on my-vm-1:</p>
    <p>6 At the command prompt on my-vm-1, install the Nginx web server:</p>
    <p>7 Use the nano text editor to add a custom message to the home page of the web server:</p>
    <p>8 Use the arrow keys to move the cursor to the line just below the h1 header. Add text like this, and replace YOUR_NAME with your name:</p>
    <p>9 Press Ctrl+O and then press Enter to save your edited file, and then press Ctrl+X to exit the nano text editor.</p>
    <p>10 Confirm that the web server is serving your new page. At the command prompt on my-vm-1, execute this command:</p>
    <p>11 To exit the command prompt on my-vm-1, execute this command:</p>
    <p>12 To confirm that my-vm-2 can reach the web server on my-vm-1, at the command prompt on my-vm-2, execute this command:</p>
    <p>13 In the Navigation menu (Navigation menu), click Compute Engine &gt; VM instances.</p>
    <p>14 Copy the External IP address for my-vm-1 and paste it into the address bar of a new browser tab. You will see your web server's home page, including your custom text.</p>
    <h1 id="congratulations">Congratulations!</h1>
  </body>
</html>
