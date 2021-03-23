
# @Transactional
+ update시에는 save를 명시적으로 하지않고 @transactional 사용
+transaction 범위를 잡아주는 동시에 이 범위에서 처리가 벗어났을 때 DB에 내용 적용됨

