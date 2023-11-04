# SQL Injection (mitigation)
Ini adalah pertahanan terbaik terhadap SQL injection, yaitu dengan data sebagai satu kesatuan yang terikat pada kolom tanpa interpretasi. 

## Try it! Writing safe code
```sh
getConnection
PreparedStatement
prepareStatement
?
?
statement.setString(1, name)
statement.setString(2, mail)
```

## Try it! Writing safe code
- Tuliskan source code berikut ini kemudian tekan tombol **Submit**
```sh
try {
    Connection conn = DriverManager.getConnection(DBURL, DBUSER, DBPW);
    PreparedStatement statement = conn.prepareStatement("SELECT status FROM users WHERE name=? AND mail=?");
    statement.setString(1, "name");
    statement.setString(2, "mail");
    statement.executeUpdate();
} catch (Exception e) {
    System.out.println("Oops. Something went wrong!");
}
```