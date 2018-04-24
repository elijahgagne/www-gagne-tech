
# www-gagne-tech\Readme.md

1. Download hugo to convert Markdown to HTML
1. Create a Github repo
1. Link Netlify website to Github repo
1. Add CNAME DNS record
1. Test HTTP
1. Enable automatic TLS certificates with Let's Encrypt
1. Test HTTPS
1. Setup a blog with hugo


## 1. Download hugo to convert Markdown to HTML

[https://gohugo.io/getting-started/installing/](https://gohugo.io/getting-started/installing/)
[https://github.com/gohugoio/hugo/releases/download/v0.40/hugo_0.40_Windows-64bit.zip](https://github.com/gohugoio/hugo/releases/download/v0.40/hugo_0.40_Windows-64bit.zip)

```powershell
$Url  = "https://github.com/gohugoio/hugo/releases/download/v0.40/hugo_0.40_Windows-64bit.zip"
$File = "C:\dartbox\Utilities\hugo_0.40_Windows-64bit.zip"

Invoke-WebRequest -Uri $Url -OutFile $File

Unblock-File $File

Expand-Archive $File "C:\dartbox\Utilities\hugo"

Remove-Item $File

# Add hugo to PATH
$CurrentPath = [Environment]::GetEnvironmentVariable("Path", "User")
$UpdatedPath = "C:\dartbox\Utilities\hugo;" + $CurrentPath
[Environment]::SetEnvironmentVariable("Path", $UpdatedPath, "User")
```


## 2. Create a Github repo

[https://github.com/elijahgagne/www-gagne-tech](https://github.com/elijahgagne/www-gagne-tech)

```powershell
cd C:\dartbox\Code
hugo new site www-gagne-tech
cd www-gagne-tech

git init
git add -A
git commit -m "initial commit"
git remote add origin https://github.com/elijahgagne/www-gagne-tech.git
git push -u origin master
```


## 3. Link Netlify website to Github repo

1. Connect to Git provider
2. Pick a repository
3. Build options, and deploy!

```
Build command:     hugo -s .
Publish directory: public
```

Set a deployment environment variable
```
HUGO_VERSION: 0.40
```

## 4. Add CNAME DNS record

Change Site Name
gagne.netlify.com

Domain management
Add Custom Domain
www.gagne.tech

Create CNAMES
http://controlpanel.tech/customer
gagne.tech     -> gagne.netlify.com
www.gagne.tech -> gagne.netlify.com


## 5. Test HTTP

http://www.gagne.tech/


## 6. Enable automatic TLS certificates with Let's Encrypt


## 7. Test HTTPS

https://www.gagne.tech/


## 8. Setup a blog with hugo

```powershell
cd C:\dartbox\Code\www-gagne-tech

git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke

# Edit your config.toml configuration file
# and add the Ananke theme and update the URL
np config.toml

# Create a post
hugo new posts/my-first-post.md

# Update the post
np content/posts/my-first-post.md

hugo server -D
```

Browse to http://localhost:1313/

```powershell
git add -A
git commit -m "Added first post"
git push
```
