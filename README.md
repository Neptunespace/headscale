# headscale simple installation 


Go on this website and click generate: https://www.wireguardconfig.com/ 

![image](https://user-images.githubusercontent.com/93327314/142696540-77230d9d-cf1f-4603-855c-a8d10f7ac7a9.png)

copy the private key SERVER (not the client key).

sudo nano /home/ubuntu/config/private.key

paste the private key inside and save the file ( ctrl+s, ctrl+x)


1. When running headscale in a docker container, prepare a directory to hold all configuration

```shell
   mkdir config
   ```
   
 
   ```shell
   touch /home/ubuntu/config/db.sqlite
   ```
   
   2. Clone the repo
   
   ```shell
   git clone https://github.com/juanfont/headscale.git /home/ubuntu/headscale
   ```
   3. Copy the needed file to config.
   
   ```shell
   cp /home/ubuntu/headscale/config-example.yaml /home/ubuntu/config/config.yaml
   ```
   
   ```shell
   cp /home/ubuntu/headscale/derp-example.yaml /home/ubuntu/config/derp.yaml       ovhgbzvoihovhaoivhbzeoivbhzoibhiohezbiozbvipzb$ebhzierobhzbhzepbo
   ```
   4. Edit the config
   
   ```shell
      nano /home/ubuntu/config/config.yaml
   ```
   Replace server_url: with your public ipv4 address  or domain name (https works too).
   
   5. Run the container.
  
   ```shell
      sudo docker run -d \
      --name=headscale \
      --net=bridge \
      -v /home/ubuntu/config:/etc/headscale/ \
      -p 8080:8080 \
      headscale/headscale \
      headscale serve
   ```
   6. Remove the useless headscale folder
   
   ```shell
      sudo rm -rf /home/ubuntu/headscale
   ```
   
   
   Enjoy ;)
