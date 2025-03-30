# 2-astra-AI-personal-project
생성형 ai 2기 개인프로젝트 repo

### 과제 : 
개인 프로젝트(2주간)
주어진 데이터셋 중 원하는 데이터셋을 사용해 원하는 사전 훈련 모델(CNN)을 훈련시키고, 연구보고서를 작성해 보세요.
- (필수) Test Accuracy, Test Loss 출력 값과 성능 시각화(그래프)를 포함한 연구 및 분석 과정에 대한 내용이 있어야합니다.
- (필수) DB 연동
- (선택) 위 성공 조건을 달성했다면. 실제 데이터를 입력해 예측 또는 분류 결과 출력 후 분석한 내용도 작성해보세요.

### main idea 
실험용 데이터세트 : Almond Varieties (https://www.kaggle.com/datasets/mahyeks/almond-varieties/data)
각 클래스 별 300~400장 이미지 존재 -> 너무 적다.
이를 해결하기 위해 few shot learning 도입.
 - prototypical network 적용 (논문 : https://arxiv.org/abs/1703.05175)
 - backbone : resnet 18 -> few shot learning의 효과를 빠르게 보기 위해 일부러 작은 모델 선택.
 - train dataset : cifar-100 dataset(https://www.cs.toronto.edu/~kriz/cifar.html), 견과류가 없는 데이터세트를 train으로 선택함.

### 실험
| num | pretrained | train | test | shot | meta batch size |
|-----|------------|-------|------|------|-----------------|
| 1   | Y          | N     | Y    | 1    | -               |
| 2   |            |       |      | 5    | -               |
| 3   | Y          | Y     | Y    | 1    | 1               |
| 4   |            |       |      | 1    | 4               |
| 5   |            |       |      | 1    | 8               |
| 6   |            |       |      | 5    | 1               |
| 7   |            |       |      | 5    | 4               |
| 8   |            |       |      | 5    | 8               |

### 결과
| experiment_id | shot | meta_batch_size | best_val_acc | status    |
|---------------|------|------------------|---------------|-----------|
| exp_1         | 1    | -                | 52.48         | Evaluated |
| exp_2         | 5    | -                | 71.38         | Evaluated |
| exp_3         | 1    | 1                | 68.03         | Finished  |
| exp_4         | 1    | 4                | 69.80         | Finished  |
| exp_5         | 1    | 8                | 69.10         | Finished  |
| exp_6         | 5    | 1                | 82.88         | Finished  |
| exp_7         | 5    | 4                | 81.18         | Finished  |
| exp_8         | 5    | 8                | 80.90         | Finished  |


### 보고서
보고서 링크 : https://www.notion.so/adapterz/8-1ba394a480618011abdbeeffde2df896?pvs=4




