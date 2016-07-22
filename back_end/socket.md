*select* - 
다중 입출력 함수로 I/O를 처리하는 경우 non-blocking으로 여러 파일을 체크 하면서 읽어들일 테이터가 어떤 상태인지 확인하여 
변화가 있따면 해당 파일을 리턴. 만일 변화가 없다면 block 상태가 되며 timeout 으로 빠져 나옴. sleep 대신 select를 사용할 
수 있음

*poll*- select 와 마찬가지로 파일지시자의 이벤트를 기다리다가 이벤트가 발생하면, poll 에서의 block 이 해제되고, 
다음 루틴에서 어떤 파일지시자에 이벤트가 발생했는지 검사하는 방식을 사용

select 와 poll의 차이는 select는 모든 입출력을 검사하며 입출력이 갱신시 모든 입출력을 복사하여 그만큼 자원의 소비가 큼
poll의 경우 지정한 입출력들만 검사하며 리턴되는 값이 select의 파일지시자인것에 비해해당 객체를 리턴함 (정보를 많이 리턴)

* poll은 소켓 프로그래밍에서 해당 소켓이 살있는지 활성화 상태인지 확인에 많이 쓴다.

epoll poll의 확장 형태로 특정 이벤트의 준위 상태에 따라 동작한다. 해당 이벤트가 발생한 시점(Edge Triggered)과 
발생중인 시점(Level triggered)으로 준위가 나뉘며 이는 기존의 속도 뿐만 아니라 데이터를 많이 보낼수 있게 되었다. 
epoll은 non-blocking I/O에서 효율적이지만 표준사항이 아니기에 기타 유닉스에서 쓸수 없다. (커널 2.6버전 이상 지원)