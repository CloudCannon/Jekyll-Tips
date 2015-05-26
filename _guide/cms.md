---
title : CMS and Hosting
order: 8
---

[CloudCannon](http://cloudcannon.com) is a service which provides a CMS for Jekyll websites, they also provide hosting. We're going to use CloudCannon to allow our client to update the website.

**Important**: CloudCannon detects that it's a Jekyll website by looking for a `/_config.yml` file. Create `_config.yml` in the website root (it can be empty for now) and push it to GitHub.

Head over to [CloudCannon](http://cloudcannon.com), sign up for a free account and create a website.

![Create Site](/img/guide/cms/create_site.png)

This brings up the file browser for the site. There are no files at the moment so let's add some! Click the **connect storage provider** button.

![Dashboard](/img/guide/cms/dashboard.png)

We want to sync files from our repository so click **Connect** next to GitHub and allow CloudCannon access to your account.

![Connect](/img/guide/cms/connect.png)

Connect the repository for the website.

![Repo](/img/guide/cms/repo.png)

CloudCannon will pull in your files and display them in the file browser. Any updates you make in CloudCannon sync back to GitHub and any changes you push to GitHub sync to CloudCannon.

![Files](/img/guide/cms/files.png)

Now we have the files on CloudCannon, it's time to add updatable regions. Click on `index.html`, this brings up the site in preview. You can navigate around the website in this view. Click on the **Code Editor** view to bring up the source code of the site.

![Preview](/img/guide/cms/preview.png)

We set the editable regions by adding a class of **editable** to elements in the HTML. Let's make the headings on the index page editable:

{% highlight html %}
<header>
  <div class="header-content">
    <div class="header-content-inner">
      <h1 class="editable">Your Favorite Source of Free Bootstrap Themes</h1>
      <hr>
      <p class="editable">Start Bootstrap can help you build better websites using the Bootstrap CSS framework! Just download your template and start going, no strings attached!</p>
      <a href="#about" class="btn btn-primary btn-xl page-scroll">Find Out More</a>
    </div>
  </div>
</header>
{% endhighlight %}

The context you put the editable class is important. If you wanted to give more control to the client you could add the class to the `div`. Then they'd be able to add more headings, lists, images etc.

Go to the **Visual Editor** view. The elements with the editable class have a yellow box around them indicating they're editable. Try clicking on an editable region and making an update inline.

![Visual Editor](/img/guide/cms/visual.png)

CloudCannon pushes your website live to a testing domain of `*.cloudvent.net`. On the free plan the website isn't public, we need to add a password before we can view it. Go to **Site Settings**, then **Site Password** and type in a password for your website.

![Password](/img/guide/cms/password.png)

Click on the cloudvent domain at the top of the page, enter your password. Our site is now live on the internet!

![Cloudvent](/img/guide/cms/cloudvent.png)
