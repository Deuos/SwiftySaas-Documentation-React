# Backend Deployment

##### Digital Ocean - Racknerd - AWS - Google Cloud - Oracle Cloud Recommended

You can use any web service platform out there, I recommend you go with a monthly or yearly payment since you will know how much you will be paying for. Watch for hidden fees etc, when choosing a platform to host your backend. Since its a Restful API, the cost shouldn't be too much until you are running extensive jobs. 

If you are buying a VPS - Deploy using a Linux since it will be the cheapest and fastest

For the backend, I have already created a dockerfile for you, which you can run and deploy anywhere. 

[AWS Docker Deployment Article](https://medium.com/@kumarapkvel/step-by-step-guide-to-host-a-simple-rest-api-in-aws-docker-aws-app-runner-6adcda4f144a)

[DigitalOcean Deployment Article](https://docs.digitalocean.com/products/marketplace/catalog/docker/)

**Linux VPS**

[Nginx Setup Article](https://www.digitalocean.com/community/tutorials/how-to-install-nginx-on-ubuntu-20-04) - This will guide you how to open your Linux Vps to the public using Nginx

[Linux Deployment Article](https://www.docker.com/blog/how-to-deploy-on-remote-docker-hosts-with-docker-compose/) - This show you a better understanding of the dockerfile and docker

Other things you might need to do

* SSL Certificate
* A Record setup for api.swiftysaas.com
* Linux Security
