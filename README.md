# Book_data_crawling

# 목표
교보문고 각 카테고리 별 이미지, 이미지url , title , 작가 , 출판사 , 한줄평 데이터 수집 <br> 
<br>
<br>
<br>
# 현재까지 진행상황 

1/20 : 기본적인 접근 및 크롤링 단계 구조화 완료 
<br>
1/21 : 기본적인 이미지 접근 및 이미지 수집 폴더 생성 + 다운 코드 작성 
<br> 
1/22 : 이미지 다운 문제 해결 + 전반적인 진행 흐름 재설정 
<br> 
1/23 : Frame을 빠져나와 상세화면으로 돌아가기 설정 완료 
<br>
1/24 : 전반적인 리팩토링, 한 페이지의 이미지들 크롤링 작업화 완료 + 다음 페이지로 이동 부분 구현화 ( 세부 작업 필요 ) 
<br>
1/25 : 각 index를 구분지어, 해당 index조건이 충족되었을 때 다음페이지로 이동하도록 설정하기 완료 ( 성능부분은 글쎄... 이후, 리팩토링 작업을 통한 최적화 작업 진행하면 더 좋은 성능을 뽑아낼수 있을것으로 예상) 

<br>

# 문제점 
1/21 이미지 path 접근까지 완료하였는데 이미지 수집이 진행되지 않고 없는 요소라고 에러가 뜸 
<br> 
1/23 이미지 수집 후, 창을 닫고 이전 화면으로 돌아가고 싶은데, Frame 설정을 해제해 줘도 driver.back()이 작동하지 않음  <br>
1/25 수집과정에서 크게보기가 없어 path가 달라 수집이 안되는 경우 발생 , title 명에 / 이 포함되어 있어 해당 폴더에 들어가지 않고 경로로 판단하여 저장이 안되는 경우 발생 
<br>
# 해결
1/22 : 각 웹 페이지안에 페이지를 띄운형태로 존재하여 dirver.switch_to.frame을 이용해 해당 frame으로 접근을 시도해야했음 
<br>
1/24 : 상세보기 이동으로 인한 history가 중첩되어 있는것으로 추정됨, 2번을 하니 뒤로가기가 제대로 작동이 되었음 
<br>
1/25 : title을 chr()로 문자열 변환을하여 해당 부분 문제 해결 

# 개선 방안 
1. Selenium + BeautifulSoup을 활용하여 Selenium으로 페이지 넘겨주고, BeautifulSoup로 데이터 수집하면 현재보다 더 빠르게 진행할수있지않을까 라는 고민 <br> 
2. 현재는 단일 데이터이기에 단일 프로세싱으로 진행하였지만, 이후 DB관련 데이터들을 크롤링할때는 multiProcessing을 통해 데이터 크롤링을 하면 더 좋은 성능을 낼 수 있을것으로 예상 (Mutex 예방) 
