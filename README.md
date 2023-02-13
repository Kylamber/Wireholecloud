# WireHoleCloud
This is some kind of a fork for the [WireHole](https://github.com/IAmStoxe/wirehole) docker-compose project without Unbound (I could not get this working for me). Combining [WireGuard Easy](https://github.com/WeeJeWel/wg-easy), [Pi-Hole](https://pi-hole.net/), [Nextcloud](https://nextcloud.com/) in one docker compose so you can have your own private cloud storage accessible through a self-hosted VPN.

## Quickstart
To get started, clone this repo and `docker compose up`.
```bash
git clone https://github.com/Kylamber/Wireholecloud.git
cd Wireholecloud
docker compose up
```

Another way is just to download `docker-compose.yml` and put it into a folder and `docker compose up` it.

## Usage
The IP addresses and ports mentioned here are the defaults inside `docker-compose.yml`
### WireGuard Easy (wg-easy)
Connect to wg-easy using `localhost:51821` or `10.2.0.3:51281` and login using the specified password in `docker-compose.yml`. Add clients as you wish and connect them with your devices. The devices that have access to this VPN can access the other services in the same docker network.

![image](https://user-images.githubusercontent.com/32596839/218538768-e479d35f-aa7b-4ad9-8e99-e953e44c9e44.png)


### NextCloud
Connect to NextCloud using `localhost:8080` or `10.2.0.4:8080`. To set it up the first time, you can fill in the admin user and password. For the database, select MySQL/MariaDB and input the database user, password, and name according to `docker-compose.yml`. For the database host, put in `localhost:3306` and if that doesn't work try putting in `10.2.0.5:3306`.

![image](https://user-images.githubusercontent.com/32596839/218542609-7bfcadd0-f04e-4933-aaf1-5d646c6034a8.png)


### Pi-Hole
Connect to Pi-Hole's admin site using `localhost:8081/admin` or `10.2.0.100:8080/admin`.

![image](https://user-images.githubusercontent.com/32596839/218539172-bcc1439d-f5b8-47c2-9570-ce7be2629c74.png)


## Modifications
If you only want to use the WireGuard Easy and Pi-Hole containers, feel free to delete the mariadb and nextcloud container from `docker-compose.yml`.  

## Limitations
I do believe that this can't be used in an armv7 devices such as a Raspberry Pi since the mariadb container doesn't support it. 
