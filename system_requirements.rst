.. index::
    single: Requirements

System Requirements
===================

OroCRM is a web application which runs on a server. Users interact with the application via a web browser on any computer or mobile device that have access to the internet or the network where the server is hosted.


Server-side Requirements
------------------------

Resources
~~~~~~~~~

Resources configuration depends on the data size and number of active users and integrations. Typical setup could be done on a single server with the minimum of 2 CPU cores, 2GB RAM and a fast hard drive (SSD is recommended). The application could scale to multiple servers and a separate database server based on the expected load.


Operating Systems
~~~~~~~~~~~~~~~~~

Linux distributions (RedHat, Ubuntu, Debian, CentOS) are recommended for the production setup.
Windows 7 and above and Mac OS X can be used for the development environment.

Software
~~~~~~~~

Oro applications are compatible with most web servers with PHP support, but we recommend the following configuration:

+-------------------+---------------------------------------------------+
| *Web Server*      | * `Apache`_ 2.2.x or 2.4.x                        |
|                   | * `Nginx`_ latest mainline or stable version      |
|                   |                                                   |
|                   | Web server configuration recommendations are well |
|                   | described in `Symfony documentation`_             |
+-------------------+---------------------------------------------------+
| *PHP*             | * `PHP`_ 7.X                                      |
|                   | * PHP CLI, the same version as for the web server |
+-------------------+---------------------------------------------------+
| *PHP Settings*    | Few updates to default PHP configuration settings |
|                   | should be done in php.ini for the web server and  |
|                   | CLI:                                              |
|                   |                                                   |
|                   | * date.timezone must be set                       |
|                   | * detect_unicode must be disabled                 |
|                   | * memory_limit should be 512M or above            |
|                   |                                                   |
|                   | If you have xdebug installed (not recommended in  |
|                   | the production setup):                            |
|                   |                                                   |
|                   | * xdebug.scream must be disabled                  |
|                   | * xdebug.show_exception_trace must be disabled    |
|                   | * xdebug.max_nesting_level above 100              |
+-------------------+---------------------------------------------------+
| *PHP Extensions*  | * ctype                                           |
|                   | * curl                                            |
|                   | * fileinfo                                        |
|                   | * gd                                              |
|                   | * intl (ICU library 4.4 and above)                |
|                   | * json                                            |
|                   | * mbstring                                        |
|                   | * mcrypt                                          |
|                   | * mysql                                           |
|                   | * pcre                                            |
|                   | * simplexml                                       |
|                   | * tokenizer                                       |
|                   | * xml                                             |
|                   | * zip                                             |
+-------------------+---------------------------------------------------+
| *Database*        | * `MySQL`_ 5.1 and above                          |
+-------------------+---------------------------------------------------+
| *Process Control* | * `Supervisor`_ or alternative                    |
+-------------------+---------------------------------------------------+

Enterprise Edition Software
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Enterprise edition is built to support better scale and performance. It is compatible with additional software configuration that allows to achieve these goals.

+-------------------+----------------------------------------------------+
| *PHP Extensions*  | * pgsql                                            |
+-------------------+----------------------------------------------------+
| *Database*        | * `PostgreSQL`_ / `EnterpriseDB`_ 9.1 and above    |
+-------------------+----------------------------------------------------+
| *Search Index*    | * `Elasticsearch`_ 2.x                             |
+-------------------+----------------------------------------------------+
| *Job Queue*       | * `RabbitMQ`_ 3.5.8 and above, 3.6.x is recommended|
+-------------------+----------------------------------------------------+

**PostgreSQL Configuration**

PostgreSQL `uuid-ossp` extension should be loaded for proper doctrine's `guid` type handling. In order to enable it, connect to the database server and run sql query:

.. code-block:: sql

    CREATE EXTENSION "uuid-ossp";


Optional recommendations
~~~~~~~~~~~~~~~~~~~~~~~~

* `Node.js`_ could be used for more efficient JS assets minification
* `Tidy PHP extension`_ should be installed to make sure that HTML is correctly converted into a text representation
* `Redis`_ - could be used for more efficient application caching. Supported versions of Redis from 2.0 to 3.2


Client-side Requirements
------------------------

On the client side, Oro applications could be used with most of the graphical browsers on any operating system.
Recommended and supported browsers are:

 * `Mozilla Firefox`_ (latest)
 * `Google Chrome`_ (latest)
 * `Microsoft Internet Explorer`_ 10 and above
 * `Microsoft Edge`_ (latest)
 * `Safari`_ (latest)

.. note::

    Any browser you use needs to have cookies and JavaScript turned on.

.. _`Apache`: https://httpd.apache.org/
.. _`Elasticsearch`: https://www.elastic.co/products/elasticsearch
.. _`EnterpriseDB`: https://www.enterprisedb.com/
.. _`Google Chrome`: https://www.google.com/chrome/
.. _`Microsoft Edge`: https://www.microsoft.com/en-us/windows/microsoft-edge
.. _`Microsoft Internet Explorer`: https://www.microsoft.com/en-us/download/internet-explorer.aspx
.. _`Mozilla Firefox`: https://www.mozilla.org/en-US/firefox/new/
.. _`MySQL`: https://www.mysql.com/
.. _`Nginx`: https://www.nginx.com/
.. _`Node.js`: https://nodejs.org/en/
.. _`PHP`: https://secure.php.net/
.. _`PostgreSQL`: https://www.postgresql.org/
.. _`RabbitMQ`: https://www.rabbitmq.com/
.. _`Redis`: https://redis.io/
.. _`Safari`: http://www.apple.com/safari/
.. _`Supervisor`: http://supervisord.org/
.. _`Symfony documentation`: http://symfony.com/doc/2.8/setup/web_server_configuration.html
.. _`Tidy PHP extension`: http://php.net/manual/en/book.tidy.php
.. _`Xdebug`: https://xdebug.org/
