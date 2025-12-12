# JDBC-Comeback
# JDBC - Comeback Prep
Connecting JDBC with PostgresSQL
```java
import java.sql.*;
public class demojdbc1 {

    public static void main (String[] args) throws ClassNotFoundException, SQLException {
        String url="jdbc:postgresql://localhost:5432/Demo";
        String uname="postgres";
        String pwd="Sai@572charan24";
        String q1="select id from \"Tab1\" where id=1 ";
        Class.forName("org.postgresql.Driver");
        Connection con=DriverManager.getConnection(url,uname,pwd);
        Statement st=con.createStatement();
        ResultSet rs=st.executeQuery(q1);
        while(rs.next()){
            int id=rs.getInt("id");
            System.out.println(id);
        }

        con.close();
        System.out.println("done");
    }
}
```
Executing CRUD operations:
```java
import java.sql.*;
public class demojdbc1 {

    public static void main (String[] args) throws ClassNotFoundException, SQLException {
        String url="jdbc:postgresql://localhost:5432/Demo";
        String uname="postgres";
        String pwd="Sai@572charan24";

        Class.forName("org.postgresql.Driver");
        Connection con=DriverManager.getConnection(url,uname,pwd);
        Statement st=con.createStatement();

        String q1="insert into \"Tab1\" values(4,'tej')";
        String q2="update \"Tab1\" set id=7 where name='sai'";
        String q3="delete from \"Tab1\" where id=3";
        boolean status=st.execute(q1);
        boolean status2=st.execute(q2);
        boolean status3=st.execute(q3);
        System.out.println(status);
        System.out.println(status2);
        System.out.println(status3);
        con.close();
    }
}
```
Output in java:  
false  
false  
false   
This does NOT mean the insert failed.  
It means: “No ResultSet was produced.”  
Use executeUpdate() instead of execute().  




