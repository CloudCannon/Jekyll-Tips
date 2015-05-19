---
layout: guide
title : CMS and Hosting
order: 7
---

[CloudCannon](http://cloudcannon.com) is a service which provides a CMS for Jekyll websites, they also provide hosting. We're going to use CloudCannon to allow our client to update the website.

**Important**: CloudCannon detects that it's a Jekyll website by looking for a **_config.yml** file in the website root. Add **_config.yml** to your website root (it can be empty for now) and push it to GitHub.

Head over to [CloudCannon](http://cloudcannon.com), sign up for a free account and create a website.

![Create Site](/img/guide/cms/create_site.png)

This bring up the file browser for the site. There's no files at the moment so let's add some! Click the connect storage provider button.

![Dashboard](/img/guide/cms/dashboard.png)

We want to sync files from our repository so click next to GitHub and allow CloudCannon access to your account.

![Connect](/img/guide/cms/connect.png)

Connect the repository for the website.

![Repo](/img/guide/cms/repo.png)

CloudCannon will pull in your files and display them in the file browser. Any updates you make in CloudCannon are synced back to GitHub and any changes you push to GitHub are synced to CloudCannon.

![Files](/img/guide/cms/files.png)

Now we have the files on CloudCannon, it's time to add updatable regions. Click on **index.html**, this brings up the site in preview. You can navigate around the website in this view. Click on the **Code Editor** view to bring up the source code of the site.

![Preview](/img/guide/cms/preview.png)

We set the updatable regions by adding a class of **editable** to elements in the HTML. Let's make the **&lt;p&gt;**'s inside the billboard section and the info details section editable like so:

<pre>&lt;section class=&quot;billboard&quot;&gt;
    &lt;div class=&quot;wrapper&quot;&gt;
      &lt;div class=&quot;caption&quot;&gt;
        &lt;p class=&quot;editable&quot;&gt;Excepteu roccaecat&lt;/p&gt;
        &lt;p class=&quot;editable&quot;&gt;sunt culpa officia deserunt&lt;/p&gt;
      &lt;/div&gt;
    &lt;/div&gt;
&lt;/section&gt;&lt;!--  End Billboard  --&gt;</pre>

<pre>&lt;div class=&quot;info_details editable&quot;&gt;</pre>

As you can see you have complete control over which elements you want to make updatable. In **billboard** we've ensured there's always two paragraphs. For info_detail the client can add update everything.

Go to the visual editor view. The elements with the editable class have a yellow box around them indicating they're updatable. Try clicking on an editable region and making an update directly inline.

![Visual Editor](/img/guide/cms/visual.png)

One thing you might notice is when you delete most of the text in the **billboard** section the 2nd paragraph jumps up beside the first one. This is due to how the CSS on this particular template behaves. The visual editor is simply running all your CSS and Javascript so there's no way for it to know this isn't the desired effect. To fix this you'd need to add some CSS to your stylesheet to ensure the paragraphs don't jump up like that.

CloudCannon pushes your website live to a testing domain of *.cloudvent.net. To view this on the free plan you'll need to set a password on the website. On paid plans you can add your own domain. 
