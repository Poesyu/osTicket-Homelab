# osTicket-Homelab

<h2>Description</h2>
Fill in
<br />

<h2>Utilities Used</h2>

<b>osTicket</b>

<b>Oracle VirtualBox</b>

<b>Tailscale</b>

<b>Rustdesk</b>


<h2>Operating Systems Used </h2>

<b>Windows 11</b> 



<h2>Setup:</h2>

<p align="Left">
Used Rustdesk with Tailscale to securely remote into my home server (Using a headless hdmi): <br/>
<img src="Images/image.png"/>
<br />
<br />

<p align="Left">
Now that I connected to my homeserver I will need to make a VM using Oracle VirtualBox.  <br/>
<img src="Images/image (1).png"/>
<br />
<br />

<p align="Left">
The VM started up so I now need to install the following files:
 
  - [osTicket](https://osticket.com/download/) - The help-desk application files.
  - [Visual Studio C++ Redistributable](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#latest-supported-redistributable-version) - Libraries required for PHP and MySQL to run on Windows.
  - [MySQL](https://www.mysql.com/downloads/) - The database server.
  - [HeidiSQL](https://www.heidisql.com/download.php) - A lightweight GUI tool to connect to MySQL.
  - [PHP](https://www.php.net/releases/index.php) - The backend logic.
  - [PHP Manager for IIS](https://www.iis.net/downloads/community/2018/05/php-manager-150-for-iis-10) - A simple IIS plugin.
  - [IIS URL Rewrite](https://www.iis.net/downloads/microsoft/url-rewrite) - Translates URLs into the actual PHP scripts.
  </p>
 <br/>


<p align="Left">
Now I need to go into Windows Features and turn on some options (CGI) so that IIS does not just appear as errors and code. <br/>
<img src="Images/wfea1.png"/>
<img src="Images/wfea2.png"/>
<img src="Images/wfea3.png"/>
<br />
<br />

<p align="Left">
Now to install PHP Manager for IIS. This lets us register PHP, switch versions, and enable extensions without having to go directly into the config files. <br/>
<img src="Images/iis1.png"/>
 
IIS URL Rewrite Module allows it to input URLs in osTicket by routing requests to the correct PHP scripts.
<img src="Images/iis2.png"/>
<br />
<br />

<p align="Left">
Its time to place the PHP files in the PHP folder.<br/>
<img src="Images/php1.png"/>
 
The files should look like this:

<img src="Images/php2.png"/>
<br />
<br />

<p align="Left">
Install Microsoft Visual Studio C++ Redistributable. <br/>
<img src="Images/mvs1.png"/>

This is needed so that everything works, otherwise it will crash.
<br />
<br />

<p align="Left">
Time to install MySQL.
<br/>
<img src="Images/sql1.png"/>
 
The SQL setup is pretty self explanatory. This will setup the database service, root password, and the port.
<img src="Images/sql2.png"/>

<br />
<br />

<p align="Left">
Now to register PHP from IIS. Run IISm as Administrator <br/>
<img src="Images/iism1.png"/>


Find PHP Manager and click it.

<img src="Images/iism2.png"/>


Register the new PHP version

<img src="Images/iism3.png"/>

Select the php-cgi

<img src="Images/iism4.png"/>

Now that this has put done I restarted IIS to apply the new PHP registration.

<br />
<br />

<p align="Left">
I then installed osTicket by extracting it into 'C:\inetpub\wwwroot' <br/>

<img src="Images/osti1.png"/>

I also moved the upload folder which renamed it to 'C:\inetpub\wwwroot\osTicket'

I then restarted to apply everything.
<br />
<br />

<p align="Left">
I select the drop-down arrow then continue to the right side; where I click "Browse*:80 (http)" under Manage Folder.
<img src="Images/lh1.png"/>
This leads me to 'http://localhost/osTicket (port 80)' which shows me that the site opens properly.
<img src="Images/lh2.png"/>
<br />
<br />

<p align="Left">
At the top of the site it shows that some extensions did not open properly so I went back to IIS to enable them.  <br/>
<img src="Images/phm1.png"/>
 
<img src="Images/phm2.png"/>
 
I then enable 'php_imap.dll'

<img src="Images/phm3.png"/>
 
<br />
<br />

<p align="Left">
Now to solve the other problems. I renamed the 'ost-sampleconfig.php' to 'ost-config.php'  <br/>
<img src="Images/ost1.png"/>
 
<img src="Images/ost2.png"/>
<br />
<br />

<p align="Left">
I then assigned permissions. <br/>
 
<img src="Images/pe1.png"/>

<img src="Images/pe2.png"/>

 Now I added permissions.
 
<img src="Images/pe3.png"/>

<img src="Images/pe4.png"/>

<img src="Images/pe5.png"/>

Now everyone has control for now just to test if everything functional. I will change that.
<br />
<br />

<p align="Left">
I am almost there with all these changes. <br/>
 
<img src="Images/osp1.png"/>
<br />
<br />

<p align="Left">
I now install HeidiSQL. <br/>
 
<img src="Images/hsql1.png"/>

<img src="Images/hsql2.png"/>

I now create a new database.

<img src="Images/hsql3.png"/>

 I named the new database 'osTicket'
<br />
<br />
 
<p align="Left">
Now everything is finished with no errors! <br/>
 
<img src="Images/done.png"/>
 
Now I will create fake requests and practice how to use ticketing software. This will mostly be for my home servers if it runs into any problems. 
<br />
<br />

