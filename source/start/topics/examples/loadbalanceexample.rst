
.. meta::
   :description: An example NGINX configuration that performs simple load balancing.

Simple Load Balancing
=====================

nginx.conf
----------

.. code-block:: nginx

  http {
    upstream myproject {
      server 127.0.0.1:8000 weight=3;
      server 127.0.0.1:8001;
      server 127.0.0.1:8002;    
      server 127.0.0.1:8003;
    }

    server {
      listen 80;
      server_name www.domain.com;
      location / {
        proxy_pass http://myproject;
      }
    }
  }
