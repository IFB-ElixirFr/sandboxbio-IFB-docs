## Installation tutorial



!!! warning "Requirement"

    Node.js and npm are required. Please install them before this tutorial.


=== "For local installation"

    ####Fork, clone or download this project

    ```bash
    git clone git@github.com:sandbox-bio/sandbox.bio.git
    ```

    ####Install all required packages for Sandbox.bio

    step 1

    ```bash
    cd sandbox.bio
    npm install
    ```
    step 2

    ```bash
    cd app
    npm install
    ```
    #### Build the sandbox.bio app
    
    ```bash
    npm run build
    npm run dev
    ```
    If everything went well you see a message like this below.

    ```bash
    Your application is ready~! 🚀
    
      - Local:      http://0.0.0.0:1111
      - Network:    http://xx.xxx.xx.xx:1111
    ```

=== "For server install with nginx"

    #### Install ngnix

    We recommend [this tutorial](https://ubuntu.com/tutorials/install-and-configure-nginx#1-overview) for installing nginx and have adapted the following steps.

    #####3.Creating our own website

    We're using a "sandbox" folder instead of "tutorials".

    ```bash
    cd /var/www
    sudo mkdir sandbox
    cd sandbox
    sudo nano index.html
    ```

    #####4. Setting up virtual host

    In /etc/nginx/sites-enabled we create the sandbox file

    ```bash
    cd /etc/nginx/sites-enabled
    sudo nano sandbox
    ```


    We define the `root` and `server name` variables as shown below.

    ```bash
    server {
        listen 80;
        listen [::]:80;
        
        server_name sandbox.bio.france-bioinformatique.fr;
        
        root /var/www/sandbox/bio;
        index index.html;

        location / {
               try_files $uri $uri/ =404;
       }
    }
    ```

    ####Fork, clone or download this project

    ```bash
    cd /var/wwww
    git clone git@github.com:sandbox-bio/sandbox.bio.git
    ```

        ####Install all required packages for Sandbox.bio

    step 1

    ```bash
    cd sandbox.bio
    npm install
    ```
    step 2

    ```bash
    cd app
    npm install
    ```

    #### Build the sandbox.bio app
    
    ```bash
    npm run build
    npm run dev
    ```

    #### We're adapting nginx to run sandbox.bio

    ```bash
    cd /etc/nginx/sites-enabled
    sudo nano sandbox
    ```

    ```bash
        server {
           listen         80;
           server_name    sandboxbio.france-bioinformatique.fr;
           return         301 https://$server_name$request_uri; #Redirection
    }
    server {
            listen         443 ssl;
            listen [::]:443 ssl;
            server_name sandboxbio.france-bioinformatique.fr;
    
             root /var/www/sandbox.bio/app/public;
            index index.html;
           location / {
            try_files $uri $uri/ =404;
    
           }
    }
    ```

    #### Restart Nginx

    ```bash
    sudo service nginx restart
    ```

