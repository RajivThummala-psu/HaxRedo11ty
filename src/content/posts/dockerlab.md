---
title: Generating a Docker File for your NASA Image Search Repo

order: 1
---
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/t2kuu6bmcqr4975els0h.png" alt="Image description"></p>
<p>First started in 2013, Docker is a set of platform as a service products that leverage OS-level virtualization to deliver software in containers. </p>
<p>Containers make it easy to put new versions of software, with new business features, into production quickly-and to quickly roll back to a previous version if you need to. A form of virtualization, one single container can be utilized to run anything from a small microservice or software process to a larger application. Inside a container are all the necessary executables, binary code, libraries, and configuration files. Thus, docker is so powerful due to its ability to facilitate the microservice deployment process by leveraging containers to run across different computing environments. </p>
<hr>
<p>To begin, lets ensure that you have a rudimentary understanding of how docker functions. Please run through <a href="https://www.docker.com/play-with-docker">this tutorial</a> if you are not familiar with docker. </p>
<p>If you are not running through the tutorial, ensure that you have your own server through Docker. If you are stuck on this, please run through the aforementioned tutorial. </p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/uxuec84i6jwn9ka0ltkq.png" alt="Your screen should like like this"></p>
<p>The NASA Image Search Repository already has some adequate functionality. Leveraging microservices, the application can be deployed in a non-taxing way that does not increase in complexity as it is transferred between computing environments. However, there is one way to optimize this deployment: containers. Docker will help us integrate our microservices into containers and will consequently avoid becoming a monolithic application. </p>
<p><strong>Setup</strong></p>
<p>Create ADD NEW INSTANCE in the Docker Playground. Run the following command in the new instance console.
<code>git clone <a href="https://github.com/IST402-Group-E/ip">https://github.com/IST402-Group-E/ip</a> project/blob/master/src/Nasa.js &amp;&amp; cd Nasa.js</code></p>
<p><strong>Configure</strong></p>
<p>Before we ran any Docker commands, we need to configure our custom settings for this application. These settings will be an API key and the url of your Play With Docker instance.</p>
<p>Run the following command to set up a fresh copy of your environment settings.</p>
<p><code>cp dot.env.example dot.env</code></p>
<p>What we just done is created a new file called dot.env. Following the configuration as code principle, we are going to add our applications custom settings via environment variables. Docker relies on this pattern to ensure the application thats running inside of it is stateless.</p>
<p>Now we need to populate those settings.</p>
<p>Select the EDITOR button in your docker lab (it is to the right of the orange DELETE button)</p>
<p>Now we need to obtain our api key, which will be our unique password for requesting a new query. Head over to api.nasa.gov to signup and generate an api key for NASA Image search. </p>
<p>Obtain this key and then insert it into dot.env (replace it with XXXXXXX)</p>
<p>Now select open port in docker
Type 4000 into the prompt and click &quot;Ok&quot;.</p>
<p>You should see a new page that is blank since there is no running application yet. COPY the url that blank page. That&#39;s were our server will be accessible when we get this thing running.</p>
<p>Now that we have the public url we can add it to our dot.env and click &quot;Save&quot;</p>
<p>Now just head over to docker and start up the application</p>
<p>Run the following command in your terminal: docker-compose-up. Select port 80 to view our application!</p>
