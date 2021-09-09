# Main Senario
1. 세탁기 선택
> 1. 세탁기 리스트로부터 세탁기 UUID를 이용하여 예약 선택


2. 신청하기
> 1. washing machine uid에 woomam_wms의 bookedTime, phoneNumber 갱신  

3. QR코드 본인인증
> 1. woomam_wms 의 unchecked -> verified

4. 빨래선택
> 1. 포인트 상태 확인 및 포인트 차감 : point 차감된 결과 서버에 POST로 전송 -> user table의 point 수정   
> 2. POST로 woomam_wms의 TABLE UPDATE


5. 수거 전 QR 본인인증 및 종료   
> 1. woomam_wms의 세탁기 UUID에 해당하는 특정 row를 초기화

6. 포인트 충전  
> 1. 인앱결제로 카카오페이 테스트계정 연동, 
> 2. 결제된 결과 서버에 갱신 POST로 user 정보 다 준다.

---

## Things to be added
- [ ] add features with `POINT`
- [ ] make in-app purchase with sth like Kakaopay


