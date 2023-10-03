## CLONE THE REPOSITORY
Clone the ros1_ci repository
    '$ cd ~/catkin_ws/src && mkdir ros1_ci'
    '$ cd ros1_ci && git clone https://github.com/jtrubatch/ros1_ci.git'

## INSTALL / RUN JENKINS
### If Jenkins is already installed (NOT RECOMMENDED)
Run the included file: run_jenkins.sh
    '$ cd ~/catkin_ws/src/ros1_ci && ./run_jenkins.sh'
    If there is an issue with permissions/executing
    '$ chmod +x run_jenkins.sh'

### Install and Run Jenkins
1. Run the included file: jenkins.sh
    '$ ./jenkins.sh'
    If there is an issue with permissions/executing
    '$ chmod +x jenkins.sh'
2. Open the generated file: jenkins__pid__url.txt and open the link to the Jenkins Web UI
3. Follow the initial set up instructions
    1. Copy the generated password from the console output
    2. Install Suggested Plugins
    3. Skip and Continue as Admin (Optional Create an Admin User)
    4. Not Now for Instance Configuration
    5. Start Using Jenkins
4. Run the run_jenkins.sh script (OPTIONAL)
    This should add some permanence to the jenkins install.
## CONFIGURE AND TEST PIPELINE
### Pipeline from SCM (Option 1)
1. From the Jenkins Dashboard Select New Item in the Upper Left.
2. Create a Pipeline Job
3. In the Pipeline Section 
    1. Change the Definition to Pipeline from SCM
    2. Set the SCM to Git 
    3. Add the Repo https://github.com/jtrubatch/ros1_ci.git
    4. Change the Branch to main
    5. Save     
4. Build to Verify Correct Configuration
5. Configure -> General/Build Triggers Select Poll SCM and enter '* * * * *'
6. Save
7. Add a Comment to Any File in the Local Repo 
    Example: /tortoisebot_waypoints/scripts/tortoisebot_action_server.py 
8. Add and Commit Changes to your Local Repo
9. Push the Changes '$ git push -u origin main'
10. Switch to The Jenkins GUI and Wait for the Build to Commence (Approximately 1 min)
