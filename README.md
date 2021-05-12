# 산업별 매출, 주식 데이터 분석을 통한 산업의 변화 탐색적 분석
최근 국내 주식 시장의 성장과 함께 사람들의 주식에 대한 관심이 커졌다. 팀은 종목별 주가 데이터가 아닌 산업별 매출, 시가총액 데이터의 분석을 통해 국내 산업에 관한 이해를 높이고자 EDA 프로젝트를 수행하였다.

[EDA_PROJECT.slide](https://docs.google.com/presentation/d/1Csl1MLUTw5lVrj_WnfCUEIMFXts95V_eYx0El8KG378/edit?usp=sharing)

***
## 1. 개요
### 1-1. 목적
- 산업별 시가총액, 시장규모, 영업이익, 매출, 회사 수 변화 탐색 및 분석 
- 산업간 매출, 시가 총액의 격차 등 종합적 탐색 및 분석
- ROE, PER 기준으로 산업별 투자 전략 탐색 및 분석

### 1-2. 데이터셋
- 데이터
    - 코스닥 산업별 수익현황 2004-2019.csv
    - 코스피 산업별 수익현황 2004-2019.csv
    - 코스닥 산업별 시가총액 2004-2019.csv
    - 코스피 산업별 시가총액 2004-2019.csv
    - 업종별 국내 시장규모 2000-2018.csv

- 활용 범위
    - 2004년 ~ 2019년
- 출처
    - [KOSIS 국가통계포털](https://kosis.kr/index/index.do)
    - [ISTANS 산업통계종합포털](https://istans.or.kr/mainMenu.do)

### 1-3. 팀원 / 역할
- [이경무](https://github.com/rudan916) / 산업별 시가총액 데이터 확보 및 전처리, 산업별 분석 시각화, 발표자료 제작
- [김도겸](https://github.com/dockyum) / 산업별 수익현황 데이터 확보 및 전처리, 산업간 분석 시각화, 발표자료 제작, README 작성
- [고원진](https://github.com/wonjin77) / 업종별 국내 시장규모 데이터 확보 및 전처리, 산업 분류 체계 통힙(전처리), 투자 인사이트 발굴, 발표자료 제작, 발표

***

## 2. 핵심 요약
### 2-1. 산업별 분석
![merged graph](https://user-images.githubusercontent.com/18084336/108586725-9a3ce180-7393-11eb-92bf-fc17967a2d43.png)
산업분류 : 건설업, 통신업, 음식료품, 전기전자

표본 데이터 기준 산업별 영업이익과 회사수 증가 감소 요인은 지방 미분양 아파트 증가와 통신 4G 설비투자 대폭 증가 그리고 반도체 호황기 같은 시장변화 뿐만 아니라 상대적으로 특수한 사드배치 이슈와 같은 국제 정치적인 요인도 있다.

[merged_graph_1.ipynb](./merged_graph_1.ipynb)

### 2-2. 산업간 분석
1. 연간 자기자본이익률
![평균 자기자본이익률](https://user-images.githubusercontent.com/18084336/108587623-176a5580-7398-11eb-9736-9b1b17023588.png)
전 산업군에서 연간 자기자본이익률이 꾸준히 좋았던 산업은 '운수장비'와 '의약품' 이었다.

2. 시총, 매출, 영엽이익 관계
![시총, 매출, 영엽이익 관계](https://user-images.githubusercontent.com/18084336/108587984-163a2800-739a-11eb-90bb-0b3d4af26997.png)

3. 산업간 시가총액 비율
![산업간 시가총액 비율](https://user-images.githubusercontent.com/18084336/108588324-d8d69a00-739b-11eb-967c-d0fe11c3c8e9.png)
전기전자와 서비스업의 비중이 점점 증가하여 50%를 넘었다.

[norm_max_preprocessing.ipynb](./norm_max_preprocessing.ipynb)
[]()
### 2-3. 산업별 투자 분석
1. idea
    - PER이 낮은 기업(산업) / ROE가 높은 기업(산업)에 투자할 때 수익이 나는지 단순 back-testing
    - 해당 연도 및 산업군 historical 평균에 비해 PER 낮을 경우 / ROE가 높을 경우 매수 등
    - 해당 연도 및 산업군 historical 평균에 비해 PER 높을 경우 / ROE가 낮을 경우 매도 등

| 산업군 | PER 평균 이하 & ROE 평균 이하 | PER 평균 이하 & ROE 15 이상 | PER 평균 이하 | ROE 15 이상 | ROE 평균 이상 | Total |
|-----|--------|--------|--------|--------|--------|--------|
|건설업	|-1	|-4	|-7	|-1	|5	|-8|
|광업	|1	|1	|1	|1	|1	|5|
|기계	|-3	|-2	|-1	|-3	|-5	|-14|
|기타제조업	|-1	|-3	|-3	|-3	|1	|-9|
|농업, 임업 및 어업	|-4	|-5	|-7	|-3	|-1	|-20|
|비금속광물	|-1	|-3	|-1	|-5	|-1	|-11|
|서비스업	|4	|1	|7	|-5	|1	|8|
|섬유의복	|0	|-3	|-3	|-3	|3	|-6|
|운수장비	|0	|1	|1	|1	|-1	|2|
|운수창고업	|2	|0	|1	|-1	|3	|5|
|유통업	|5	2	|7	|-3	|3	|14|
|음식료품	|3	|-2	|3	|-7	|3	|0|
|의료·정밀기기	|1	|-2	|3	-7	|-1	|-6|
|의약품	|7	|0	|9	|-9	|5	|12|
|전기가스	|1	|0	|1	|-1	|1	|2|
|전기전자	|2	|1	|3	|-1	|1	|6|
|종이·목재	|-2	|-5	-|7	|-3	|3	|-14|
|철강금속	|3	|2	1	|3	|5	|14|
|통신업	|4	|0	|5	|-5	|3	|7|
|화학	|2	|1	|3	|-1	1|	|6|
|제조업	|3	|1	|3	|-1	|3	|9|
|Total	|26	|-19	|19	|-57	|33	|2|

* ROE평균 이상 / PER 평균 이하 & ROE 평균 이하 인 전략이 가장 성과가 좋음

[eda_per_roa_cap.ipynb](./eda_per_roa_cap.ipynb)
***

## 3. 내용

### 3-1. 산업 분류 기준 정리
3가지 데이터의 산업 분류가 다르기 때문에 분석을 위해 기준을 맞추는 과정이 필요했다

데이터 | 산업 분류 항목 | 개수
-----| -----------|------
산업별 수익현황 데이터 (KOSIS) | '농업, 임업 및 어업', '광업', '음식료품', '섬유의복', '종이·목재', '화학', '의약품', '비금속광물', '철강금속', '기계', '전기전자', '의료·정밀기기', '운수장비', '기타제조업', '유통업', '전기가스', '건설업', '운수창고업', '통신업', '서비스업' | 20
코스닥 산업별 시가총액 데이터 (KOSIS) | '농림업', '광업', '제조업', '음식료・담배', '섬유・의류', '종이・목재', '출판・매체복제', '화학', '제약', '비금속', '금속', '기계.장비', '일반전기전자', '의료・정밀기기', '운송장비・부품', '기타제조업','전기.가스.수도', '건설', '유통', '숙박・음식', '운송', '금융', '오락・문화', '기타서비스','통신방송서비스', '통신방송서비스1', '통신방송서비스2', 'IT S/W & SVC', 'IT S/W & SVC(인터넷)', 'IT S/W & SVC(디지털컨텐츠)', 'IT S/W & SVC(소프트웨어)', 'IT S/W & SVC(컴퓨터서비스)', 'IT H/W', 'IT H/W(통신장비)', 'IT H/W(정보기기)', 'IT H/W(반도체)', 'IT H/W(IT부품)' | 37
코스피 산업별 시가총액 데이터 (KOSIS) | '농업, 임업 및 어업', '광업', '음식료품', '섬유의복', '종이·목재', '화학', '의약품', '비금속광물', '철강금속', '기계', '전기전자', '의료정밀', '운수장비', '기타제조업', '유통업', '전기가스', '건설업', '운수창고업', '통신업', '금융업', '금융업(은행)', '금융업(증권)', '금융업(보험)', '금융업(기타금융)', '서비스업' | 25
업종별 국내 시장규모 데이터 (INSTANS) | '전산업', '농림어업', '광업', '제조업', '전기가스수도', '폐수처리 및 자원재활용', '건설', '서비스업', '제조업', '의약', '반도체', '디스플레이', '컴퓨터', '통신기기', '가전', '정밀기기', '전지', '항공', '석유화학', '정밀화학', '기타 전자부품', '전기기기', '일반목적기계', '특수목적기계', '자동차', '철도', '기타 수송장비', '석유정제', '고무', '플라스틱', '유리', '세라믹', '시멘트', '기타 비금속 광물', '철강', '비철금속', '주조', '조립금속', '조선', '음식료', '담배', '섬유', '의류', '가죽·신발', '목재', '제지', '인쇄', '가구', '기타 제조업', '서비스업', '도·소매업', '운수·보관', '출판', '방송', '통신', '정보', '금융·보험', '부동산', '임대', '전문·과학기술', '사업시설관리서비스', '사업지원', '공공행정', '교육', '의료·보건', '사회복지', '숙박·음식점', '예술·스포츠·여가', '기타 서비스' | 69
**통합 후 분류** | **'농업, 임업 및 어업', '광업', '제조업','음식료품', '섬유의복', '종이·목재', '화학', '의약품', '비금속광물', '철강금속', '기계', '전기전자', '의료·정밀기기', '운수장비', '기타제조업', '유통업', '전기가스', '건설업', '운수창고업', '통신업', '서비스업'** | **21**

[@wonjin77](https://github.com/wonjin77)
### 3-2. 병합을 위한 각 데이터 전처리
#### 업종별 국내 시장규모 데이터

```python
market_size_raw.rename(index={
    '전산업':'전체', 
    '농림어업':'농업, 임업 및 어업', 
    '의약':'의약품', 
    '도·소매업':'유통업', 
    '전기가스수도':'전기가스', 
    '건설':'건설업', 
    '운수·보관':'운수창고업',
    '정밀기기': '의료·정밀기기'}, inplace=True)
market_size_reform = pd.DataFrame({ '년도' : [], '시장규모' : [], '산업분류' : []})

for industry in market_size_final.index:
    for year in market_size_final.columns:
        values = pd.DataFrame(
            columns=['년도', '시장규모', '산업분류'], 
            data=[[year, market_size_final[year][industry], industry]])
        market_size_reform = market_size_reform.append(values)
```
[market_size_data_preprocessing.ipynb](./market_size_data_preprocessing.ipynb)
### 3-3. 데이터 병합
#### 데이터 병합

```python
df_msmc = pd.merge(df_ms, df_mc, how='outer', on=['산업분류','년도'])
industry_df = pd.merge(df_mi, df_msmc, on=['산업분류','년도'], how='outer')
industry_df = industry_df.dropna()
```

![data set](https://user-images.githubusercontent.com/18084336/108584073-b0da3d00-7381-11eb-9a6a-ec110cfa4624.png)

```python
msno.matrix(industry_df);
```
![결측치](https://user-images.githubusercontent.com/18084336/108589815-97e28380-73a3-11eb-8fbd-681a3493b3e3.png)

[merge_data_preprocessing.ipynb](./merge_data_preprocessing.ipynb)

### 3-4. 전처리
#### 전체 산업분류 정규화
```python
df_norm_std = pd.DataFrame()
for i in range(len(df['산업분류'].unique())):
    data = df[df['산업분류'] == df['산업분류'].unique()[i]][list(df.columns)[2:]]
    data_norm = (data - data.mean()) / data.std()
    df_norm_std_left = df[['산업분류', '년도']][df['산업분류']==df['산업분류'].unique()[i]]
    df_norm_std_ind = pd.concat([df_norm_std_left, data_norm], axis=1)
    df_norm_std = df_norm_std.append(df_norm_std_ind)
df_norm_std
```
[eda_corr.ipynb](./eda_corr.ipynb)
#### 산업별 정규화의 평균 - 히트맵
```python
for idx, sector in enumerate(sector_norm_ls):
    globals()['df_norm_ind_{}'.format(idx)] = df_norm[df_norm['산업분류'] == sector]
    globals()['df_norm_ind_{}'.format(idx)].drop(columns='산업분류', inplace=True)
    globals()['df_norm_ind_{}'.format(idx)].set_index('년도', inplace=True)

    df_norm_t = df_norm_t.add(globals()['df_norm_ind_{}'.format(idx)])
    
df_norm_to = df_norm_t / 20
df_norm_to
```
![전처리](https://user-images.githubusercontent.com/18084336/108594173-b2285b80-73bb-11eb-80cb-a0a188e49840.png)
[eda_corr-heatmap.ipynb](./eda_corr-heatmap.ipynb)

### 3-5. 데이터 시각화
#### 매출, 시총 관계 탐색
```python
sns.jointplot(y='매출액 (백만원)',x='시총', hue='산업분류',data=df_no_manuf, height=8, legend='auto')
plt.show()
```
![매출 시총](https://user-images.githubusercontent.com/18084336/108590892-358c8180-73a9-11eb-8d15-c3c4c22dad57.png)

#### 당기순이익 탐색
```python
plt.figure(figsize=(18,10))
sns.boxplot(x="산업분류", y="당기순이익 (백만원)", data=df_no_manuf, flierprops={'markerfacecolor':'g', 'marker':'D'})
plt.show()
```
![당기순이익](https://user-images.githubusercontent.com/18084336/108590995-bf3c4f00-73a9-11eb-8c34-169ec805a85e.png)

####
### 3-6. 참고자료
- 산업 분류 통합화
    - http://kssc.kostat.go.kr/ksscNew_web/kssc/common/ClassificationContent.do?gubun=1&strCategoryNameCode=001&categoryMenu=007&addGubun=no
- 산업별 분석
    - 건설업 회사수 감소(서울경제 박윤선 기자) - https://news.naver.com/main/read.nhn?mode=LSD&mid=sec&sid1=101&oid=011&aid=0003470717
    - 건설업 영업이익 감소(조선일보 박정현 기자) - https://news.naver.com/main/read.nhn?mode=LSD&mid=sec&sid1=101&oid=366&aid=0000238007
    - 통신업 영업이익 감소(파이낸셜뉴스 이설영 기자) -https://news.naver.com/main/read.nhn?mode=LSD&mid=sec&sid1=105&oid=014&aid=0002786115
    - 전기전자 영업이익 증가(경향신문 임아영 기자) - https://news.naver.com/main/read.nhn?mode=LSD&mid=sec&sid1=101&oid=032&aid=0002902647
    - 음식료품 영업이익 감소(SBS 이한승 기자) - https://news.naver.com/main/read.nhn?mode=LSD&mid=sec&sid1=004&oid=374&aid=0000140179
