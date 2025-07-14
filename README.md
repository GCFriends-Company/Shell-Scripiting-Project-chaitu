# 🔐 GitHub Collaborator Access Audit Script

This shell script automates the process of auditing **who has read (pull) access** to a GitHub repository using the **GitHub REST API**.

---

## 📋 Features

- ✅ Lists all collaborators with **read access** (i.e., pull permission)
- 🔐 Uses **GitHub personal access token (PAT)** for authentication
- 💻 Built entirely in **Bash**, using `curl` and `jq` for API and JSON handling
- 🧪 Can be run locally or scheduled using `cron` for periodic access reviews

---

## 🛠️ How It Works

This script:

1. Accepts two arguments:
   - GitHub **repository owner**
   - GitHub **repository name**
2. Uses your GitHub **username** and **personal access token** to authenticate
3. Calls the GitHub API to fetch a list of collaborators
4. Filters those with **read access** (using the `.permissions.pull == true` check)
5. Prints their GitHub usernames to the terminal

---

## 📦 Requirements

- `bash`
- `curl`
- [`jq`](https://stedolan.github.io/jq/) – to parse JSON
- GitHub [Personal Access Token (PAT)](https://github.com/settings/tokens) with `repo` scope

---

## ⚙️ Usage

```bash
# Set your GitHub credentials as environment variables
export username=your_github_username
export token=your_personal_access_token

# Run the script with repo owner and repo name as arguments
./list-users.sh <repo_owner> <repo_name>

## Example
 -./list-users.sh GCFriends-Company Shell-Scripiting-Project-chaitu
## 📤 Sample Output
 -Listing users with read access to GCFriends-Company/Shell-Scripiting-Project-chaitu...
 -Users with read access to GCFriends-Company/Shell-Scripiting-Project-chaitu:
 -chaitrajaamchuri
 -teammate1
 -teammate2
## If no users with pull access are found:
 -No users with read access found for GCFriends-Company/Shell-Scripiting-Project-chaitu.

## 🧠 Real-Time Use Case
 This script is useful for:

 -Security audits – know who has access to your repos

 -Compliance reviews – automate access checks on a schedule

 -DevOps teams – integrate into CI/CD or monitoring tools

 -Large organizations – manage and report access across multiple teams

 -You can schedule this with cron to perform daily or weekly audits and even extend it to export results to a CSV, email, or Slack channel.

