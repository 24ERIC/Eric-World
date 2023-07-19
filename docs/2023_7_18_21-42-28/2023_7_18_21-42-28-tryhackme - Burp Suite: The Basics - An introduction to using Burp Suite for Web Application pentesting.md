# tryhackme - Burp Suite: The Basics - An introduction to using Burp Suite for Web Application pentesting

- Whilst Burp Community has a relatively limited feature-set compared to the Professional edition, it still has many superb tools available. These include:

    Proxy: The most well-known aspect of Burp Suite, the Burp Proxy allows us to intercept and modify requests/responses when interacting with web applications.
    Repeater: The second most well-known Burp feature -- Repeater -- allows us to capture, modify, then resend the same request numerous times. This feature can be absolutely invaluable, especially when we need to craft a payload through trial and error (e.g. in an SQLi -- Structured Query Language Injection) or when testing the functionality of an endpoint for flaws.
    Intruder: Although harshly rate-limited in Burp Community, Intruder allows us to spray an endpoint with requests. This is often used for bruteforce attacks or to fuzz endpoints.
    Decoder: Though less-used than the previously mentioned features, Decoder still provides a valuable service when transforming data -- either in terms of decoding captured information, or encoding a payload prior to sending it to the target. Whilst there are other services available to do the same job, doing this directly within Burp Suite can be very efficient.
    Comparer: As the name suggests, Comparer allows us to compare two pieces of data at either word or byte level. Again, this is not something that is unique to Burp Suite, but being able to send (potentially very large) pieces of data directly into a comparison tool with a single keyboard shortcut can speed things up considerably.
    Sequencer: We usually use Sequencer when assessing the randomness of tokens such as session cookie values or other supposedly random generated data. If the algorithm is not generating secure random values, then this could open up some devastating avenues for attack.

In addition to the myriad of in-built features, the Java codebase also makes it very easy to write extensions to add to the functionality of the Burp framework. These can be written in Java, Python (using the Java Jython interpreter), or Ruby (using the Java JRuby interpreter). The Burp Suite Extender module can quickly and easily load extensions into the framework, as well as providing a marketplace to download third-party modules (referred to as the "BApp Store"). Whilst many of these extensions require a professional license to download and add in, there are still a fair number that can be integrated with Burp Community. For example, we may wish to extend the inbuilt logging functionality of Burp Suite with the Logger++ module.


- Installation
- Note: The AttackBox already has Burp Suite installed, so please feel free to skip this task if you do not intend to use Burp Suite locally.

Burp Suite is one of those tools that is very useful to have around, whether you're explicitly assessing a web or mobile application for a pentest/bug bounty, or are simply wanting to debug a new feature in a web app you are developing. For this reason, it is important to know how to install Burp Suite on a variety of platforms, rather than just using it inside a pentesting OS such as Kali or Parrot. You never know when you might need it!

Fortunately, PortSwigger have made installing Burp Suite extremely easy on Linux, macOS, and Windows, providing dedicated installers for all three. As a Java application, Burp can also be downloaded as a JAR archive and run on effectively anything that will support a Java runtime environment.

Burp Suite comes pre-packaged with Kali Linux, so you should not need to install it there. If, for some reason, Burp is missing from your Kali installation, you can easily install it from the Kali apt repositories.

For other systems, we can download installers from the Burp Suite Downloads page.

From the dropdown menus, we can select our operating system, as well as whether we want Burp Suite Community or Burp Suite Professional:
The Burp Suite download page giving us the choice between pro and community, as well as to select our operating system. The hashsums for our selection are also shown

We can then click the "Download" button to start downloading the Burp Suite installer. No matter which operating system you are using, make sure to use Burp Suite Community Edition.
Once we have verified the integrity of our download, we can install it in the normal way for our operating system (e.g. Running the executable in Windows or executing the script from the terminal with sudo in Linux).

Note: If installing in Linux, you can choose to install either with or without super-user permissions. If you decide not to use sudo when executing the script, Burp Suite will be installed in your home directory at ~/BurpSuiteCommunity/BurpSuiteCommunity and will not be added to your PATH.

The installation wizard is very intuitive. It is generally safe to accept the suggested defaults, regardless of your operating system; however, it is still sensible to read through the installer carefully.

With Burp Suite installed, we can now start up the application. The first time we use it, Burp Suite will ask us to read and accept its terms and conditions; make sure you do so before accepting or declining them!

With the terms and conditions accepted, we are presented with another menu. We will go through this in the next task.


- The Dashboard 
- 

When we open Burp Suite and have accepted the terms and conditions, we are met with a window asking us to select the project type.

This window doesn't give us many options in Burp Community. Burp Pro would allow us to save our work to the disk or load a previously saved project at this point. All we can do here is click "Next", however.

The next window allows us to choose a configuration for Burp Suite. Leaving this at the default is perfect for most situations:

Click "Start Burp", and the main Burp Suite interface will open!

The first time you open Burp Suite, you may be presented with a screen of training options. These are well worth reading through if you get the time.

If not (and in any subsequent sessions regardless), you will be presented with the slightly daunting Burp Dashboard:

The Burp Suite Dashboard Tab

Don't be alarmed if this doesn't make too much sense just yet -- it soon will!

In short, the Dashboard interface is split into four quadrants:

The four quadrants of the burp dashboard labelled in anti-clockwise order, starting from the top left.

    The Tasks menu allows us to define background tasks that Burp Suite will run whilst we use the application. The Pro version would also allow us to create on-demand scans. The default "Live Passive Crawl" (which automatically logs the pages we visit) will be more than suitable for our uses in this module.
    The Event log tells us what Burp Suite is doing (e.g. starting the Proxy), as well as information about any connections that we are making through Burp.
    The Issue Activity section is exclusive to Burp Pro. It won't give us anything using Burp Community, but in Burp Professional it would list all of the vulnerabilities found by the automated scanner. These would be ranked by severity and filterable by how sure Burp is that the component is vulnerable.
    The Advisory section gives more information about the vulnerabilities found, as well as references and suggested remediations. These could then be exported into a report.
    Clicking on one of the example vulnerabilities in the Issue Activity section gives us an idea of what this looks like:
    The Advisory section showing the example OS Command Injection vulnerability advisories


Throughout the various tabs and windows of Burp Suite, you will find little help icons: a question mark within a circle.

Clicking on these will open a new window containing help for the section, for example:

Screenshot showing the help text for the Dashboard

These are extremely useful if you're ever stuck and don't know what a feature does, so make good use of them!

- Navigation


Navigating around the Burp Suite GUI by default is done entirely using the top menu bars:

The Burp Suite navigation bar showing the sub-tabs available in Burp Proxy

These allow you to switch between modules (along the top row of the attached image). If the selected module has more than one sub-tab, then these can be selected using a second menu bar which appears directly below the original bar (the bottom row of the image above). It is common for module-specific settings to be provided in these sub-tabs (as is the case with the Proxy Options above).

Tabs can also be popped out into separate windows should you prefer to view multiple tabs separately. This can be done by clicking "Window" in the application menu at the top of the screen, then choosing to "Detach" tabs:

Demonstration of the menu allowing you to detach windows

These can be reattached in the same way.

In addition to the menu bar, Burp Suite also has keyboard shortcuts that allow quick navigation to key tabs. By default, these are:
Shortcut
	Does
Ctrl + Shift + D
	Switch to the Dashboard
Ctrl + Shift + T
	Switch to the Target tab
Ctrl + Shift + P
	Switch to the Proxy tab
Ctrl + Shift + I
	Switch to the Intruder tab
Ctrl + Shift + R
	Switch to the Repeater tab

We will look at how we can view and change these in the next task.

- Options


Before we start learning about the Burp Proxy, let's take a look at the options available for configuring Burp Suite.

There are two types of settings: Global Settings (also called User Settings), and Project Settings.

User settings affect the Burp Suite installation as a whole and will be applied every time we start the application. By contrast, Project Settings only apply to the current project. Given that we can't save projects in Burp Suite Community Edition, this effectively means that any project options we set will be lost every time we close Burp.

Many options are provided as both global settings (which are used to set a baseline) and project settings (which can be used to override the equivalent global setting).

Note: The settings system in Burp Suite was recently completely revamped. This task has been updated to use the new version. Please ensure that you are using the latest version of Burp Suite.

The Settings window can be accessed by clicking on the "Settings" button in the top navigation bar:
The top navigation bar with the Settings button highlighted

Clicking this button opens a separate settings window, as shown below:
Burp Suite Settings Window

On the left hand side we have a menu containing options to change the scope between all settings, user settings, and project settings, as well as search for specific settings, or select them by category.

It should be noted that many of the tools in Burp Suite offer shortcuts to specific categories of settings. For example, the Proxy tool includes a "Proxy settings" button which will open the Settings window directly to the section relevant to the proxy.

Screenshot showing the Proxy settings button in the Proxy tab

The Search feature of the settings page is a relatively new addition; however, it is absolutely invaluable, allowing us to search for settings using keywords.

Familiarise yourself with the range of configurable options in Burp Suite, then complete the following exercises.

- 
- 


The Burp Proxy is the most fundamental (and most important!) of the tools available in Burp Suite. It allows us to capture requests and responses between ourselves and our target. These can then be manipulated or sent to other tools for further processing before being allowed to continue to their destination.

For example, if we make a request to https://tryhackme.com through the Burp Proxy, our request will be captured and won't be allowed to continue to the TryHackMe servers until we explicitly allow it through. We can choose to do the same with the response from the server, although this isn't active by default. This ability to intercept requests ultimately means that we can take complete control over our web traffic -- an invaluable ability when it comes to testing web applications.

There are a few configurations we need to make before we can use the proxy, but let's start by looking at the interface.

Note: You do not need to follow along with this task -- just read the information and understand what the Proxy is used for.

When we first open the Proxy tab, Burp gives us a bunch of useful information and background reading. This information is well worth reading through; however, the real magic happens after we capture a request:

Capturing a GET request to TryHackMe with the Burp Proxy

With the proxy active, a request was made to the TryHackMe website. At this point, the browser making the request will hang, and the request will appear in the Proxy tab giving us the view shown in the screenshot above. We can then choose to forward or drop the request (potentially after editing it). We can also do various other things here, such as sending the request to one of the other Burp modules, copying it as a cURL command, saving it to a file, and many others.

When we have finished working with the Proxy, we can click the "Intercept is on" button to disable the Intercept, which will allow requests to pass through the proxy without being stopped.

Burp Suite will still (by default) be logging requests made through the proxy when the intercept is off. This can be very useful for going back and analysing prior requests, even if we didn't specifically capture them when they were made.

Burp will also capture and log WebSocket communication, which, again, can be exceedingly helpful when analysing a web app.

The logs can be viewed by going to the "HTTP history" and "WebSockets history" sub-tabs:
Viewing the logs in the HTTP history sub-tab

It is worth noting that any requests captured here can be sent to other tools in the framework by right-clicking them and choosing "Send to...". For example, we could take a previous HTTP request that has already been proxied to the target and send it to Repeater.

Finally, there are also Proxy specific options, which in the Proxy Settings, accessible by clicking on the "Proxy Settings" button.

These options give us a lot of control over how the proxy operates, so it is an excellent idea to familiarise yourself with these.

For example, the proxy will not intercept server responses by default unless we explicitly ask it to on a per-request basis. We can override the default setting by selecting the "Intercept responses based on the following rules" checkbox and picking one or more rules. The "Or Request Was Intercepted" rule is good for catching responses to all requests that were intercepted by the proxy:
Screenshot showing the response interception rules in Proxy Settings

The "And URL Is in target scope" is another very good default rule; we will look at scoping later in this room.

You can make your own rules for most of the Proxy options, so this is one section where looking around and experimenting will serve you very well indeed!

Another particularly useful section of this sub-tab is the "Match and Replace" section; this allows you to perform regexes on incoming and outgoing requests. For example, you can automatically change your user agent to emulate a different web browser in outgoing requests or remove all cookies being set in incoming requests. Again, you are free to make your own rules here.


You've seen the theory; now it's time to start using the proxy for yourself.

There are two ways to proxy our traffic through Burp Suite.

    We could use the embedded browser (we will cover this in a later task).
    We can configure our local web browser to proxy our traffic through Burp; this is more common and so will be the focus of this task.

The Burp Proxy works by opening a web interface on 127.0.0.1:8080 (by default). As implied by the fact that this is a "proxy", we need to redirect all of our browser traffic through this port before we can start intercepting it with Burp. We can do this by altering our browser settings or, more commonly, by using a Firefox browser extension called FoxyProxy. FoxyProxy allows us to save proxy profiles, meaning we can quickly and easily switch to our "Burp Suite" profile in a matter of clicks, then disable the proxy just as easily.

Note: All instructions will be given with Firefox in mind, as this is the default browser for both Kali Linux and the TryHackMe AttackBox. If you are using another browser locally then you are advised to use the AttackBox, or you may otherwise need to find alternative methods to those presented in this task. If you can't get the proxy working in your local browser and do not want to use the AttackBox, then you may wish to skip ahead to the Burp Suite Browser task.

There are two versions of FoxyProxy: Basic and Standard. Both versions allow you to change your proxy settings on the fly; however, FoxyProxy Standard gives you a lot more control over what traffic gets sent through the proxy. For example, it will allow you to set pattern matching rules to determine whether a request should be proxied or not: this is more complicated than the simple proxy offered by FoxyProxy basic.

The basic edition is more than adequate for our usage. It is pre-installed and configured in the Firefox browser of the AttackBox, so if you are using the AttackBox, please feel free to skip ahead to the last section of this task.

If you are using your own machine, you can download FoxyProxy Basic here.

Once installed, a button should appear at the top right of the screen which allows you to access your proxy configurations:
FoxyProxy button at the top right of the screen highlighted

There are no default configurations, so let's click on the "Options" button to create our Burp Proxy config.

This will open a new browser tab with the FoxyProxy options page:
Screenshot showing the FoxyProxy options page with the Add button circled. There are currently no configs

Click on the "Add" button and fill in the following values:

    Title: Burp (or anything else you prefer)
    Proxy IP: 127.0.0.1
    Port: 8080

Screenshot showing the three fields of the Add Proxy screen filled in as per the list above

Now click "Save".

When you click on the FoxyProxy icon at the top of the screen, you will see that that there is a configuration available for Burp:
Screenshot of the Burp Config in FoxyProxy

If we click on the "Burp" config, our browser will start directing all of our traffic through 127.0.0.1:8080. Be warned: if Burp Suite is not running, your browser will not be able to make any requests when this config is activated!

Activate this config now -- the icon in the menu should change to indicate that we have a proxy running:
The FoxyProxy icon when we have a proxy selected

Next, switch over to Burp Suite and make sure the Intercept is On:
Screenshot showing the intercept button in Burp Proxy

Now, try accessing the homepage for http://MACHINE_IP/ in Firefox. Your browser should hang, and your proxy will populate with the request headers.

Congratulations, you just intercepted your first request!

From here, you can choose to forward or drop the request. Alternatively, you could send it to another tool or perform any number of other actions by right-clicking on the request and selecting an option from the right-click menu.

Remember: Whilst you are connected to the proxy and have the Proxy Intercept switched on, your browser will hang whenever you make a request. A very common mistake when you are learning to use Burp Suite (and indeed, later on!) is to accidentally leave the intercept switched on and ergo be unable to make any web requests through your browser. If your browser is hanging and you don't know why: check your proxy!



ote: The AttackBox is already configured to solve the problem posed in this task. If you are using the AttackBox and don't wish to read through the information here, you can skip to the next task.

Great, so we can intercept HTTP traffic -- what's next?

Unfortunately, there's a problem. What happens if we navigate to a site with TLS enabled? For example, https://google.com/:
Screenshot showing the FireFox HSTS warning message about the Portswigger CA cert not being trusted

We get an error.

Specifically, Firefox is telling us that the Portswigger Certificate Authority (CA) isn't authorised to secure the connection.

Fortunately, Burp offers us an easy way around this. We need to get Firefox to trust connections secured by Portswigger certs, so we will manually add the CA certificate to our list of trusted certificate authorities.

First, with the proxy activated head to http://burp/cert; this will download a file called cacert.der -- save it somewhere on your machine.

Next, type about:preferences into your Firefox search bar and press enter; this takes us to the FireFox settings page. Search the page for "certificates" and we find the option to "View Certificates":
FireFox certificate settings

Clicking the "View Certificates" button allows us to see all of our trusted CA certificates. We can register a new certificate for Portswigger by pressing "Import" and selecting the file that we just downloaded.

In the menu that pops up, select "Trust this CA to identify websites", then click Ok:

We should now be free to visit any TLS enabled sites that we wish!

The following video shows the full import process:



If the last few tasks seemed overly complex, rest assured, this topic will be a lot simpler.

In addition to giving us the option to modify our regular web browser to work with the proxy, Burp Suite also includes a built-in Chromium browser that is pre-configured to use the proxy without any of the modifications we just had to do.

Whilst this may seem ideal, it is not as commonly used as the process detailed in the previous few tasks. People tend to stick with their own browser as it gives them a lot more customisability; however, both are perfectly valid choices.

We can start the Burp Browser with the "Open Browser" button in the proxy tab:
Open Browser button in the Proxy tab highlighted

A Chromium window will now pop up. Any requests we make in this will go through the proxy.

Note: There are many settings to do with the Burp Browser in the Project options and User options tabs -- make sure to go look at them!

If we are running on Linux as the root user (as we are with the AttackBox), Burp Suite is unable to create a sandbox environment to start the Burp Browser in, causing it to throw an error and die:

The Burp Browser Error indicating that our current configuration can't run without a sandbox

There are two simple solutions to this:

    The smart option: We could create a new user and run Burp Suite under a low privilege account.
    The easy option: We could go to Project options -> Misc -> Embedded Browser and check the  Allow the embedded browser to run without a sandbox option. Checking this option will allow the browser to start, but be aware that it is disabled by default for security reasons: if we get compromised using the browser, then an attacker will have access to our entire machine. On the training environment of the AttackBox this is unlikely (and isn't a huge issue even if it does happen), but keep it in mind if you try this on a local installation of Burp Suite.

Be aware that you will need to do this if using the embedded browser on the AttackBox.


Finally, we come to one of the most important parts of using the Burp Proxy: Scoping.

It can get extremely tedious having Burp capturing all of our traffic. When it logs everything (including traffic to sites we aren't targeting), it muddies up logs we may later wish to send to clients. In short, allowing Burp to capture everything can quickly become a massive pain.

What's the solution? Scoping.

Setting a scope for the project allows us to define what gets proxied and logged. We can restrict Burp Suite to only target the web application(s) that we want to test. The easiest way to do this is by switching over to the "Target" tab, right-clicking our target from our list on the left, then choosing "Add To Scope". Burp will then ask us whether we want to stop logging anything which isn't in scope -- most of the time we want to choose "yes" here.
GIF showing the process described above

We can now check our scope by switching to the "Scope" sub-tab (as shown in the GIF above).

The Scope Settings window allows us to control what we are targeting by either Including or Excluding domains / IPs. This is a very powerful section, so it's well worth taking the time to get accustomed to using it.
We just chose to disable logging for out of scope traffic, but the proxy will still be intercepting everything. To turn this off, we need to go into the Proxy Options sub-tab and select "And URL Is in target scope" from the Intercept Client Requests section:

Screenshot circling the Intercept in Scope requests only setting

With this option selected, the proxy will completely ignore anything that isn't in the scope, vastly cleaning up the traffic coming through Burp.




Control of the scope may be the most useful aspect of the Target tab, but it's by no means the only use for this section of Burp.

There are three sub-tabs under Target:

    Site map allows us to map out the apps we are targeting in a tree structure. Every page that we visit will show up here, allowing us to automatically generate a site map for the target simply by browsing around the web app. Burp Pro would also allow us to spider the targets automatically (i.e. look through every page for links and use them to map out as much of the site as-is publicly accessible using the links between pages); however, with Burp Community, we can still use this to accumulate data whilst we perform our initial enumeration steps.
    The Site map can be especially useful if we want to map out an API, as whenever we visit a page, any API endpoints that the page retrieves data from whilst loading will show up here.
    Scope Settings: We have already seen the Scope Settings window — it allows us to control Burp's target scope for the project.
    Issue Definitions: Whilst we don't have access to the Burp Suite vulnerability scanner in Burp Community, we do still have access to a list of all the vulnerabilities it looks for. The Issue Definitions section gives us a huge list of web vulnerabilities (complete with descriptions and references) which we can draw from should we need citations for a report or help describing a vulnerability.




Having looked at how to set up and configure our proxy, let's go through a simplified real-world example.

We will start by taking a look at the support form at http://MACHINE_IP/ticket/:
Screenshot of the support form at /ticket/

In a real-world web app pentest, we would test this for a variety of things: one of which would be Cross-Site Scripting (or XSS). If you have not yet encountered XSS, it can be thought of as injecting a client-side script (usually in Javascript) into a webpage in such a way that it executes. There are various kinds of XSS -- the type that we are using here is referred to as "Reflected" XSS as it only affects the person making the web request.

Let's begin.
Answer the questions below

Try typing: <script>alert("Succ3ssful XSS")</script>, into the "Contact Email" field. You should find that there is a client-side filter in place which prevents you from adding any special characters that aren't allowed in email addresses:




We have now reached the end of the Burp Basics room.

This room has hopefully given you a good grasp of the Burp Suite interface and configuration options, as well as giving you a working knowledge of the Burp Proxy.

You are advised to experiment with these foundations until you are completely comfortable with them. Burp Suite is an invaluable tool in a web or mobile application pentester's arsenal. We will be building on these skills in the next room of the module covering Burp Suite Repeater.


