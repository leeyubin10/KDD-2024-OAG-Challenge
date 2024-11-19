# OAG-Challenge: WhoIsWho-IND Task

## 📌 프로젝트 개요
**OAG-Challenge**는 학술 그래프 마이닝 분야에서 state-of-the-art 발전을 목표로 하는 KDD Cup 2024의 도전 과제입니다. 이 프로젝트는 학술 데이터 마이닝을 통해 과학의 발전, 특성 및 트렌드를 이해하고, 정부의 과학 정책 수립, 기업의 인재 발굴, 연구자의 효율적인 지식 습득을 돕기 위한 기회를 제공합니다.

**WhoIsWho-IND** 작업은 온라인 학술 논문의 증가로 인한 이름 모호성 문제를 해결하고자 합니다. 특히, 부정확한 저자 구분 결과로 인해 잘못된 저자 순위와 상금 부정 등의 문제가 발생하고 있습니다. 이 작업은 주어진 저자 프로필을 기반으로 논문 배정 오류를 탐지하는 모델 개발을 목표로 합니다.

---

## 🧑‍💼 작업 설명
**목표**: 주어진 저자 프로필을 바탕으로, 잘못 배정된 논문을 식별하는 모델을 개발합니다. 각 저자의 프로필은 저자 이름과 그들이 발표한 논문들로 구성되어 있습니다.

**제공되는 논문 속성**:
- **title**: 논문 제목
- **authors.name**: 저자 이름
- **author.org**: 저자 소속 기관
- **venue**: 발표된 학술지 또는 학회
- **year**: 발표 연도
- **keywords**: 논문의 주요 키워드
- **abstract**: 논문의 요약

**중요 사항**: 기존 학술 검색 시스템의 구분 결과를 사용하지 않고 모델을 개발해야 합니다.

---

## 📊 데이터셋

### 파일 설명:
- **Pid_to_info_all.csv**: 논문 ID와 관련된 상세 정보
- **train_author.csv**: 학습에 사용되는 저자 정보와 그들의 논문
- **ind_valid_author.csv**: 검증용 저자 정보

### 컬럼 설명:
| Column              | Type      | Description                              |
|---------------------|-----------|------------------------------------------|
| **ID**              | string    | Paper ID                                 |
| **title**           | string    | Paper title                              |
| **authors.name**    | string    | Author's name                            |
| **author.org**      | string    | Author's organization                    |
| **venue**           | string    | Conference or Journal                    |
| **year**            | int       | Publication year                         |
| **keywords**        | list of strings | Keywords associated with the paper       |
| **abstract**        | string    | Abstract of the paper                    |

---

## 🛠️ 사용된 기술

이 프로젝트에서는 **그래프 신경망(GCN)** 을 사용하여 논문과 저자 간의 관계를 학습하고, 학술 그래프의 구조에서 중요한 정보를 추출하여 잘못된 논문 배정을 탐지합니다.

- **GCN (Graph Convolutional Network)**: 그래프의 구조적 관계를 반영하여 저자와 논문 사이의 연결을 학습하고, 논문 배정 오류를 예측하는 데 사용되었습니다.
- **GCCAD (Graph Contrastive Context-Aware Denoising)**: 이 모델은 GCN의 확장으로, 문맥을 반영한 주의(attention) 메커니즘을 추가하여 논문 간의 관계를 보다 정밀하게 학습하고, 보다 정확한 오류 탐지를 지원합니다. GCCAD는 GCN과 결합하여 문서의 의미적 특성과 저자의 관계를 더 잘 반영할 수 있습니다. 이 모델은 특히, 논문 간의 복잡한 관계를 파악하고 오류를 탐지하는 데 유용합니다.

---

## 🚀 실행 방법

### 1. 저장소 클론
```bash
git clone https://github.com/yourusername/oag-challenge-whoswho-ind.git
cd oag-challenge-whoswho-ind

### 2. 구글드라이브 파일 다운로드
https://drive.google.com/drive/folders/1PrVC0VaZygtZ8p46G4RQP5CyBJO_rxE-?usp=drive_link
