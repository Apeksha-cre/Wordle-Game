# CPSC-449-Web Backend Engineering:Project-4
# Project Members:

1. Hardik Vagrecha          885198390 | hardik.vagrecha@csu.fullerton.edu
2. Apurva Umakant Gawande   885897918 | apurva.gawande@csu.fullerton.edu
3. Apeksha Shah             885904342 | apeksha@csu.fullerton.edu
4. Maria Ortega             887028306 | mortega15@csu.fullerton.edu

# Configuration files:
1. Procfile is a mechanism for declaring what commands are run by your application to start the app 
2. Update the nginx.config from nginx_config/tutorial into default file present in /etc/nginx/sites-enabled

## To start crontab run the following command:
```bash
   crontab -e 
   Enter the script in the file which opens (example : /tmp/crontab.81GywU/crontab):
   */10 * * * * run-one rq reque -all --queue default
```
# The following are the steps to run the project:
1. Installing and configuring Nginx:
```bash
sudo apt update
sudo apt install --yes nginx-extras
```
2. Then cd into the CPSC449-Project3 folder and run the following commands:
```bash
cd bin
chmod u+x litefs
sh init_dir.sh
cd ..
```
3. Start the services
```bash
foreman start 
//Do this to register the callbackUrl
// Sometimes foreman will not start so please restart the system and agin run foreman start
```
4. Run both the init scripts to populate the database and automatically connect the api to the database. 
```bash
open a new terminal at the project folder and enter:
sh ./bin/init_auth.sh
sh ./bin/init_game.sh
```
5. After running this command stop the foreman and then again start it.

Now the API can be run using httpie.

## ENDPOINT 1:
For registering an user: @app.route("/register", methods=["POST"])
```bash
# http POST http://tuffix-vm/register/ username={yourname} password={yourpassword}
```
## ENDPOINT 2:
For authenticating the user:@app.route("/auth", methods=["GET"])
```bash
Ex: On postman with Basic-Auth: http://tuffix-vm/auth
note: this is no longer available externally, but other endpoints will make use of it
```
## ENDPOINT 3: 
For creating a new game for an authenticated user:@app.route("/game/", methods=["POST"])
```bash
# http --auth {yourname}:{yourpasswrod} POST tuffix-vm/game
```
## ENDPOINT 4:
For getting the game state of the authenticated user:@app.route("/game/:gameId", methods=["GET"])
```bash
# http --auth {yourname}:{yourpasswrod} GET tuffix-vm/game/gameId
``` 
## ENDPOINT 5:
List all the games for the authenticated user:@app.route("/my-games", methods=["GET"])
```bash
# http --auth {yourname}:{yourpasswrod} GET tuffix-vm/my-games
```
## ENDPOINT 6:
Guessing a word: @app.route("/game/:gameId", methods=["PATCH"])
```bash
# http --auth {yourname}:{yourpasswrod} PATCH tuffix-vm/game/gameId word={5 letter guess}
```
## ENDPOINT 7:
Resetting the leaderboard to empty: @app.route("/resetleaderboard", methods=["POST"])
```bash
# http POST http://127.0.0.1:5400/resetleaderboard
```
## ENDPOINT 8:
Viewing the top 10 on the leaderboard: @app.route("/leaderboard", methods=["GET"])
```bash
# http http://127.0.0.1:5400/leaderboard
```


   
