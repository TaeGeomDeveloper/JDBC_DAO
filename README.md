# JDBC_DAO
데이터베이스 접근 객체

## DB CRUD    : DAO 클래스    Public class GisaDao

### 컨낵션 객체 가져오기
```JAVA
  Connection con = ConnectionManager.getConnection();
```

### 쿼리 작성
``` JAVA
   String sql = "SELECT * FROM gisa3 WHERE local_code = ?";
```

### 삽입
``` JAVA
  1) 삽입 준비하기
  Statement stmt = con.createStatement();
  2) 특정한 쿼리만 통과 하는 전용 통로 작성.
  PreparedStatement pstmt = con.prepareStatement(sql);
  
  삽입 하기
  1) int affectedCount = stmt.executeUpdate(sql);
  
  2) ResultSet rs = pstmt.executeQuery();
  
```

### 테이블 값 구하기
``` JAVA
  다음행 실행하기
  if(rs.next()) {
            result = rs.getInt(1);
       }
```
