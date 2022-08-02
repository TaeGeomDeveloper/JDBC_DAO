
## InsertData

``` java

public boolean insertData(ArrayList<StudentVO> list) throws SQLException {
        boolean flag = false;
        int affectedCount = 0;
        // 컨넥션 객체 가져오기
        Connection con = ConnectionManager.getConnection();
        Statement stmt = con.createStatement();
        
        // 삽입 쿼리
        for(StudentVO vo : list) {
            String sql = "INSERT INTO gisa3 VALUES (" + vo.getStdNo() + ",'" + vo.getEmail() + "'," +
                vo.getKor() + "," + vo.getEng() + "," + vo.getMath() + "," +
                vo.getSci() + "," + vo.getHist() + "," + vo.getTotal() + ",'" +
                vo.getMgrCode() + "','" + vo.getAccCode() + "','" + vo.getLocCode() + "')";
            // 삽입 준비
            stmt = con.createStatement();
            // 삽입
            affectedCount += stmt.executeUpdate(sql);
        }
        
        // 연결된 통로 모두 닫기
        lesson.jdbc.day4.ConnectionManager.closeConnection(null,stmt,con);

        // 삽입 준비
        //Statement stmt = con.createStatement();

        // 삽입
        //affectedCount += stmt.executeUpdate(sql);
        if(affectedCount > 0) {
            flag = true;
        }
        return flag;


    }

```
