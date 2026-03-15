1. Conceptualization
Project Title: 오픈소스 금융 라이브러리를 활용한 주식 전략 분석 및 공유 플랫폼: Stock-Flow (또는 Stock-Hub)

(Logo) - option
(이 부분에는 상승하는 그래프나 돋보기 모양의 로고 아이콘을 삽입하세요)

Student No, Name, E-mail:

Student No: 22220926

Name: 김준영

E-mail: rudnw2021@naver.com

GitHub: https://github.com/Kl-J0/Stock-Flow

[ Revision history ]

Revision date	Version #	Description	Author
03/15/2026	1.00	초안 작성(First Draft)	김준영
= Contents =

Business purpose

System context diagram

Use case list

Concept of operation

Problem statement

Glossary

References

1. Business purpose

1) Project background & Motivation
최근 개인 투자자들의 주식 시장 참여가 급증했지만, 방대한 금융 데이터를 일반인이 분석하기에는 한계가 있습니다. 특히 다양한 오픈소스 금융 라이브러리(예: Pandas-datareader, Backtrader 등)가 존재함에도 불구하고 개발 지식이 없는 투자자들은 이를 활용하지 못하고 있습니다. 이에 누구나 오픈소스 알고리즘을 활용해 주가를 분석하고 전략을 공유할 수 있는 플랫폼을 기획했습니다.

2) Goal

데이터 시각화: 오픈소스 라이브러리를 활용한 실시간 주가 차트 및 보조지표 제공.

전략 백테스팅: 사용자가 설정한 매매 전략이 과거 데이터에서 얼마나 유효했는지 시뮬레이션 기능 제공.

커뮤니티 기반 집단지성: 자신의 매매 알고리즘을 오픈소스로 공개하고 토론하는 환경 구축.

3) Target market

데이터 기반의 객관적인 투자를 원하는 개인 투자자.

자신의 퀀트(Quant) 알고리즘을 검증하고 공유하고 싶은 주니어 개발자 및 분석가.

2. System context diagram

System: Open-Stock Analysis Platform (본 시스템)

External Actors:

User (Investor): 주가 조회, 분석 리포트 열람, 매매 전략 설정.

Financial Data API (Yahoo Finance, KRX 등): 실시간 주식 시세 및 기업 재무 제표 데이터 제공처.

Open-source Library Server: 알고리즘 계산을 위한 분석 엔진.

Administrator: 시스템 유지보수 및 사용자 커뮤니티 관리.

3. Use case list

ID	Use Case Name	Actor	Description
1	실시간 시세 조회	User	특정 종목의 현재가, 호가, 거래량 등을 실시간으로 확인한다.
2	기술적 지표 설정	User	이동평균선, RSI, MACD 등 분석에 필요한 지표를 차트에 추가한다.
3	전략 백테스팅 실행	User	과거 데이터를 바탕으로 특정 매매 조건의 수익률을 계산한다.
4	분석 리포트 공유	User	자신이 분석한 차트와 전략을 커뮤니티 게시판에 업로드한다.
5	관심 종목 알림 설정	User	특정 가격 도달 시 푸시 알림을 받도록 설정한다.
6	데이터 소스 관리	Admin	API 연동 상태를 확인하고 최신 금융 데이터를 업데이트한다.
4. Concept of operation

1) 실시간 시세 및 지표 분석 (Real-time Analysis)

Purpose: 사용자에게 시각화된 투자 판단 자료를 제공함.

Approach: 오픈소스 차트 라이브러리를 연동하여 사용자가 선택한 지표를 실시간으로 렌더링함.

Dynamics: 사용자가 종목명을 검색하고 차트 도구를 선택할 때 발생.

Goals: 지연 시간 없는 정확한 금융 데이터 시각화.

2) 전략 백테스팅 (Strategy Backtesting)

Purpose: 실제 투자 전 매매 전략의 유효성을 검증함.

Approach: Python 기반의 오픈소스 백테스팅 엔진을 사용하여 과거 10년치 데이터를 시뮬레이션함.

Dynamics: 사용자가 '매수 조건'과 '매도 조건'을 입력 후 실행 버튼을 누를 때 발생.

Goals: 수익률, MDD(최대 낙폭) 등 상세 통계 리포트 생성.

5. Problem statement

1) 데이터 정확성 및 지연 (Data Reliability): 무료 오픈소스 API를 사용할 경우 유료 데이터에 비해 10~15분 지연이 발생할 수 있습니다. 이를 사용자에게 명확히 공지하고, 중요 데이터는 캐싱 기술을 통해 속도를 개선해야 합니다.

2) 서버 부하 관리 (Technical Difficulty): 수많은 사용자가 동시에 백테스팅 알고리즘을 돌릴 경우 서버에 과부하가 올 수 있습니다. 이를 해결하기 위해 비동기 처리(Celery 등)와 큐 시스템을 도입해야 합니다.

3) NFRs (비기능적 요구사항):

금융 데이터를 다루므로 데이터 무결성이 보장되어야 함.

차트 로딩 속도는 2초 이내여야 함.

모바일 환경에서도 차트 조작이 원활해야 함 (반응형 설계).

6. Glossary

Backtesting: 과거 데이터를 사용하여 특정 투자 전략이 어떤 성과를 냈을지 시험하는 과정.

Candlestick Chart: 시가, 고가, 저가, 종가를 봉 형태로 나타낸 차트.

API (Application Programming Interface): 외부 시스템으로부터 주식 데이터를 가져오기 위한 접점.

7. References

Yahoo Finance API Documentation: https://finance.yahoo.com/

Pandas-datareader Open-source Library: https://github.com/pydata/pandas-datareader

Backtrader Library: https://www.backtrader.com/

기존 오픈소스 설계 예시 파일 (Example 1~8) 구조 및 양식 참조.
