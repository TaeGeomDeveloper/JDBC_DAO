
## InsertDataV2

```Java
public boolean InsertDataV2(ArrayList<StudentVO> list) throws SQLException {
        boolean flag = false;
        Connection con = ConnectionManager.getConnection();

        String sql = "INSERT INTO gisa3 values (?,?,?,?,?,?,?,?,?,?,?)";
        // 특정한 쿼리만 통과 하는 전용 통로 작성.
        PreparedStatement pstmt = con.prepareStatement(sql);
        int count = 0;
        for( StudentVO vo : list) {
            //vo = list.get(0);
            pstmt.setInt(1, vo.getStdNo());
            pstmt.setString(2, vo.getEmail());
            pstmt.setInt(3, vo.getKor());
            pstmt.setInt(4, vo.getEng());
            pstmt.setInt(5, vo.getMath());
            pstmt.setInt(6, vo.getSci());
            pstmt.setInt(7, vo.getHist());
            pstmt.setInt(8, vo.getTotal());
            pstmt.setString(9, vo.getMgrCode());
            pstmt.setString(10, vo.getAccCode());
            pstmt.setString(11, vo.getLocCode());
            count += pstmt.executeUpdate();
        }

        if(count > 0) flag = true;

        pstmt.close();
        con.close();

        return flag;
    }

```
