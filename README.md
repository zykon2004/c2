# c2
## C2 server, client and cli
### Features
 - Linux Server running as an http listener
 - Linux Client running as an http listener
 - Beautiful CLI
 - Local DB using sqlite3
 - Payload Authentication using HMAC
 - Encryption with self signed certs
   
### Requirments
 - Docker
 - Docker compose
## HOWTO
### Building docker compose
```sh
git clone --depth=1 https://github.com/zykon2004/c2.git
./c2/builder.sh
```
### Running CLI
```sh
docker exec -it c2-server bash
python cli/cli.py
```
## Running without Docker
 - Clone the 3 projects
```sh
git clone --depth=1 https://github.com/zykon2004/c2-client.git
git clone --depth=1 https://github.com/zykon2004/c2-server.git
git clone --depth=1 https://github.com/zykon2004/c2-server-cli.git
```
 - Create a separate virtualenv for each one using requirements.txt
 - On 3 terminal windows activate the virtualenv of each, then:
 ```sh
 # 1st Terminal
 python c2-client/client/client.py
 # 2nd Terminal
 python c2-server/server/server.py
 # 3nd Terminal
 python c2-server-cli/cli/cli.py
 ``` 
  - Use CTRL + C to QUIT
## Docker causing erros
**Problem**:
```sh
failed to create network projects_c2_network: Error response from daemon: Pool overlaps with other one on this address space
```
Solution:
```sh
docker compose down
```
Hardcore solution (Will delete images, containers, cache)
```sh
docker system prune --all --force
```
**Problem #2**:
```sh
Error response from daemon: Address already in use
```
Solution:
I dont know why this is happening and I was not to reproduce it consistently.
The workaround is to close all newly created containers and start them 1 by 1 starting from the server.
Also make sure that the port is not really used by some other process:
```sh
lsof -i tcp:8001
```
A restart to docker engine helps:
```sh
sudo systemctl restart docker
```
