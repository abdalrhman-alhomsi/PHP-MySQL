PHP MySQL
===

PHP-MySQL provides two classes which aim to make the execution of queries
against a MySQL engine more organized and powerful. By routing all queries
through a connection wrapper and an instantiable **MySQLQuery** class, queries
can be analyzed, recalled, and their connections shared, more efficiently.

As an example, the **getDuration** method on a **Query** object gives you the
ability to determine a queries execution length/duration. Similarly, the static
**MySQLConnection** method **getStats** provides statistics on the number of
queries executed grouped by type, as well as a collection of the total queries
executed during the length of the request.

### Sample MySQL Connection

    // load dependency
    require_once APP . '/vendors/PHP-MySQL/MySQLConnection.class.php';
    
    // database credentials and connection
    $database = array(
        'host' => 'localhost',
        'port' => 3306,
        'username' => '<username>',
        'password' => '<password>'
    );
    MySQLConnection::init($database);
    
    // output resource object
    $resource = MySQLConnection::getLink();
    print_r($resource);
    exit(0);

### Sample MySQL Query

    // load dependencies
    require_once APP . '/vendors/PHP-MySQL/MySQLConnection.class.php';
    require_once APP . '/vendors/PHP-MySQL/MySQLQuery.class.php';
    
    // database credentials and connection
    $database = array(
        'host' => 'localhost',
        'port' => 3306,
        'username' => '<username>',
        'password' => '<password>'
    );
    MySQLConnection::init($database);
    
    // database select; query; output
    (new MySQLQuery('USE `mysql`'));
    $query = (new MySQLQuery('SELECT * FROM `user`'));
    print_r($query->getResults());
    exit(0);