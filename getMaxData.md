
## getMaxData

``` java
 public int getMaxData(String query) throws SQLException {
        // 컨낵션 필요
        Connection con = ConnectionManager.getConnection();
        int result = 0;
        PreparedStatement pstmt = con.prepareStatement(query);
        ResultSet rs = pstmt.executeQuery();
        if(rs.next()) {
            result = rs.getInt(1);
        }
        // 주의 확인
        rs.close();
        pstmt.close();
        con.close();

        return result;
    }

```
