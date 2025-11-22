# Getting Started With Github API (Beginner friendly guide)
## 1. What Github API is
The Github API allows you to interact with Github programmatically instead of using and clicking buttons on the website. You send Http requests to create repo, fetch user data, open issue and more. 
## 2. Base URL:
Github is a REST API and all rest API start with :

``` https://api.github.com```
## 3. Authentication
Github uses personal Acess Tokem(PAT) for authentication
### steps to get your token
1. Login to Github
2. Go to settings
3. Scroll to developer settings - personal access tokens
4. Create a new token (fine grained token recommended)
5. Copy the token and keep safe (you will not see it again)

### How to use te token 
Add it to your request header:

``` Authorization: Bearer YOUR_TOKEN_HERE```
## 4. Making your first request
Example: Get a github User

Endpoint

``` GET/users/(username) ```

Full example using (cURl)

``` curl https://api.github.com/users/octocat/-H "Authorization: Bearer YOUR_TOKEN" ```
### What you will get in your response 
A jSON object with ;
- name 
- username
- profile URL
- number of repos
- followers
- etc..

## 5. List a User's public repositories
``` GET/users/(username)/repos ```

Example
``` curl https://api.github.com/users/octocat/repos/-H "Authorization:Bearer YOUR_TOKEN ```

Response
Returns a lsit of repos with:
- name 
- descripton
- visbility
- done uRLs
- stars
- languages
## 6. Create a new repository:
``` POST/users/repos ```
Body example

```{
    "name":"my _new_repo",
    "description":"my first repo created using the Github API "
    "private":false"
} 
```

Example (cURL)

``` CURL -X POST https://api.github.com/users/repos/-H "Authorization: Bearer YOUR_TOKEN"/
-H "content-Type: application/json"/
-d '{"name":"my-new-repo","private":false"}'
```
If the token has the right permission, the new repo will be created immediately.

## 7. 