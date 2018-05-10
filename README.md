# The-Portfolio
A quick template and walkthough for a minimalist portfolio website

### Getting Started
Go ahead and make a github repo - for testing to make sure it's set up correctly, make the name `yourname.github.io`. For example, I would use matthewcech.github.io as the name.

### Configuring GitHub's side of this:

<img src="https://i.imgur.com/NZlhA6a.gif" alt="Configuring Github" width="300px">

- Head to repo settings
- Find the secion about github pages. If you have not enabled it, do so. 
- Once enabled, specify your custom domain. 
- If you look in the repo root, we see a CNAME file was added!
- It's good practice to add a www.<sitename> variant. You can do this in-browser by clicking the edit button.


### Configuring Google Domains

<img src="https://i.imgur.com/Nn929du.gif" alt="Setting up Google Domains to point at GitHub for HTTP component" width="300px">

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

