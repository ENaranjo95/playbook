# Starting a new Wordpress from the [Wordpress Starter](https://github.com/Resilient-Labs/wordpress-starter)

Before you can duplicate a repository and push to your new copy, or mirror, of the repository, you must create the new repository on GitHub.
For example, for a resilient lab project, the lead developer would initiate a empty repo on github with the name matching the directory (folder) that the files will be saved in. Afterwards, you can follow the following commands:

1. Open Terminal
2. Create a bare clone of the repository by running the following in terminal:
```
git clone --bare https://github.com/Resilient-Labs/wordpress-starter.git
```
3. Mirror-push to the new repository by running the following in terminal:
```
cd wordpress-starter.git
```
```
git push --mirror https://github.com/your-github-username/new-repository-name.git
```
4. Remove the temporary local repository you created in step 1.
```
cd ..
```
```
rm -rf wordpress-starter.git
```
5. Afterwards, check your github to see that the newly created repo has been populated with data from the cloned repo. If all looks good on github.com clone the updated like so (Remember, be sure you grab the clone link from your own newly created repo):
```
git clone https://github.com/your-github-username/new-repository-name.git
```

### Making the files your own
Open in text editor/IDE
#### Files to edit:

##### /site/web/app/themes/sage/assets/manifest.json
Change the line 25: ```"devUrl": "http://roots-example-project.dev"``` to ```"devUrl": "http://new-project-name.dev"```

##### /trellis/group_vars/development/vault.yml
Change line 7: ```roots-example-project.com:``` to: ```new-project-name.com:```   

##### /trellis/group_vars/development/wordpress_sites.yml   
Change line 5: ```roots-example-project.com:``` to: ```new-project-name.com```   
Change line 8: ```- canonical: roots-example-project.dev``` to: ```- canonical: new-project-name.dev```   
Change line 10: ```- www.roots-example-project.dev``` to: ```- www.new-project-name.dev```   
Change line 12: ```admin_email: admin@roots-example-project.dev``` to: ```admin_email: admin@new-project-name.dev```   

### Running the Wordpress Project on your local machine
1. Change directories to the ```trellis``` sub-directory by running the following in terminal:
```
cd trellis 
```
2. **Install external Ansible roles/packages**
```shell
# @ new-project-name/trellis (you must cd to this path)  
ansible-galaxy install -r requirements.yml
```

3. **Install theme components**
Jump into the Sage directory by running the following in terminal:
```shell
# @ new-project-name/site/web/app/themes/sage (you must cd to this path)  
cd ../site/web/app/themes/sage
```
then run the following in terminal:
```shell
# Install Node dependencies 
npm install
```

```shell
# Install Bower dependencies 
bower install
```

```shell
# Install Gulp dependencies 
gulp
```

4. **Fire up the server** (be patient, but watch the console––it may prompt for your system password
```shell
# @ roots-example-project.com/trellis (you must cd to this path)  
cd ../../../../../trellis
```

```shell
# Run vagrant up !
vagrant up
```
_Note: to shut down the server:_ `vagrant halt`

### Files to edit for Wordpress Development:





