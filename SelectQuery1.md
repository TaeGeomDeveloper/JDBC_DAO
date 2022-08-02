# DAO

## SekectQuery
```java
public int selectQuery1(String query) throws SQLException {
        // 컨낵션 필요
        Connection con = ConnectionManager.getConnection();
        int result = 0;
        PreparedStatement pstmt = con.prepareStatement(query);
        ResultSet rs = pstmt.executeQuery();
        if(rs.next()) {
            result = rs.getInt(1);
        }
        // 주의 확인
        ConnectionManager.closeConnection(rs,pstmt,con);
        return result;
    }

```
