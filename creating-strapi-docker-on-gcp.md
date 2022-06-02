## Creating Strapi docker on GCP

1. `sudo apt-get update`
2. Install Docker `sudo apt install docker.io`
3. Add sudo right to docker `sudo usermod -a -G docker $USER`
4. Install Docker Compose `sudo apt install docker-compose`
5. Install GIT `sudo apt install git`
6. setup your `docker-compose.yml`
7. setup your project
8. run `docker-compose up -d`
9. check if containers running `docker container ls`

## Uploading files
### Single file
`gcloud compute scp database.sql --zone "europe-west2-b" disco-elysium-wp2:~/wp-data/ --project "bigdrive-332209"`

### Folder
`gcloud compute scp --recurse database --zone "europe-west2-b" disco-elysium-wp2:~/wp-data/ --project "bigdrive-332209"`


### Wordpress starter repo
https://github.com/nezhar/wordpress-docker-compose

