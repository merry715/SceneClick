# SceneClick: Data-Driven YouTube Thumbnail Optimizer

> **"SceneClick은 '예쁜' 썸네일을 만드는 것이 아니라, 데이터를 통해 '클릭되는' 썸네일로 개선합니다."**
> **"Instead of generating 'aesthetic' thumbnails, SceneClick improves existing thumbnails based on regression-based visual insights."**

---

## 프로젝트 개요 (Project Overview)

**SceneClick**은 유튜브 해외여행 브이로그 썸네일의 시각적 문제를 회귀분석(Regression Analysis)으로 진단하고, 이를 최적화하는 데이터 기반 AI 솔루션입니다.

디자이너의 감각에 의존하던 기존 방식에서 벗어나, "조회수 효율(View Efficiency)"과 상관관계가 입증된 시각적 변수를 조절하여 클릭률을 상승하는 것을 목표로 합니다.

### 핵심 기능 (Key Ideas)
1.  **진단 (Diagnose):** 회귀분석 모델을 활용해 현재 썸네일의 시각적 문제점(과도한 대비, 부조화 등) 진단
2.  **변환 (Convert):** 분석된 인사이트를 프롬프트 및 이미지 처리 규칙(Rule-based Processing)으로 변환
3.  **검증 (Validate):** 개선된 결과물의 예상 성과 시뮬레이션

---

## 데이터 분석 및 연구 인사이트 (Regression-Based Insights)

본 프로젝트는 실제 유튜브 **해외여행 브이로그 썸네일 30건**의 데이터를 수집하여 OLS 회귀분석을 수행했습니다.

### 1. 분석 결과 (Key Findings)
조회수 효율과 유의미한 상관관계를 보인 두 가지 변수는 다음과 같습니다.

| 변수 (Variable) | 상관관계 (Coef) | 해석 (Interpretation) |
| :--- | :--- | :--- |
| **전체 대비 (Overall Contrast)** | **Negative (-)** | 대비가 과도하게 높을수록 클릭 효율 저하 |
| **배경 대비 얼굴 비율 (Face-to-BG Ratio)** | **Negative (-)** | 배경과 조화되지 않고 얼굴만 튀는(고대비) 구성일수록 효율 저하 |

### 2. 결론 및 적용 (Conclusion)
> **"Higher contrast and excessive face dominance tend to reduce view efficiency."**

분석 결과, 여행 브이로그에서는 인물보다 **'여행지의 분위기(배경)'**가 중요함이 입증되었습니다.
SceneClick 모델은 이를 단순한 예측기가 아닌, **"디자인 방향성을 제시하는 가이드라인(Directional Design Guideline)"**으로 활용하여 이미지를 생성합니다.

👉 **[ 상세 분석 코드 보기 (Notebook)](notebooks/SceneClick_Analysis_Regression.ipynb)**

---

## 프로젝트 문서 및 자료 (Documents)

프로젝트의 기획부터 통계적 검증 과정까지의 상세 문서는 `docs` 폴더에 아카이빙 되어 있습니다.

* **기획 및 설계**
  * [ 기획안 (Project Proposal)](docs/SceneClick_Plan.pdf)
  * [ 서비스 설계 로직 (Service Logic)](docs/Service_Architecture_Logic.pdf)
* **데이터 분석**
  * [ 회귀분석 결과 보고서 (Analysis Report)](docs/Data_Analysis_Report.pdf)
* **발표 자료**
  * [ 최종 발표 슬라이드 (Presentation)](docs/SceneClick_Presentation.pdf)
  * [ 발표 요약본 (Summary)](docs/SceneClick_Presentation_Summary.pdf)

---

## 데이터셋 (Data Check)

분석에 활용된 가공 데이터는 `data` 폴더에 있으며, 용량이 큰 원본 이미지 데이터 등은 아래 링크에서 확인하실 수 있습니다.

* **Preprocessed Data:** [data/thumbnail_data.xlsx](data/thumbnail_data.xlsx)
* **Raw Data Structure:** [👉 Download Raw Data (Google Drive Link)](여기에_구글드라이브_링크를_넣으세요)

---

## 실행 방법 (How to Run)

1.  **Repository Clone**
    ```bash
    git clone [https://github.com/your-username/SceneClick.git](https://github.com/your-username/SceneClick.git)
    ```
2.  **Install Dependencies**
    ```bash
    pip install -r requirements.txt
    ```
3.  **Run Application**
    ```bash
    # 메인 서비스 실행 (Gradio)
    jupyter notebook SceneClick.ipynb
    ```

---

### Tech Stack
* **Language:** Python
* **Analysis:** Pandas, Statsmodels (OLS Regression)
* **AI & Web:** Stable Diffusion, Gradio
