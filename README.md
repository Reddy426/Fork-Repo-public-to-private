# Fork-Repo-public-to-private
Changing the visibility of forked repository

**Quick Answer:**  
You cannot directly change a *forked repository* from public to private on GitHub. Forks inherit the visibility of the original repository. To make your fork private, you need to **duplicate the repository** into a new private repo instead.  

---

### 🔑 Why you can’t just flip the switch
- GitHub does not allow changing the visibility of a fork if the parent is public.  
- If you try to make a fork private, GitHub detaches it from the fork network and treats it as a new repository.  

---

### ✅ Steps to make a fork private
1. **Create a new private repository** in your GitHub account.  
   - Go to **Repositories → New → Set visibility to Private**.  

2. **Mirror the forked repo into your new private repo**:  
   ```bash
   # Clone the public repo as a bare repository
   git clone --bare https://github.com/username/original-public-repo.git

   # Move into the cloned repo
   cd original-public-repo.git

   # Push all branches and tags to your new private repo
   git push --mirror https://github.com/yourname/private-repo.git

   # Clean up
   cd ..
   rm -rf original-public-repo.git
   ```

3. **Work in your private repo** going forward.  
   - You can still pull updates from the original public repo by adding it as a remote:  
     ```bash
     git remote add upstream https://github.com/username/original-public-repo.git
     git fetch upstream
     git merge upstream/main
     ```

---

### ⚠️ Important Notes
- **GitHub Pages** will be disabled if you make a repo private.  
- Only collaborators you invite will have access.  
- If you’re part of an organization, visibility changes may be restricted by the org owner.  

---
