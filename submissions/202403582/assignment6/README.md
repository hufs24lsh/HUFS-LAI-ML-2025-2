%%writefile final/README.md
# 강의자료 자동 요약기 (Lecture Note Summarizer)

본 프로젝트는 컴퓨터 또는 AI 분야 강의 텍스트를 입력하면 **핵심 문장**, **키워드**, **자동 threshold 추천**, 그리고 **자동 노트 생성** 기능을 제공하는 요약 도구입니다.
TF-IDF + Logistic Regression 기반으로 학습된 모델을 사용하며, Gradio UI를 통해 누구나 쉽게 활용할 수 있도록 서비스 형태로 구현되었습니다.

---

##  Install & Run

### 1. 패키지 설치
프로젝트 디렉토리(final/)에서 아래 명령어 실행:

```
pip install -r requirements.txt
```

### 2. 서비스 실행

```
python app.py
```

실행 후 Gradio 인터페이스가 자동으로 브라우저에 표시됩니다.

또는 아래 링크에서 바로 사용하실 수 있습니다.

https://huggingface.co/spaces/hufs24lsh/ML-lecsum

---

## Project Structure

```
final/
 ├── app.py                     # Gradio 서비스 메인 코드
 ├── requirements.txt           # 필요한 Python 라이브러리
 └── model/
       ├── final_model.pkl          # 학습된 Logistic Regression 모델
       └── tfidf_vectorizer.pkl     # TF-IDF 벡터라이저
```

---

## Features

### 1) 핵심 문장 추출
- Logistic Regression 모델이 각 문장에 대한 중요도 확률을 계산
- Threshold 기반으로 핵심 문장 여부 판단
- 정렬 옵션 제공
  - 원래 순서
  - 핵심문장 먼저
  - 확률 높은 순
  - 확률 낮은 순

### 2) 키워드 추출
- 각 문장의 TF-IDF 벡터를 합산
- 중요도가 높은 상위 N개 키워드 자동 추출

### 3) Threshold 자동 최적화
- 문장 확률 분포 기반 local-threshold 계산
- 가장 높은 F1 score가 나오는 threshold 자동 추천

### 4) 자동 노트 생성
- 키워드
- 핵심 문장
- 요약문
을 한 번에 만들어 주는 전체 노트 자동 생성 기능

### 5) 설명 기능
- 핵심 문장 판단 기준 설명
- 키워드 추출 기준 설명
- Threshold 설명

---

## 추천 사용 시나리오

### 1. 강의 텍스트 입력  
   → 강의 전체 내용을 복사하여 붙여넣습니다.

### 2. threshold 자동 최적화  
   → 문장들의 확률 분포를 기반으로 최적 threshold를 추천받습니다.

### 3. 핵심 문장 추출 / 키워드 추출 / 자동 노트 생성  
   → 원하는 기능 버튼을 눌러 결과를 확인합니다.


---

## Example
예시 텍스트 버튼을 통해 크루스칼 알고리즘 설명 텍스트를 자동 입력해서 즉시 테스트할 수 있습니다.
