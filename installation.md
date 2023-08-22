# Install MySQL server
### ON Windows :



### ON Linux :
1. Open Terminal (Ctrl + Alt + T)
2. Run the following commands :- 

        $ sudo apt update
        $ sudo install mysql-server
        $ sudo systemctl start mysql.service

3. To open mysql bash run,

        $ sudo mysql
    
    To exit from the bash type exit. See below,

        mysql> exit

4. Configuring MySQL for passwords and security. Run the command
        
        $ sudo mysql_secure_installation
        
    You will get a message like this
        
        Securing the MySQL server deployment.

        Connecting to MySQL using a blank password.
        
        VALIDATE PASSWORD COMPONENT can be used to test passwords and improve security. It checks the strength of password and allows the users to set only those passwords which are secure enough. Would you like to setup VALIDATE PASSWORD component?
        
        Press y|Y for Yes, any other key for No: 
    
    Press y if you are using mysql for production or business purposes,
    
    else

    Press n if you are using mysql for learning purposes. 

    After selecting your desired mode.
    You'll might see text as below, 

        Skipping password set for root as authentication with auth_socket is used by default.
        If you would like to use password authentication instead, this can be done with the "ALTER_USER" command.
        See https://dev.mysql.com/doc/refman/8.0/en/alter-user.html#alter-user-password-management for more information.

        By default, a MySQL installation has an anonymous user, allowing anyone to log into MySQL without having to have a user account created for them. This is intended only for testing, and to make the installation go a bit smoother. You should remove them before moving into a production environment.
        
        Remove anonymous users? (Press y|Y for Yes, any other key for No) : 

    Press y if you want your user created and password set for your user, so that no one else can use your server if your localhost machine has access to many other people.
    
    Else, press n, this will allow direct access to the server without any authentication process and if any other user except you, uses your localhost machine, they can have access to the server too.

    After selecting your authentication type, you'll see text as below,

         ... skipping.


        Normally, root should only be allowed to connect from 'localhost'. This ensures that someone cannot guess at the root password from the network.
        
        Disallow root login remotely? (Press y|Y for Yes, any other key for No) : 
    
    Press y for denying permissions to access login remotely else press n.

    After that, you'll see text as below,

        By default, MySQL comes with a database named 'test' that anyone can access. This is also intended only for testing, and should be removed before moving into a production environment.


        Remove test database and access to it? (Press y|Y for Yes, any other key for No) : 

    Press y to remove the database else press n.
    (Pressing n recommended, if you are using mysql server for learning purposes.)

    After that you'll see text as below, 

         ... skipping.
        Reloading the privilege tables will ensure that all changes made so far will take effect immediately.
        
        Reload privilege tables now? (Press y|Y for Yes, any other key for No) : 

    Press y (recommended).

5. If by any chance you get an error message at the VALIDATE PASSWORD message after selecting n option, do the following steps.
    - Open new terminal and type the command,

            $ sudo mysql
    - Your sql bash will open, then type the command, 
    
        ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'your password'; 
        
        See below,

            mysql> ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'root'; 

6. Install WorkBench GUI for MySQL.
    - Go to chrome and search snap mysql-workbench-community
    - You will see a link from snapcraft.io for installing mysql-workbench-community. Click on it.
    - Click on the install button 
    - Copy the command provided on the website for downloading the workbench. It'll be similar to the one below, 
    
            $ sudo snap install mysql-workbench-community

    - Note: if snap isn't already installed in your system, follow the commands provided on the website or follow as below,

            $ sudo apt update
            $ sudo apt install snapd
    
        Now, re run the previous workbench command and your workbench should be installed succesfully.