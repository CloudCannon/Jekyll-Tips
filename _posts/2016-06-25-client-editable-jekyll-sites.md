---
title: Client editable Jekyll sites
episode: 30
image_path: /img/casts/client-editing/preview.jpg
length: 7
video_id: oinHNWVvPLU
description: Have non-technical people update Jekyll sites
resources:
  - name: Source code
    link: https://github.com/CloudCannon/creative-jekyll-theme/
  - name: CloudCannon
    link: https://cloudcannon.com
category: intermediate
order: 1.2
---
Many people don't use Jekyll for client projects because typically a non-developer will have to learn HTML, Markdown and Liquid to update content. In this tutorial we're using [CloudCannon](https://cloudcannon.com) which gives non-developers an easy way to update Jekyll sites.

### What is CloudCannon?

CloudCannon is cloud content management system and hosting provider for Jekyll websites. A develop uploads a Jekyll site in the browser or by syncing with GitHub, Bitbucket or Dropbox. CloudCannon then builds the site, hosts it and provides an interface for a non-technical user to make updates.

### Setup

To begin, we need to create a CloudCannon account and create our first site. Head over to [CloudCannon](https://cloudcannon.com) and click the *Get Started Free* button.

![CloudCannon homepage](/img/casts/client-editing/cloudcannon-homepage.png)

Enter our details into the sign up form.

![CloudCannon sign up form](/img/casts/client-editing/sign-up.png)

Once we've signed up we're taken to our dashboard. Click *Create Site*.

![CloudCannon dashboard](/img/casts/client-editing/dashboard.png)

Enter a name for the site. I'm going to use the site from the [Converting a static site to Jekyll](/jekyll-casts/converting-a-static-site-to-jekyll/) cast so I'll call it *Creative*.

![CloudCannon enter site name](/img/casts/client-editing/enter-site-name.png)

This creates the site and gives us options for uploading our files. If you'd like to use the same site I'm using you can download it [here](https://github.com/CloudCannon/creative-jekyll-theme/archive/master.zip).

There's a number of ways of getting your files on CloudCannon. To keep things simple we're just going to upload a folder from our local computer. Click on the folder icon.

![CloudCannon site dashboard](/img/casts/client-editing/site-dashboard.png)

Navigate to your Jekyll site and click *Upload*.

![CloudCannon select files](/img/casts/client-editing/select-files.png)

Once the files upload, CloudCannon builds the site.

![CloudCannon uploaded files](/img/casts/client-editing/uploaded-files.png)

We can view the live site by clicking on the _.cloudvent.net_ URL in the sidebar.

![CloudCannon live site](/img/casts/client-editing/creative-template.png)

### Editables

The last thing we need to do is to define areas in our HTML which non-developers can update. These are called [Editable Regions](https://docs.cloudcannon.com/editing/editable-regions/) and are set by adding a class of `editable` to HTML elements.

Open `index.html` in CloudCannon and add a class of `editable` to the `h1` and `p` inside `<div class="header-content-inner">` so it becomes the following:

~~~ html
<div class="header-content-inner">
  <h1 class="editable">Your Favorite Source of Free Bootstrap Themes</h1>
  <hr>
  <p class="editable">Start Bootstrap can help you build better websites using the Bootstrap CSS framework! Just download your template and start going, no strings attached!</p>
  <a href="/about.html" class="btn btn-primary btn-xl page-scroll">Find Out More</a>
</div>
~~~

### Client Access

Now the site is ready for our non-developer to update. We'll set up _Client Sharing_ which allows our client to update their site without having to create an account. Go to the Site Settings -> Client Sharing and set a password for your client.

Our non-developer can view their live site at _something_.cloudvent.net (or you can set up a custom domain). To update their site they just add `/update` to the URL and enter the password we set.

### The Client Workflow
Once the client logs in they see their site with coloured boxes highlighting the editable regions. The client can update content directly inline by clicking on the yellow box.

![CloudCannon update inline](/img/casts/client-editing/update-inline.png)

By clicking _Collections_ in the sidebar the client can manage their blog posts.

![CloudCannon posts](/img/casts/client-editing/posts.png)

Editing posts happens in the [Content Editor](https://docs.cloudcannon.com/editing/content-editor/) which is a rich text editor for Markdown. The client can also manage all the front matter data on the page using an easy-to-use editor.

![CloudCannon content editor](/img/casts/client-editing/content-editor.png)

Or we can also use the [Visual Editor](https://docs.cloudcannon.com/editing/visual-editor/) to update posts.

![CloudCannon post Visual Editor](/img/casts/client-editing/blog-visual-editor.png)

The client can also update collection documents using the same editor. In this example there's no body content and only front matter so we've made the front matter editor full screen.

![CloudCannon collection](/img/casts/client-editing/collection.png)

If we have GitHub, Bitbucket or Dropbox connected to the site all changes the client makes would also push back to the storage provider.

Now the client can update all the content and hasn't had to learn HTML, Liquid or Markdown. This gives a small taste of what you can achieve on CloudCannon. [Sign up free](https://app.cloudcannon.com/users/sign_up) and make your Jekyll site client editable.
