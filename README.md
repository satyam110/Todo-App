1. Install MongoDB Commuinty edition on your machine (You can follow any tutorial for installation)

2. After Pulling/Cloning the Git Repository follow these commands :

	a. inside todo app folder run $npm install
	
	b. CD into backend directory and again run $npm install

3. Now npm pakages are installed inside your app folder

4. Start the mongodb server by typing

	$mongo
	
	Note: If you encounter with ‘/data/db’ not found traceback to home directory and perform    	          these commands 
		1. $ sudo mkdir -p /data/db/
		2. $ sudo chown `id -u` /data/db 
5. Now you need to start node server, cd into backend folder then run $nodemon server
   
    Note: 1) If nodemon command not found encountered run $ npm install -g nodemon
	2) If you encounter with error “[nodemon] Internal watch failed: ENOSPC: System limit for 	number of file watchers reached”
	then run $ echo fs.inotify.max_user_watches=582222 | sudo tee -a /etc/sysctl.conf && sudo sysctl -p

6. Now change directory back, and run $ npm start

Thats’s it now your MERN Todo app is up and running, Thank you.