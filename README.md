# jenkins
Jenkins

Install Jenkins 

# 1. Install jenkins
sudo zypper addrepo http://pkg.jenkins-ci.org/opensuse/ jenkins
sudo zypper install jenkins
# You would be asked something like this:
# Do you want to reject the key, trust temporarily, or trust always? [r/t/a/?] (r): t
# Overall download size: 115.9 MiB. After the operation, additional 159.9 MiB will be used.
# Continue? [y/n/?] (y): y

# 2. Start jenkins
sudo /etc/init.d/jenkins start

# 3. Configure Jenkins
# Go to Manage Jenkins> Plugins > Available Plugins> Github API Plugin and Github Plugin
# select and install with restart

# 4. Configure System:
# Go to Manage Jenkins > configure
Set up Jenkins Location

# 5. Add Git User credential
git config --global user.name "Jenkins"
git config --global user.email "jenkins@dev.server.com"

# 6. Setup SSH keys
su -s /bin/bash jenkins
cd ~
ssh-keygen -t rsa

#7. Copy the key and put in deploy keys of the project. You can view the key by cat /keypath

#8. Create a new Jenkins Empty Job

#9. Supply a project name

#10. Give the project url in Github Project url. for eg. http://github.com/tshriram02/Angular-Flash-Talk

#11. In Source Code Management, supply repository url, for eg. http://github.com/tshriram02/Angular-Flash-Talk 

#12. In Build triggers, choose your appropriate options, generally, Build when a change is pushed to GitHub and Poll SCM with a schedule of H/5 * * * * which means jenkins will poll every 5 minutes.

#13. In Build/Execute Shell, put command as bundle exec rake db:migrate RAILS_ENV=test&&bundle exec rake spec RAILS_ENV=test&&bundle exec cap integration deploy:migrations, where integration is the environment

#14. Click on Apply and Save.

#15. If you're facing SSH issues - enable SSHless login by adding your jenkins key to ~/.ssh/authorized_keys in the user account from where you're doing the deployment. Create the file authorized_keys if it's not present by touch ~/.ssh/authorized_keys

#16. Click on build now/push something to your repository to trigger the build.

#17. You can also add Jenkins service in your Github repository.

#18. If you face SFTP upload permission problems, please change set :deploy_via, :copy to set :deploy_via, :remote_cache in Capfile
