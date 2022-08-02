# JDBC_DAO
데이터베이스 접근 객체

```java
public ArrayList<StudentVO> selectQuizeData() throws SQLException {
        ArrayList<StudentVO> list;
        list = new ArrayList<>();
        // 컨택션 정보
        Connection con = ConnectionManager.getConnetion();

        // 쿼리 부분
        String sql = "SELECT * FROM gisa3";
        // 특정한 쿼리만 통과 하는 전용 통로 작성.
        PreparedStatement pstmt = con.prepareStatement(sql);
        ResultSet rs = pstmt.executeQuery();

        // 쿼리 처리
        StudentVO vo;
        // 테이블의 데이터를 원하는 부분만큼 저장해야함.
        // VO를 이용해서 컬랙션에 저장.
        while(rs.next()){
            vo = new StudentVO(rs.getInt(1),
                    rs.getString(2),
                    rs.getInt(3),
                    rs.getInt(4),
                    rs.getInt(5),
                    rs.getInt(6),
                    rs.getInt(7),
                    rs.getInt(8),
                    rs.getString(9),
                    rs.getString(10),
                    rs.getString(11));
            list.add((vo));
        }

        ConnectionManager.closeConnection(rs,pstmt,con);
        return list;
    }

```
