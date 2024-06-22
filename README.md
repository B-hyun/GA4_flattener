
RDB에서 사용하기위해 GA4 데이터를 Flat 테이블로 분리하기 위한 오픈소스를 소개한다. 

관련해서는 먼저 내 블로그에서도 확인 할수 있다. 
https://fantasy-story.tistory.com/4
https://fantasy-story.tistory.com/29


구글클라우드가 익숙하지 않다면 어느정도는 리서치가 필요하다. 
이대로 구현하면 중첩되어 있는 GA4 테이블을 RDB에서 전체 RAW를 활용 가능하다. 

[폴더]
*cf : Flat 기본 테이블 생성용 Cloud Functions 메인 소스 (Intraday 제외 테이블추출)
*cfconfigbuilder : Config 파일 생성 Cloud Functions 소스 (사용자 수동 호출용)
*cfconfigbuilderps : Config 파일 생성 Cloud Functions 소스 (pub/sub 수신용)
*cfintraday : Flat intraday 테이블 생성용 Cloud Functions 소스
*cfintradaysqlview : Flat intraday view 생성용 Cloud Functions 소스
*sample_config : GA4-F Config 샘플 (GCS 로드용)
*tests : 각 모듈 테스트용 소스
*tools : 단위 테스트 & 테이블 삭제용 소스 

[PY파일]
*dm_helper.py : GA-F 매개변수 config 소스 (auditlog쿼리 및 deployment-manager에서 생성하는 네이밍룰설정)
*dmt_bucket.py : deploymentmanager-gcs 버킷 생성 템플릿
*dmt_cloud_function.py : deploymentmanager-Cloud Functions 생성 템플릿
*dmt_log_metric.py : deploymentmanager-log 매트릭 생성 템플릿
*dmt_log_router.py : deploymentmanager-log sink 생성 템플릿
*dmt_pubsub_topic.py : deploymentmanager-pub/sub topic 생성 템플릿

[YAML파일]
*ga_flattener.yaml : deploymentmanager 실행 YAML (config 파일 생성시 수동 호출 방식) 
*ga_flattener_colon.yaml : deploymentmanager 실행 YAML (config 파일 생성시 pub/sub 방식) 

자세한 내용은 아래 URL 참고 가능하다.
------------------------------------------------------------
https://medium.com/@vishwanathmuthuraman_92476/how-to-flatten-the-ga4-bigquery-export-schema-for-usage-in-relational-databases-a4a2cdc13fd6
https://github.com/adswerve/google_analytics_flattener_ga4
