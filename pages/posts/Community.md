<p>This will be a brief synopsis and run through on how latitude and longitude coordinates can be detected via GeoIP. Particularly, by feeding IP addresses into the GeoIP API. You can follow along with my <a href="https://github.com/RajivThummala-psu/ip-project/blob/master/src/LocationFromIP.js">github repo</a>. </p>
<p>Before we get started, let&#39;s import the necessary dependencies within your project. Since we are going to be wiring up the data to a wikipedia-query tag, we will need to import the following dependency: @lrnwebcomponents/wikipedia-query/wikipedia-query.js</p>
<p><em>Make sure you are using the right syntax</em></p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/r8ycv2suy22w095bxten.png" alt="Image description"></p>
<p>To complete the setup process we will also need to do npm install @lrnwebcomponents/wikipedia-query</p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/csmpiw6tqrlsky52cf0y.png" alt="Image description"></p>
<p>As you parse through the constructor repo, you will notice that the first API you run into is: <strong><a href="https://freegeoip.app/json/">https://freegeoip.app/json/</a></strong></p>
<p>This is the GeoIP API. Unfortunately, at the time of this writing, the server is down so I am unable to provide an overview of all the services this API offers in particular. However, you can head over to this link to poke around. </p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/vyob9fdinxuv9lscbl5k.png" alt="Image description"></p>
<p><strong>Deciphering the GeoIP API?</strong>
<img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/s433cvg4apylswqwr78k.png" alt="Image description"></p>
<p>You will notice that the geoip is set to the locationEndpoint. </p>
<p>An endpoint, as adumbrated by <a href="https://smartbear.com/learn/performance-monitoring/api-endpoints/#:~:text=Each%20endpoint%20is%20the%20location,to%20carry%20out%20their%20function.&amp;text=The%20place%20that%20APIs%20send,lives%2C%20is%20called%20an%20endpoint.">smartbear.com</a>, enables  </p>
<blockquote>
<p>APIs to transfer vital information, processes, transactions, and more. API usage will only increase as time goes on, and making sure that each touchpoint in API communication is intact is vital to the success of each API. Endpoints specify where resources can be accessed by APIs and play a key role in guaranteeing the correct functioning of the software that interacts with it.  In short, API performance relies on its ability to communicate effectively with API Endpoints.</p>
</blockquote>
<p>Thus, this will serve as an endpoint in which the GeoAPI will retrieve information regarding the client&#39;s location to carry out an operation. </p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fcs1fkmabm1x55j3lrhg.png" alt="Image description"></p>
<p>You will also notice that GeoIP is referenced in the async getGeoIPData() method. Let&#39;s take some time to pick apart what is going on here.</p>
<p>`async getGEOIPData() {
    const IPClass = new UserIP();
    const userIPData = await IPClass.updateUserIP();
    return fetch(this.locationEndpoint + userIPData.ip)
      .then(resp =&gt; {
        if (resp.ok) {
          return resp.json();
        }
        return false;
      })
      .then(data =&gt; {</p>
<pre><code>    console.log(<span class="hljs-keyword">data</span>);
    <span class="hljs-keyword">this</span>.state = <span class="hljs-keyword">data</span>.region_name; <span class="hljs-comment">//avoided making the same mistake as last time (reminder --&gt; region name)</span>
    <span class="hljs-keyword">this</span>.city = <span class="hljs-keyword">data</span>.city;
    <span class="hljs-keyword">this</span>.location = `${<span class="hljs-keyword">data</span>.city}, ${<span class="hljs-keyword">data</span>.state}`;
    <span class="hljs-keyword">this</span>.lat = <span class="hljs-keyword">data</span>.latitude; 
    <span class="hljs-keyword">this</span>.long = <span class="hljs-keyword">data</span>.longitude;

    console.log(`Your coordinates: ${<span class="hljs-keyword">this</span>.lat} ${<span class="hljs-keyword">this</span>.long}`);
    <span class="hljs-keyword">return</span> <span class="hljs-keyword">data</span>;
  });`
</code></pre><p>To make it easier, lets split this up into 2 parts to get a better understanding: Obtain information from the API &amp; Feed into LitElement based web component to provide stateful updating of the DOM</p>
<p><strong>Obtain information from the API</strong></p>
<p>Lets begin by taking a look at this segment:</p>
<p><code>async getGEOIPData() {
    const IPClass = new UserIP();
    const userIPData = await IPClass.updateUserIP();
    return fetch(this.locationEndpoint + userIPData.ip)
      .then(resp =&gt; {
        if (resp.ok) {
          return resp.json();
        }
        return false;
      })</code></p>
<p>The fetch command in particular should strike you as new if you have not worked with this language much. It was for me atleast. However, you will quickly learn from a google search that it works similar to the throw and catch commands from java. </p>
<p>What is happening here is that the program is essentially throwing out a mandatory request for the program to provide information regarding the location endpoint, which we instantiated in the constructor. If the program does not get a response, it will catch it (through returning false in this case). As stated earlier, the location endpoint serves as a checkpoint for the API to retrieve information regarding the client&#39;s location. </p>
<p>What you will notice also is that &quot;userIPData.ip&quot; is also being fetched. Lets take a look at this further. You can follow along in my repo if that is easier!</p>
<p>`async updateUserIP() {
    return fetch(this.ipLookUp)
      .then(resp =&gt; {
        if (resp.ok) {
          return resp.json();
        }
        return false;
      })
      .then(data =&gt; {
        this.ip = data.ip;
        this.cityYouAreIn = data.city;
        this.countryYouAreIn = data.country;</p>
<pre><code>    <span class="hljs-keyword">this</span>.location = `${<span class="hljs-keyword">data</span>.city}, ${<span class="hljs-keyword">data</span>.country}`;

    <span class="hljs-comment">// this.location = "Your location is: " + data.cityYouAreIn+ ", " + data.countryYouAreIn; //understood that the data. references the getproperties method</span>
    <span class="hljs-keyword">return</span> <span class="hljs-keyword">data</span>;
  });
</code></pre><p>  }`</p>
<p>We will notice here that the updateUserIP method is being used to retrieve information regarding the user&#39;s ip address and listing readable info regarding their whereabouts (city &amp; country). It is also fetching ipLookUP (<a href="https://ip-fast.com/api/ip/?format=json&amp;location=True">https://ip-fast.com/api/ip/?format=json&amp;location=True</a>), which can be found in the constructor in this file. </p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/oa1uuy43jdvn5qx14amy.png" alt="Image description"></p>
<p>ipLookup references an API called ip-fast. ip-fast is an API that analyzes the client&#39;s network activity to approximate their location. In case of error, it will return false to catch. </p>
<p>Both of these API&#39;s are thus added together to obtain the geoIPdata. Therefore, what we essentially have here in the async getGEOIPData() method enables us to leverage 2 APIs to retrieve the information that we need. But what do we do now that the data has been fetched?</p>
<p><strong>Feed into LitElement based web component to provide stateful updating of the DOM</strong></p>
<p>`  })
      .then(data =&gt; {</p>
<pre><code>    <span class="hljs-keyword">this</span>.state = <span class="hljs-keyword">data</span>.region_name; <span class="hljs-comment">//avoided making the same mistake as last time (reminder --&gt; region name)</span>
    <span class="hljs-keyword">this</span>.city = <span class="hljs-keyword">data</span>.city;
    <span class="hljs-keyword">this</span>.location = `${<span class="hljs-keyword">data</span>.city}, ${<span class="hljs-keyword">data</span>.state}`;
    <span class="hljs-keyword">this</span>.lat = <span class="hljs-keyword">data</span>.latitude; 
    <span class="hljs-keyword">this</span>.long = <span class="hljs-keyword">data</span>.longitude;

    console.log(`Your coordinates: ${<span class="hljs-keyword">this</span>.lat} ${<span class="hljs-keyword">this</span>.long}`);
    <span class="hljs-keyword">return</span> <span class="hljs-keyword">data</span>;
  });`
</code></pre><p>Now if we take a look at this second half of the method, we will notice that the data is actually being entered into the console for use. When I first ran into this section of the program, I actually found it quite easy to interpret despite being unfamiliar with this syntax. </p>
<p>We start of with &quot;then the data&quot;...</p>
<p>Is used to retrieve information regarding the client&#39;s state. You must call for state through region_name as opposed to just data.state (don&#39;t make the same mistake I did). Next you can see that the city and location are retrieved. We also add both latitude and longitude into our instances so that we can obtain the geographical coordinates. Ensure that you are doing data.latitude and data.longitude NOT data.lat and data.long. </p>
<p>These instances are then simply fed into the console.</p>
<p><code>console.log(</code>Your coordinates: ${this.lat} ${this.long}<code>);
        return data;</code></p>
<p>From here, all you have to do is render. I referenced <a href="https://codepen.io/btopro/pen/yLNmVbw">btopro&#39;s codepen</a> to do this, as you can see in my repo. </p>
<p>After copious efforts getting all the bugs out of my code, I am close to getting an accurate solution. I will continue to update the repo as I optimize the program.</p>
<p>As you can see, leveraging public API&#39;s to perform functions are seamless and potent. There are a multitude of micro services across the web that can be utilized to achieve a goal in a non-taxing manner. </p>
<p>NASA Rendering in particular is a great one, which provides the ability to render images from NASA by leveraging their <a href="https://api.nasa.gov/api.html#apod">public api</a>. This enables individuals that are not affiliated with NASA to easily access this large stack of information with ease. </p>
<p>As highlighted by <a href="https://wilsjame.github.io/how-to-nasa/">wilsjame</a>, these are just some of the <a href="https://api.nasa.gov/api.html#apod">many APIs</a> that can be used: </p>
<ul>
<li><p>Near Earth Object Web Service (NeoWs): Access to near Earth asteroid information.</p>
</li>
<li><p>Earth Polychromatic Imaging Camera (EPIC): Full disc imagery of the Earth.</p>
</li>
<li><p>Earth Observatory Natural Event Tracker (EONET): Prototype web service providing continuously updated natural event metadata, such as storm imagery, gathered from the Earth’s surface.
NASA Image and Video Library: Access to the NASA Image and Video Library.</p>
</li>
<li><p>Sounds (beta): Access to space sounds via SoundClound with some of the hassle abstracted away.</p>
</li>
<li><p>NASA rendering; render images from NASA using their public API to render the data</p>
</li>
</ul>
<p>Good luck on your attempt and I thank you for taking your time to read this post. </p>

