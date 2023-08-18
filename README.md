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
chmod +x ./c2/builder.sh
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
