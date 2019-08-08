### pymysql
---
https://github.com/PyMySQL/PyMySQL

```py
import pymysql.cursors

connection = pymysql.connect(host='localhost',
  user='user',
  password='passwd',
  db='db',
  charset='utf8mb4',
  cursorclass=pymysql.cursors.DictCursor)
try:
  with connection.cursor() as cursor:
    sql = "INSERT INTO `users` (`email`, `password`) VALUES (%s, %s)"
    cursor.execute(sql, ('webmaster@python.org', 'very-secret'))

  connection.commit()
  
  with connection.cursor() as cursor:
    sql = "SELECT `id`, `password` FROM `users` WHERE `email`=%s"
    cursor.execute(sql, ('webmaster@python.org',))
    result = cursor.fetchone()
    print(result)
finally:
  connection.close()

```

```sh
python3 -m pip install PyMySQL
python3 -m pip install PyMySQL[rsa]
```

```sql
CREATE TABLE `users` (
  `id` int(11) NOT NULL AUTO_INCREMENT,
  `email` varchar(255) COLLATE utf8_bin NOT NULL,
  `password` varchar(255) COLLATE utf8_bin NOT NULL,
) ENGINE=InnoDB DEFAULT CHARSET=utf8 COLLATE=utf8_bin
AUTO_INCREMENT=1 ;
```
