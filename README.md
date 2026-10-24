# 무릎 3D MRI에서 pseudo X-ray 만들기

무릎 **3D MRI** 데이터로부터 가짜 X-ray(**pseudo X-ray**)를 만드는 과정을 단계별로
체험하고, 같은 환자의 **실제 X-ray** 와 비교하는 교육용 실습 노트북입니다.
별도 설치 없이 구글 코랩(Colab)에서 바로 실행할 수 있도록 구성했습니다.

## 바로 실행 (Colab)

아래 배지를 누르면 코랩에서 노트북이 열립니다.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mhj0326/knee-pseudo-xray-demo/blob/main/knee_pseudo_xray.ipynb)

노트북을 연 뒤 "런타임 → 모두 실행"을 선택하면 데이터 다운로드부터 결과 비교까지 자동으로 진행됩니다.

## 구성

- **1부. 정의와 예시** — MRI, X-ray, pseudo X-ray가 각각 무엇인지 설명하고 예시 이미지를 보여줍니다.
- **2부. 단계별 제작** — 3D MRI 확인 → X선 감쇠계수 설정 → 투영 → 각도 변화 → 대비 보정 →
  실제 X-ray와 비교 → 10명 전체 비교 → 직접 실험.

## 데이터

`data/cases/` 아래에 10명분이 들어 있습니다. 환자 폴더마다 다음 두 파일이 있습니다.

- `mri_label.npz` — 128 x 128 x 128 크기의 3D MRI 라벨 볼륨 (조직 번호 0~7)
- `real_xray.png` — 같은 환자의 실제 X-ray 사진

## 참고 사항

- 데이터는 교육용으로 가공된 무릎 영상입니다.
- pseudo X-ray는 3D 볼륨을 한 방향으로 더해(투영) 만든 2차원 영상으로,
  X선이 뼈는 많이, 연골은 적게 막는 성질을 수치로 흉내 냅니다.
- 그래프 안의 글자는 영어로 표기했습니다. 코랩에는 한글 폰트가 기본 포함되어 있지 않아,
  한글을 쓰면 글자가 깨지기 때문입니다. 설명 문서는 모두 한국어입니다.

## 교사용 메모

- 추가 패키지 설치 없이 코랩 기본 환경(numpy, matplotlib, scipy, PIL)에서 동작합니다.
- 학생이 `PICK`(환자 선택), `mu`(감쇠계수), 투영 축, 감마 값을 바꿔 보며
  결과 변화를 관찰하도록 설계했습니다.
