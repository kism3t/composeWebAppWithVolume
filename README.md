# Sample Docker Compose Web (mounted volume)
This demonstrates a docker-compose.yml which starts a nginx web server and uses local (host) volume to provided content.

The intention of this docker compose was to test [multi container in Azure App Service](https://docs.microsoft.com/en-us/azure/app-service/tutorial-multi-container-app) and mount a storage account as volume. 
## Set Up Locally
1. Set up a volume in your docker:
   - execute command ` docker volume create configuration` 
2. Put content in configuration
   - Check location where on host configuration is pointing [see stackoverflow](https://stackoverflow.com/a/64418064/3042145)
   - copy content of `.\html` into it
3. Start docker:
   - execute `docker compose up` and go to [localhost:8080](http://localhost:8080/) to see the index file
4. Modify the `index.html` within the volume folder and see changes instantly in browser

## Set up Azure App Service
1. Create an App Service in azure portal (you can use [Azure Multi Container Quickstart as a Guideline](https://docs.microsoft.com/en-us/azure/app-service/quickstart-multi-container)).
2. Mount a storage File Share to an App Service (see [Mount Storage as Local File Share](https://docs.microsoft.com/en-us/azure/app-service/configure-connect-to-azure-storage?tabs=portal&pivots=container-linux))
   - name the mount as `configuration` so the `docker-compose.yml` woks, as it is defined there
3. Upload to Storage Account mounted path files and check them through App Service URL

# see also
https://docs.microsoft.com/en-us/answers/questions/343312/azure-app-services-w-docker-compose-volume-persist.html
