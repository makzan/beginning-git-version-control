# Chapter 10: Code Deployment

TODO: Need refinement on this chapter.

We can setup hook on web service that performs automatic code deployment when we push the git repository changes to the remote branch.

## Push to Cloud66

The following demonstrates deploying a web project to Cloud66 with git.

### Initial setup

Git push to bit bucket.

Then, in cloud66, create a stack by using the bit bucket repository URL.

After the analysis, we choose where to host the code. There are options from existing cloud providers, such as Linode and DigitalOcean.

The cloud66 will then build the stack by using the selected cloud provider.

### Making changes and redeploy

After the initial deployment, we can further make changes to our code.

In the cloud66 stack information, we can obtain an URL to trigger the redeployment.

NOTE: charge may apply on using Cloud66 service and cost of using cloud providers.


## Deploying with Codeship

Codeship allows us to setup our own deployment commands when new code is pushed to a remote repository.

For example, I setup makzan.net deployment script on Codeship.

That website is built by using middleman – a static site builder that generates static web pages according to my files. These web page files are then hosted in static hosting service, surge.sh.

I setup the Codeship to install the middleman gem and build the website into static web pages output. Then it install surge command and push the build folder into the service. The access key are set as a Codeship environment variables.