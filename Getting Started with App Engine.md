<!DOCTYPE html []>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta name="author" content="MarkdownViewer++" />
    <title>Getting Started with App Engine.txt</title>
    <style type="text/css">
            
/* Avoid page breaks inside the most common attributes, especially for exports (i.e. PDF) */
td, h1, h2, h3, h4, h5, p, ul, ol, li {
    page-break-inside: avoid; 
}

        </style>
  </head>
  <body>
    <h1 id="google-cloud-fundamentals-getting-started-with-app-engine">Google Cloud Fundamentals: Getting Started with App Engine</h1>
    <h3 id="objectives">Objectives</h3>
    <p>In this lab, you learn how to perform the following tasks:</p>
    <ul>
      <li>Initialize App Engine.</li>
      <li>Preview an App Engine application running locally in Cloud Shell.</li>
      <li>Deploy an App Engine application, so that others can reach it.</li>
      <li>Disable an App Engine application, when you no longer want it to be visible.</li>
    </ul>
    <h2 id="task-1-initialize-app-engine">Task 1: Initialize App Engine</h2>
    <pre>
      <code>	gcloud init
	gcloud config set account [ACCOUNT]
	gcloud config set project [PROJECT_ID]
	
</code>
    </pre>
    <p>1 Initialize your App Engine app with your project and choose its region:</p>
    <pre>
      <code>	gcloud app create --project=$DEVSHELL_PROJECT_ID
</code>
    </pre>
    <p>2 Clone the source code repository for a sample application in the hello_world directory:</p>
    <pre>
      <code>	git clone https://github.com/GoogleCloudPlatform/python-docs-samples
</code>
    </pre>
    <p>3 Navigate to the source directory:</p>
    <pre>
      <code>	cd python-docs-samples/appengine/standard_python3/hello_world
</code>
    </pre>
    <h2 id="task-2-run-hello-world-application-locally">Task 2: Run Hello World application locally</h2>
    <p>1 Execute the following command to download and update the packages list.</p>
    <pre>
      <code>	sudo apt-get update
</code>
    </pre>
    <p>2 Set up a virtual environment in which you will run your application. Python virtual environments are used to isolate package installations from the system.</p>
    <pre>
      <code>	sudo apt-get install virtualenv
	
If prompted [Y/n], press Y and then Enter.

	virtualenv -p python3 venv
</code>
    </pre>
    <p>3 Activate the virtual environment.</p>
    <pre>
      <code>	source venv/bin/activate
</code>
    </pre>
    <p>4 Navigate to your project directory and install dependencies.</p>
    <pre>
      <code>	pip install  -r requirements.txt
</code>
    </pre>
    <p>5 Run the application:</p>
    <pre>
      <code>	python main.py

Please ignore the warning if any.
</code>
    </pre>
    <p>6 In Cloud Shell, click Web preview (Web Preview) &gt; Preview on port 8080 to preview the application.</p>
    <p>7 To end the test, return to Cloud Shell and press Ctrl+C to abort the deployed service.</p>
    <p>8 Using the Cloud Console, verify that the app is not deployed. In the Cloud Console, on the Navigation menu (Navigation menu), click App Engine &gt; Dashboard.</p>
    <pre>
      <code>	gcloud app instances list
</code>
    </pre>
    <h2 id="task-3-deploy-and-run-hello-world-on-app-engine">Task 3: Deploy and run Hello World on App Engine</h2>
    <p>1 Navigate to the source directory:</p>
    <pre>
      <code>	cd ~/python-docs-samples/appengine/standard_python3/hello_world
</code>
    </pre>
    <p>2 Deploy your Hello World application.</p>
    <pre>
      <code>	gcloud app deploy
	
If prompted "Do you want to continue (Y/n)?", press Y and then Enter.
</code>
    </pre>
    <p>3 Launch your browser to view the app at <a href="http://YOUR_PROJECT_ID.appspot.com">http://YOUR_PROJECT_ID.appspot.com</a></p>
    <pre>
      <code>	gcloud app browse
</code>
    </pre>
    <h2 id="task-4-disable-the-application">Task 4: Disable the application</h2>
    <p>1 In the Cloud Console, on the Navigation menu (Navigation menu), click App Engine &gt; Settings.</p>
    <pre>
      <code>	gcloud app instances list
	gcloud app instances describe --service=s1 --version=v1 i1
</code>
    </pre>
    <p>2 Click Disable application.</p>
    <pre>
      <code>	gcloud app instances delete i1 --service=s1 --version=v1
</code>
    </pre>
    <p>3 Read the dialog message. Enter the App ID and click DISABLE.</p>
    <pre>
      <code>	qwiklabs-gcp-0855e773352d3560
</code>
    </pre>
    <h1 id="congratulations">Congratulations!</h1>
  </body>
</html>
