# More configurations

* You can specify 'down' keyword to a server which will mark it as down and will not handle any traffic like below:

    upstream backend-servers {
        server avengers:5678;
        server justice-league:5678 down;
    }

* You can mark a server as backup server, which will keep on running but wont handle any requests until the primary servers are down

    upstream backend-servers {
        server avengers:5678 backup;
        server justice-league:5678; 
    }

* You can read about more configuration options on this documentation

https://docs.nginx.com/nginx/admin-guide/load-balancer/http-load-balancer/