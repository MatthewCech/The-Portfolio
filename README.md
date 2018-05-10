# The-Portfolio
A quick template and walkthough for a minimalist portfolio website using the files in this repo. Sections have accompanying gifs, but due to size limitations, I have not displayed them as anything but links. 



### Getting Started

Go ahead and make a github repo - for testing to make sure it's set up correctly, make the name `yourname.github.io`. For example, I would use matthewcech.github.io as the name, and your site will be live at `https://yourname.github.io`! You can do this with a differently named repo as well if you wish, you'll just have to make sure you turn on github pages in the first section below.

All things considered, if you don't care about a custom URL, you're done. Just grab index.html and the assets folder from any sites you downloaded at https://theportfolio.com/ and plop them in your own (You don't need a git client, you can just drag and drop them into the repo), and you're good to go!

IF you're after a custom domain tho, carry on! You'll learn about how to set that up, and a lot more.



### Configuring GitHub's side for a custom URL:

Section Walkthough Gif: https://i.imgur.com/NZlhA6a.gif

- Head to repo settings
- Find the secion about github pages. If you have not enabled it, do so, probably on master branch. (Stop here if you don't want a custom domain!)
- Once enabled, specify your custom domain. 
- If you look in the repo root, we see a CNAME file was added!
- It's good practice to add a www.<sitename> variant. You can do this in-browser by clicking the edit button.



### Configuring Google Domains

Section Walkthough Gif: https://i.imgur.com/Nn929du.gif 

- Go to domains.google.com and navigate to the domain you wish to point at github.
- Head to the DNS tab (second from the right, looks like stacked boxes)
- Scroll all the way down to the records section
- Add an A name record for both of github's IP addresses: This way, we point the base site at github pages.
  - Github IPs are `192.30.252.154` and `192.30.252.153` at the time of writing.
- Add a CNAME record, with `www` filled in as the record name. We will direct this to the domain itself, just without the www

Google domains is fast. Like, really fast. Realistically, you can probably navigate to your new site right after setting all that up, so go ahead and test that out in incognito/private browsing mode so that we don't have old things cached.



### HTTPS (Optional, but not really optional)

At this point, we have your domain hosted at github pages. We have a custom domain rerouting HTTP requests.
However, there's no HTTPS going on, and you still need a site. For now, we should get you set up with HTTPS routing.

We'll be using cloudflare in order to force connections to be HTTPS. They don't make you pay for an SSL certificate, which is nice.

We'll start by making an email to use with Cloudflare. This can be done using one of the many free email forwards you get with a custom domain.


Section Walkthough Gif: https://i.imgur.com/eFmyvsb.gif

- Go to domains.google.com and navigate to the domain you've been using for this
- Click on the mail tab, second from the left, and scroll down. 
- Enter `cloudflare` as the email name, and route it to an email you own already. 
- As necessary, confirm the email. If you forward to the email you used for registering the domain, no confirmation is necessary.


Next, we're going to be setting up a cloudflare account, and fight out way to the console.

Section Walkthough Gif: https://i.imgur.com/uNvyr7k.gif

- Head to Cloudflare.com
- Click on the 'log in' button in the upper right of the site, and proceed to make an account. For your email, use the email you just created.
- Once you have created an account, you will be asked to specify the name of your site. Do so with your custom URL.
- From here, you will be asked to select a plan. For our purposes, the free one is just fine. 
- After confirming the plan, Cloudflare will query the existing DNS for all records. You should see 3 records that you made: the 2 A records that go to githubs IP, and the CNAME record. You will also see MX records for goole email servers. 
- If all records are present, continue. This should take you to the last step before the console.
- You will then be asked to update the name servers. Go back to the DNS records section of your custom domain, and go ahead and find the nameservers section at the top. Copy in the ones Cloudflare specifies.
- Once updated. you will then be at the console.

Second to last, we're going to set up an SSL certificate.


Section Walkthough Gif: https://i.imgur.com/8eG7flT.gif

- In cloudflare, head to the Crypto tab at the top
- Under SSL at the top, select 'flexible' from the drop down. We're going to need a flexible certificate. 
- turn 'Always use HTTPS' on
- turn 'Automatic HTTPS Rewrites' on

Finally, we're going to force everything to be rewritten to HTTPS. Because Security. Also looks professional. Also improves search result rating.


Section Walkthough Gif: https://i.imgur.com/cX9Jsyz.gif

- Head to the page rules tab at the top
- Create a new page rule for "Enforce HTTPS"
- Enter your site URL modified as follows: `http://*yoursitename.com*`
	- As an example, this demo site has `http://*theportfolio.pw*` in that field

In the crypto tab, if the certificate says "active" and if in the overview tab it says "Status: Active" then you're good to go for HTTPS. Try navigating to your page now! It should say "secure" to the left of the URL.

You're done! Good work!



### Afterthoughts

You'll need to update information in the template that's in this repo. I'd recommend a text editor that does color syntax highlighting for HTML - I personally use Sublime Text, but other common ones are Notepad++, and as of writing, atom is all the rage. Most IDEs tend to have HTML support as well.

If you're like me and don't use an IDE for this, rather, just a text editor, you will probably need a convenient local webserver. I use something called mongoose: There's a free version of it available for download at https://cesanta.com/binary.html - just plop it in your directory, and double-click to start it! 
