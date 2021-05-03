---
title: Simple web/blog creation for beginners
subtitle: A mix of github pages, jekyll, js, html, css and bootstrap
layout: post
group: blog
comments: true
author : Melchor Sanchez-Martinez
date: 2021-05-03
tags: [Web-Creation, Blog-Creation, Github-Pages, Beginners, Html, Css, Bootstrap, Jekyll]
categories: [Programming, Blog, Web, Tips]
---
<!-- excerpt-start -->
I guess **it's done!!**. The [web page](https://msanchezmartinez.com) is fully working in a way that I like it (it can be improved in several ways, and maybe I do it in the future, but not now).<!-- excerpt-end --> I thought it would had easier to customize the repo
from  [bbarad](https://github.com/bbarad/bbarad.github.io) but in the end, although I was inspired/used some code from other github repos, like [FraserLab](https://github.com/fraser-lab/fraser-lab.github.io) , [pattex](https://github.com/pattex/jekyll-tagging) , [codinfox](https://github.com/codinfox/codinfox-lanyon) or [CharalambosIoannou](https://github.com/CharalambosIoannou/CharalambosIoannou.github.io), I had to
learn a little bit of html, css and bootstrap to customize the contact form, tagging blogs posts, etc. In this regard [w3schols tutorials](https://www.w3schools.in/) have been very useful.

[Disquss](https://disqus.com) for comments, [Formspree](https://formspree.io) for the contact form, [Simplesharingbuttons](https://simplesharingbuttons.com) to create share buttons for the blog posts without forgetting [fontawesome](https://fontawesome.com) for some page style and logos have been very useful also (code examples below). Moreover in [SDR](https://superdevresources.com/), [DEV](https://dev.to), [stackoverflow](https://stackoverflow.com) or [reddit](https://www.reddit.com/) there are interesting posts that can be of great help for a beginner to have the web/blog ready.

~~~ html
<div id="disqus_thread"></div>
<script>
    /**
     *  RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR PLATFORM OR CMS.
     *  LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT: https://disqus.com/admin/universalcode/#configuration-variables
     */
    /*
    var disqus_config = function () {
        this.page.url = PAGE_URL;  // Replace PAGE_URL with your page's canonical URL variable
        this.page.identifier = PAGE_IDENTIFIER; // Replace PAGE_IDENTIFIER with your page's unique identifier variable
    };
    */
    (function() {  // DON'T EDIT BELOW THIS LINE
        var d = document, s = d.createElement('script');

        s.src = 'https://your-disquss-username.disqus.com/embed.js';

        s.setAttribute('data-timestamp', +new Date());
        (d.head || d.body).appendChild(s);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>
~~~
<p style="font-size:12px;color:darkgrey" class="text-center">*Code example for inserting disquss (provided by [Disquss](https://disqus.com)) to allow comments in blog posts*</p>
~~~ html
<div class="container">
    <div class="row">
        <div class="col-sm-4 col-md-4 col-xs-12">
          <div style="width:100%;height:263px;border:3px solid gray; border-radius: 8px;background-color:gray;" display="flex;" justify-content="center;">
          <form action="https://formspree.io/f/your-formspree-key" method="POST" id="contact-form">
           <input type="hidden" name="_subject" value="Contact request from personal website">
           <p class="text-center" style="font-size:120%; color:white; font-weight:bold">Drop me a message</p>
           <input type="text" name="Name" placeholder="Your name"  data-validate-field="Name" required=False display="block" style='width:100%;'>
           <p></p>
           <input type="email" class="fcf-form-control" name="_replyto" placeholder="Your email" required=True display="block" style='width:100%'>
           <p></p>
           <textarea name="message" class="fcf-form-control" placeholder="Type your message" required=True style='width:100%; height:100px'></textarea>
           <p></p>
           <button type="submit" style="background-color:skyblue; color:darkblue; border:3px solid skyblue; border-radius: 8px; font-weight:bold;width: 100%" class="button button-center">Submit</button>
          </form>
          </div>
    </div>
</div>
~~~
<p style="font-size:12px;color:darkgrey" class="text-center">*Code example for creating a contact form based on [formspree]((https://formspree.io))*</p>
~~~ html
</div>
<div class="footer">
    <div class="container">
        <ul class="list-inline">
        <li class="footer-inverse"><a href="mailto:your-email"><i class="fa fa-envelope fa-2x"></i></a></li>
        <li class="footer-inverse"><a href="https://linkedin.com/in/your-linkedin-page"><i class="fa fa-linkedin-square fa-2x"></i></a></li>
        <li class="footer-inverse"><a href="https://twitter.com/your-twitter-ig"><i class="fa fa-twitter fa-2x"></i></a></li>
        <li class="footer-inverse"><a href="https://github.com/your-github-idz"><i class="fa fa-github fa-2x"></i></a></li>
        <li class="footer-inverse"><a href="https://gitlab.com/your-gitlab-id"><i class="fa fa-gitlab fa-2x"></i></a></li>
        </ul>
    </div>
</div>
<script src="/static/js/jquery.min.js"></script>
<script src="/static/js/popper.min.js"></script>
<script src="/static/js/bootstrap.min.js"></script>
<script src="/static/js/parallax.min.js"></script>
<script src="https://kit.fontawesome.com/153d2c5511.js" crossorigin="anonymous"></script>
</body>
</html>
~~~
<p style="font-size:12px;color:darkgrey" class="text-center">*Code example for using fontawesome to add logos in the footer*</p>
<!-- <figure>
  <img src="https://raw.githubusercontent.com/MelchorSanchez/MelchorSanchez.github.io/master/static/img/blog/disquss.webp" alt="Code to insert disquss into blog posts (provided by disquss)" title="Code to insert disquss into blog posts (provided by disquss)" class="img-responsive">
  <figcaption>Code to insert disquss into blog posts (provided by disquss)</figcaption>
</figure> -->

<!-- ![Code to insert logos from Fontawesome](https://raw.githubusercontent.com/MelchorSanchez/MelchorSanchez.github.io/master/static/img/blog/fontawesome.webp "Code to insert logos from Fontawesome"){:class="img-responsive" :alt="Code to insert logos from Fontawesome"} -->

It has been funny, not too much difficult (has to be said that I am new in "web programming" but not in programming), but harder of I expected ... I supposed that in a couple of afternoons, in a weekend, it could be done... and in the end it took me a couple of weekends and some nights during the week. But I enjoyed the process, so although I still have to learn a lot ,almost everything, about js, html, css, boostrap and jekyll basics I have enjoyed the way (I will probably enroll in some courses in the future...), it was worth it.

I hope these few lines could serve to someone in the same situation I was! **Enjoy your web/blog programming/creation!**

And if you like how my page looks like and want to use the code, just fork my [repo](https://github.com/MelchorSanchez/MelchorSanchez.github.io) that is available on github. And if you want to go to the prmary sources, as I commented before, go to [bbarad](https://github.com/bbarad/bbarad.github.io) or [FraserLab](https://github.com/fraser-lab/fraser-lab.github.io) repos. Also you can explore more repos on github, actually there are 2,526,710 repositories containing github pages (aka the .github.io extension).

Finally, but not least, **stay tuned** because from now on I will start posting about different topics. I already have some ideas in mind that I believe could become in interesting posts!
