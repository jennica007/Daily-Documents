### jenkins plugins

**Ansible**  
- This plugin allows to execute Ansible tasks as a job build step  
- Ansible needs to be on the PATH for the build job in order to be used. This can be done through either Jenkins Global Tool Configuration or including Ansible on the OS User PATH variable.  

- Configuring Ansible through the Global Tool Configuration in Jenkins (Jenkins → Manage Jenkins → Global Tool Configuration) allows for multiple Ansible installations to be present and used by different Jenkins jobs.

- Click Add Ansible  
- Configure the name and path  
- Repeat for any additional desired installations  

**Ansible Tower**  
- This plugin connects Jenkins to Ansible Tower, allowing you to execute job templates.  
- After installing the plugin you can configure Ansible Tower servers in the Jenkins Global Configuration under the section Ansible Tower by clicking the add button.  

**Git Parameter**  
- This plugin allows you to assign git branch, tag, pull request or revision number as parameter in your  builds.
- There is no need to set up anything special in plugin settings.
- This plugin will read GIT SCM configuration from your projects.
- This plugin used directly the Git Plugin and Git Client Plugin.   

**Maven Project Plugin**  
- Automatic configuration of reporting plugins (Junit, Findbugs, ...)  
- Automatic triggering across jobs based on SNAPSHOTs published/consumed  
- Incremental build - only build changed modules  
- Build modules in parallel on multiple executors/nodes  
- Post build deployment of binaries only if the project succeeded and all tests passed   


**Polarion Webclient for SVN**  
- Browse Subversion repository folders and files
- Browse and compare revisions of SVN folders and files
- View revision details and compare SVN revisions
- Create/delete/modify files in a Subversion repository
- Create/delete SVN repository folders
- Easy browsing of SVN branches/tags
- 100% Pure Java*trade; implementation of the SVN access layer (using the JavaSVN library)
Multi-repository support   

**Role-based Authorization Strategy**   
- Creating global roles, such as admin, job creator, anonymous, etc., allowing to set Overall,Slave, Job, Run, View and SCM permissions on a global basis.  
- Creating project roles, allowing to set only Job and Run permissions on a project basis.  
-  Creating slave roles, allowing to set node-related permissions.
- Assigning these roles to users.    
