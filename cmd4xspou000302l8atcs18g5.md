---
title: "Streamlining Your Streamlit App Deployment with Docker"
datePublished: Fri Mar 22 2024 16:48:38 GMT+0000 (Coordinated Universal Time)
cuid: cmd4xspou000302l8atcs18g5
slug: streamlining-your-streamlit-app-deployment-with-docker-0f6aff7bce48
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1752608411082/1440a134-2caa-4676-a272-8990d6f2b62b.png

---

In today’s tech landscape, deploying applications efficiently and reliably is paramount. Docker has emerged as a powerful tool for packaging applications into containers, providing consistency across different environments. Streamlit, on the other hand, has gained popularity for rapidly building and deploying data-driven web apps using Python. Combining Docker with Streamlit offers a streamlined approach to deploying data apps, ensuring consistency and ease of deployment across various platforms. In this article, we’ll explore how to integrate Docker with Streamlit to deploy your apps seamlessly

### Creating a Dockerfile:

First, let’s create a Dockerfile to define the environment for running our Streamlit app.

\# This sets up the container with Python 3.10 installed.  
FROM python:3.10-slim  
  
\# This copies everything in your current directory to the /app directory in the container.  
COPY . /app  
  
\# This sets the /app directory as the working directory for any RUN, CMD, ENTRYPOINT, or COPY instructions that follow.  
WORKDIR /app  
  
\# This runs pip install for all the packages listed in your requirements.txt file.  
RUN pip install -r requirements.txt  
  
\# This tells Docker to listen on port 80 at runtime. Port 80 is the standard port for HTTP.  
EXPOSE 80  
  
\# This command creates a .streamlit directory in the home directory of the container.  
RUN mkdir ~/.streamlit  
  
\# This copies your Streamlit configuration file into the .streamlit directory you just created.  
RUN cp config.toml ~/.streamlit/config.toml  
  
\# Similar to the previous step, this copies your Streamlit credentials file into the .streamlit directory.  
RUN cp credentials.toml ~/.streamlit/credentials.toml  
  
\# This sets the default command for the container to run the app with Streamlit.  
ENTRYPOINT \["streamlit", "run"\]  
  
\# This command tells Streamlit to run your app.py script when the container starts.  
CMD \["app.py"\]

config.toml

\[global\]  
\# If True, will show a warning when you run a Streamlit-enabled script via "python my\_script.py".  
\# Default: true  
showWarningOnDirectExecution = true  
  
\[logger\]  
\# Level of logging: 'error', 'warning', 'info', or 'debug'.  
\# Default: 'info'  
level = "debug"  
  
  
  
\[runner\]  
\# Allows you to type a variable or string by itself in a single line of Python code to write it to the app.  
\# Default: true  
magicEnabled = true  
  
  
  
\[server\]  
\# List of folders that should not be watched for changes. Relative paths will be taken as relative to the current working directory.  
\# Example: \['/home/user1/env', 'relative/path/to/folder'\]  
\# Default: \[\]  
folderWatchBlacklist = \[''\]  
  
\# If false, will attempt to open a browser window on start.  
\# Default: false unless (1) we are on a Linux box where DISPLAY is unset, or (2) server.liveSave is set.  
headless = true  
  
\# Immediately share the app in such a way that enables live monitoring, and post-run analysis.  
\# Default: false  
liveSave = false  
  
\# Automatically rerun script when the file is modified on disk.  
\# Default: false  
runOnSave = false  
  
\# The port where the server will listen for client and browser connections.  
\# Default: 8501  
port = 80  
  
\# Enables support for Cross-Origin Request Sharing, for added security.  
\# Default: true  
enableCORS = false  
  
\[browser\]  
\# Internet address of the server that the browser should connect to. Can be IP address or DNS name.  
\# Default: 'localhost'  
serverAddress = "0.0.0.0"  
  
\# Whether to send usage statistics to Streamlit.  
\# Default: true  
gatherUsageStats = true  
  
\# Port that the browser should use to connect to the server when in liveSave mode.  
\# Default: whatever value is set in server.port.  
serverPort = 80

credentials.toml

\[general\]  
email\=""

#### Building the Docker Image:

Once you have created the Dockerfile and configured your Streamlit app, navigate to the directory containing your Dockerfile and execute the following command to build the Docker image:

docker build -t my\-streamlit-app .

Running the Docker Container: After building the Docker image, you can run the container using the following command:

docker run -p 80:80 my-streamlit-app

Replace `8501` with the desired port on your local machine.

#### Conclusion:

In this tutorial, we’ve learned how to integrate Docker with Streamlit to create a streamlined deployment process for data-driven web apps. By encapsulating our app and its dependencies into a Docker container, we ensure consistency and portability across different environments. This approach simplifies deployment and facilitates scalability, making it easier to share and deploy Streamlit apps with confidence. Streamline your deployment workflow today by leveraging the power of Docker and Streamlit together!