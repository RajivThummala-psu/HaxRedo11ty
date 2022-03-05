<p>Upon dipping your feet into the behemoth that is web development, you will quickly realize how non-static this field is. Everything is constantly changing and evolving, from updates to web protocols to constant syntax alterations. Consequently, a 1337 developer must periodically update their toolkit with the new fads and revolutions within the industry. </p>
<p>With a sector that is never static, it is vital that the fundamentals of web development are mastered to provide a base in expanding a developer&#39;s toolkit. Perhaps one of the most important fundamentals to grasp is the basics of JavaScript. As adumbrated by tutorialspoint:</p>
<blockquote>
<p>Javascript is the most popular programming language in the world and that makes it a programmer’s great choice. Once you learnt Javascript, it helps you developing great front-end as well as back-end softwares using different Javascript based frameworks like jQuery, Node.JS etc. Javascript is everywhere, it comes installed on every modern web browser and so to learn Javascript you really do not need any special environment setup. For example Chrome, Mozilla Firefox , Safari and every browser you know as of today, supports Javascript.Javascript helps you create really beautiful and crazy fast websites. You can develop your website with a console like look and feel and give your users the best Graphical User Experience.</p>
</blockquote>
<p>This article will provide a beginners perspective on how to begin to interact with JavaScript and will facilitate the setup process to begin exploring the language. </p>
<p><strong>NodeJS &amp; NPM</strong></p>
<p>Our first journey together in the world of JavaScript will begin by installing a software named &quot;NodeJS&quot;. What exactly is NodeJS?</p>
<blockquote>
<p>In simple terms, it’s a JavaScript free and open source cross-platform for server-side programming that allows users to build network applications quickly. <a href="https://medium.com/@LindaVivah/the-beginners-guide-understanding-node-js-express-js-fundamentals-e15493462be1">Click here to learn more about NodeJS</a></p>
</blockquote>
<p>Follow the listed steps closely and don&#39;t hesitate to scour the internet further to diagnose any challenges you encounter. </p>
<p><strong>1)</strong> Head over to <a href="https://nodejs.org/en/"></a> and select the big green button on the left that reads LTS. In my case, the version is 16.13.2 LTS. </p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/acy4bjyhnybk6x2ujpqc.png" alt="Image description"></p>
<p>Once you finish downloading, proceed to the next step. </p>
<p><strong>2)</strong> Next, hold the windows key + R and type &quot;cmd&quot; in the run box that pops up. You can also type &quot;command prompt&quot; into the search bar in your computer if you prefer. This should open up a black box. This is called the terminal or command prompt. </p>
<p>Type node-v into your terminal. This will be used to check what version of NodeJS you have downloaded. Moreover, it will be used to check if you have actually downloaded NodeJS. </p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/evw47bt1u8jvcv3c1gju.png" alt="You should get something like this"></p>
<p>You should have something like this. The number following the &quot;v&quot; is your version number. (Don&#39;t worry if it is different than what I have you may proceed to the next step). If you are encountering issues, head over to YouTube to search for a NodeJS download tutorial.</p>
<p><strong>3)</strong> Next we are going to make sure that npm downloaded correctly. Npm is a package manner that JavaScript leverages to facilitate the runtime environment. </p>
<p>Run the command npm-v to see what version of npm you have downloaded. Again, the same thing applies here. Don&#39;t worry if the numbers following the v are different than the following image. This indicates your version number. If you do not have npm installed, try running the following commmand in your terminal:</p>
<p>npm install -g npm</p>
<p>If you are still running into trouble, head over to YouTube to search for installation tutorials for npm. </p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/10lhy60b79hxkwxj0bpb.png" alt="Image description"></p>
<p><strong>Installing ohmyzsh</strong>
Next we will work on installing ohmyzsh. Zsh will aid tremendously in operating the terminal. Head over to <a href="https://dev.to/vsalbuq/how-to-install-oh-my-zsh-on-windows-10-home-edition-49g2"></a> for any extra explanations on the following steps. </p>
<p>1) To start, type &quot;windows powershell&quot; into the search bar in your computer. </p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/x93a14lwcckpj4s8thw6.png" alt="Image description"></p>
<p>Select &quot;run as administrator&quot; as depicted in the image. If you do not have windows powershell, I would advise downloading it from the Microsoft Store. Otherwise, you can try running the following steps from your regular terminal/command prompt. </p>
<p>2) Run the following command in windows powershell: </p>
<p>dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart</p>
<p>3) This leads us into our next step which is to install debian. Head over to the microsoft store on your windows machine and search for &quot;debian&quot;. Install the application as depicted in the following image. 
<img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/dbo1mhm13bqdtpfin1yh.png" alt="Image description"></p>
<p>4) Next open up debian either through the microsoft store or by searching for it in the search bar. </p>
<p>Run the following commands in order. </p>
<p>$ sudo apt-get update
$ sudo apt-get upgrade
$ sudo apt-get install zsh
$ zsh
$ sudo apt-get install curl
sh -c &quot;$(curl -fsSL <a href="https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh">https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh</a>)&quot;</p>
<p>5) Restart debian and make sure that you see .zsh somewhere in the terminal. This lets you know that you have installed zsh correctly. </p>
<p>6) Next we will be installing the node within zsh. </p>
<p>Understanding how Node works and its primary function is important. As referenced on medium.com, </p>
<blockquote>
<p>Node allows you to execute Javascript code outside of the browser, in a computing environment (such as a server or local development environment) rather then a browser environment.</p>
</blockquote>
<p>In laymans terms, node essentially enables an individual to execute their code in a sandbox environment. (Without causing any real damage). Think of it like practicing an idea for a painting on a sheet of printer paper before starting on the canvas. </p>
<p>Run the following command:</p>
<p>$ sudo apt-get install build-essential</p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/u91t9kbyz8ik6mtt095g.png" alt="Image description"></p>
<p>7) Run the following command:</p>
<p>curl -o- <a href="https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh">https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.3/install.sh</a> | bash</p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/sxhwjmcpojq8nhm0y0x4.png" alt="Image description"></p>
<p>8) Make sure that you have VSCODE installed before you proceed. If you do not have vscode installed, follow the steps linked in this video and then come back. --&gt; <a href="https://www.youtube.com/watch?v=V3o57MU5eoE"></a> </p>
<p>Run the following command:</p>
<p>code ~/.zshrc</p>
<p>This will open up vscode with a file. Click on the .zshrc tab and paste the following code after the last line. </p>
<p>export NVM_DIR=&quot;$HOME/.nvm&quot;
[ -s &quot;$NVM_DIR/nvm.sh&quot; ] &amp;&amp; . &quot;$NVM_DIR/nvm.sh&quot;</p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/sew4kw6zxfohtk9usi9g.png" alt="Image description"></p>
<p>Save the VSCODE file (Ctrl + S), then exit VSCODE. </p>
<p>9) Open up debian and run the following command:</p>
<p>nvm install --lts
<img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/k6w7p1c72fsyxrm9bqhd.png" alt="Image description"></p>
<p>Next run this command: nvm use --lts</p>
<p>Nice Work! </p>
<p><strong>Starting with open-wc</strong></p>
<p>Now we will take our first dive into working with open-wc. </p>
<p>1) Before we get started, you will need to create your github account and a repository. Follow the steps in this <a href="https://www.youtube.com/watch?v=QUtk-Uuq9nE">video </a>then proceed to the next step. </p>
<p>2) Next, you will need to establish a secure, SSH key based handshake with github. Follow the steps in this <a href="https://docs.github.com/en/authentication/connecting-to-github-with-ssh">article </a> to complete this task, then proceed to the next step. </p>
<p>3) Open your terminal (windows key  + r --&gt; type in cmd in run box). Next you will need to navigate your github repo that you created. </p>
<p>Find your github repo in your file explorer and right click the file to copy the path to your clipboard. </p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/wphs8dkl3icm74w31mcl.png" alt="Image description"></p>
<p>In your terminal, type cd then paste in the file path. 
This should change your directory to your github repo that you created. </p>
<p>4) In the terminal type npm init @open-wc. Wait for the terminal to complete its processing. </p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/mcf0ai8ykt9xqxhdoqtn.png" alt="Image description"></p>
<p>5) You should now see a gui that prompts you with some options. 
Navigate through the UI to select the following options:</p>
<p>What would you like to do today? &gt;&gt; Scaffold a new project
What would you like to scaffold?&gt;&gt; Web Component
What would you like to add <em>(just click enter)</em> &gt;&gt; 
Would you like to use typescript? &gt;&gt; No</p>
<p><em>for the following option, replace what follows hello-world with whatever you would like </em></p>
<p>What is the tagname of your web component &gt;&gt; hello-world_RajivLab1</p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/7nm9jm448nhcgl6ojvj2.png" alt="Image description"></p>
<p>Write the file to disk and install dependencies. </p>
<p>6) Follow the instructions in the terminal. 
Change the directory to your web component and then run the following command:</p>
<p>npm run start </p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/9lecqublj3pv5k8y0b2m.png" alt="Image description"></p>
<p>7) A browser should pop up with localhost in the address. Right click this page and click &quot;view page source&quot;</p>
<p><img src="https://dev-to-uploads.s3.amazonaws.com/uploads/articles/u1r3y5j4itpiqyf63zca.png" alt="Image description"></p>
<p>You now have access to the source code of this page. </p>
<p>8) Now lets go ahead and begin to decipher what this code is asking of us. Right click and select &quot;Save as&quot; to download the page. </p>
<p>9) Drag this downloaded file into vscode so that we can comment on the file and start to decipher what the code is doing.</p>
<p>If this is your first time with JavaScript, start by copy and pasting each line of code into google to try and make sense of it. Leave a comment by typing //your_comment_goes_here to annotate what you believe the code is doing. </p>
<p>This <a href="https://lit.dev/playground/#sample=examples/full-component">article </a>will help.    </p>
<hr>
<p>You can access my first ever interaction with this code snippet on my Github which is linked <a href="https://github.com/RajivThummala-psu/ist402_lab1/blob/main/localhost.htm">here</a>. Thank you for reading this article and I wish you good luck on the rest of your JavaScript journey. </p>
