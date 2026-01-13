# Data Analysis & Regression Modeling

SceneClick 서비스의 핵심 로직인 **"썸네일 요소가 조회수에 미치는 영향"**을 통계적으로 검증한 연구 코드입니다.
데이터 전처리부터 OLS 회귀분석, 결과 해석까지의 전체 과정을 포함하고 있습니다.

## 파일 목록

* **[SceneClick_Analysis_Regression.ipynb](SceneClick_Analysis_Regression.ipynb)**
  * Python의 `statsmodels` 라이브러리를 활용하여 다중 회귀분석(Multiple Linear Regression)을 수행한 메인 코드입니다.

---

## 분석 개요 (Analysis Overview)

서비스 기획 단계에서 수립한 가설을 데이터를 통해 정량적으로 검증했습니다.

* **분석 목표:** 유튜브 썸네일의 시각적 요소(X)가 조회수 효율(Y)에 미치는 영향력 측정
* **종속 변수 (Y):** 조회수 효율 (`조회수 / 구독자수 * 100`)
* **독립 변수 (X):**
  1. **대비 (Contrast):** 이미지 전체의 시각적 강렬함 (0~255)
  2. **배경 대비 얼굴 면적 비율 (%):** 배경과 얼굴 간의 시각적 분리도 및 조화

## 코드 실행 프로세스

1. **데이터 로드 및 전처리 (Preprocessing)**
   * `pandas`를 활용하여 원본 데이터 로드 및 수치형 변환
2. **변수 정의 (Feature Engineering)**
   * 독립변수($X$)와 종속변수($Y$) 설정 및 상수항(Constant) 추가
3. **모델링 (OLS Regression)**
   * `statsmodels.api.OLS` 함수를 사용하여 최소자승법 회귀 모델 적합

---

## 주요 분석 결과 (Key Findings)

코드 실행 결과 도출된 통계적 수치는 SceneClick 서비스의 알고리즘 설계 기준이 되었습니다.

### 1. 모델 신뢰도
* **R-squared (결정계수):** `0.210`
  * 썸네일의 시각적 요소가 조회수 효율 변동의 약 **21%**를 설명합니다.
* **Prob (F-statistic):** `0.0412` (< 0.05)
  * 통계적으로 유의미한 모델임을 입증했습니다.

### 2. 회귀 계수 (Coefficients) & 해석
분석 결과, 두 변수 모두 조회수 효율에 **음(-)의 영향**을 미치는 것으로 나타났습니다.

| 변수 (Variable) | 계수 (Coef) | P-value | 해석 (Interpretation) |
| :--- | :--- | :--- | :--- |
| **상수항 (Intercept)** | **4684.06** | 0.020 | 기본 조회수 효율 기대값 |
| **대비 (Contrast)** | **-53.78** | 0.052 | 전체 대비가 1 증가할수록 효율 **약 53.78 감소** |
| **얼굴 면적 비율** | **-40.83** | 0.062 | 배경 대비 얼굴의 분리감(대비)이 1% 커질수록 효율 **약 40.83 감소** |

> **결론:** "여행 브이로그에서는 과도한 고대비(High Contrast)와 배경과 조화되지 못하고 얼굴만 부각되는(High Face-to-Background Contrast) 구성이 클릭을 방해한다"는 사실을 입증했습니다.
> 즉, 얼굴 크기 자체보다 '배경(여행지 정보)과의 조화'가 핵심입니다.

---

## 사용 라이브러리 (Tech Stack)

* `pandas`: 데이터 핸들링
* `statsmodels`: 회귀분석 및 통계 검증
* `matplotlib` / `seaborn`: 데이터 시각화
