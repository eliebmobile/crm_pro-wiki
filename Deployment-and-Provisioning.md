Provisioning and deployment of both the backend api and front end application are done via ansible. 

## Commands

* `./ansible.sh provision.yml` : Provision a server  
* `./ansible.sh deploy.yml` : Deploy the application (front and backend)
* `./ansible.sh deployfe.yml` : Deploy only the front end
* `./ansible.sh deploybe.yml` : Deploy only the back end

## Roles
The Ansible roles defined are: 
* common : Setup variables that are required by other roles
* base : Base system provisioning. This setup is required for all servers that require the codebase.
* api : Deploy the backend API
* database : Provision a postgres 9.4 database
* queue : RabbiqMQ installation and setup
* webservers : NginX and uWsgi installation and configuration

## Deployment 

The deployment is performed using the following directory structure: 

```
/opt/
    crmpro/
        env/  
        api/  
        ui/   
        config/ 
```