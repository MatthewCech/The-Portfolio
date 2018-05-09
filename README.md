# The-Portfolio
A quick template and walkthough for a minimalist portfolio website

### Getting Started
Go ahead and make a github repo - for testing to make sure it's set up correctly, make the name `yourname.github.io`. For example, I would use matthewcech.github.io as the name.

### Configuring GitHub's side of this:

![Setting GitHub custom domain](https://i.imgur.com/NZlhA6a.gif)

- Head to repo settings
- Find the secion about github pages. If you have not enabled it, do so. 
- Once enabled, specify your custom domain. 
- If you look in the repo root, we see a CNAME file was added!
- It's good practice to add a www.<sitename> variant. You can do this in-browser by clicking the edit button.


### Configuring Google Domains

![Setting up Google Domains to point at GitHub for HTTP component](https://i.imgur.com/Nn929du.gif)

- Go to domains.google.com and navigate to the domain you wish to point at github.
- Head to the DNS tab (second from the right, looks like stacked boxes)
- Scroll all the way down to the records section
- Add an A name record for both of github's IP addresses: This way, we point the base site at github pages.
  - Github IPs are `192.30.252.154` and `192.30.252.153` at the time of writing.
- Add a CNAME record, with `www` filled in as the record name. We will direct this to the domain itself, just without the www