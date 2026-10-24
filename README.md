# 🦴 무릎 3D MRI → pseudo X-ray 만들기 (고등학생 실습)

무릎 **3D MRI** 데이터로부터 가짜 X-ray(**pseudo X-ray**)를 만드는 과정을
단계별 이미지로 체험하고, 같은 환자의 **실제 X-ray** 와 비교하는 교육용 실습 노트북입니다.
설치할 것 없이 **구글 코랩(Colab)** 에서 바로 실행할 수 있습니다.

## ▶️ 바로 실행하기 (Colab)

아래 배지를 누르면 코랩에서 노트북이 열립니다.
(배지 링크의 `YOUR_GITHUB_USERNAME` 을 이 레포 주인의 깃허브 아이디로 바꾸세요.)

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_GITHUB_USERNAME/knee-pseudo-xray-demo/blob/main/knee_pseudo_xray.ipynb)

노트북을 열면 **런타임 → 모두 실행** 을 누르세요. 첫 셀의 `GITHUB_USER` 만 바꾸면 됩니다.

## 📚 실습 내용 (단계)

1. 데이터 내려받기
2. 도구 준비
3. 환자 1명 고르기
4. **3D MRI** 단면 들여다보기
5. X선 감쇠(막는 정도) 정하기
6. **투영해서 pseudo X-ray 만들기** ⭐
7. 여러 각도에서 바라보기
8. 진짜 X-ray처럼 보정하기
9. **실제 X-ray와 비교**
10. 10명 전체 한눈에 보기 + 직접 해보기

## 🗂️ 데이터 구성

`data/cases/` 안에 10명분이 들어 있습니다. 각 폴더마다:

- `mri_label.npz` — 128×128×128 3D MRI 라벨 볼륨 (조직 번호 0~7)
- `real_xray.png` — 같은 환자의 실제 X-ray 사진

## ℹ️ 설명

- 데이터는 교육용으로 가공된 무릎 영상입니다.
- pseudo X-ray는 3D 볼륨을 한 방향으로 더해(투영) 만든 2차원 영상입니다.
  X선이 뼈(단단함)는 많이, 연골(무름)은 적게 막는 성질을 숫자로 흉내 냅니다.

## 🧑‍🏫 선생님용 메모

- 추가 패키지 설치 없이 코랩 기본 환경에서 동작합니다(numpy/matplotlib/scipy/PIL).
- 한글 그래프 제목을 위해 첫 실행 시 나눔폰트를 자동 설치합니다(수십 초 소요).
- 학생이 `PICK`, `mu`, 투영 축, 감마 값을 바꿔 보며 결과 변화를 관찰하도록 설계했습니다.
