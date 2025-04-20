---
created: 2025-04-17
updated: 2025-04-20
dg-publish: true
---

- ## Transformer?  
  - 시퀀스 데이터를 처리하기 위한 딥러닝 모델 아키텍처  
  - 2017년 **"Attention is All You Need"** 라는 논문에서 처음 소개됨<br/>
  <br/>

  - **공부하기 전 알아야 할 내용**     
      | What?                    |   Why?                                                             |
      |--------------------------|--------------------------------------------------------------------|
      | **Self-Attention**       | 쉽게말하면 Transformer는 Self-Attention의 집합체이기 때문            |
      | Deep Learning            | MLP, Loss, Optimizer 등의 기본구조는 알고 가는게 좋음                |
      | Linear Algebra           | Transformer, Self-Attention은 모든 연산이 행렬 기반이기 때문에       |
      | Probability & Statistics | Self-Attention에서 Attention Score를 확률로 바꿀 때 사용하기 위해    |
<br/>
<br/>

  - **공부하는 이유**  
      **저도 몰라요 하기 싫어요 응!애!**
<br/>
<hr>

- ## Self-Attention?  
  - 자신이 시퀀스의 다른 모든 요소들과 **얼마나 관련이 있는지** 를 계산해서 그에 따라 정보를 가중합하여 표현을 갱신하는 방식<br/>
<br/>

  - **Self-Attention의 흐름**  
      - **1. 입력 데이터를 고정된 차원의 벡터 시퀀스로 변환한다**  
         - 입력데이터(문장, 이미지등) 임베딩하거나 패치로 나눠 벡터 형태의 시퀀스 데이터로 변환
        <br/>
        <br/>
      - **2. 각 레이어에 가중치 행렬을 곱해 Query, Key, Value값을 만든다**  
         - 각각의 입력 벡터를 서로 다른 3개의 가중치 행렬과 곱해 Query, Key, Value 벡터를 생성한다
         - 여기서 가중치 행렬은 랜덤으로 정해진다.
        <br/>
        <br/>         
      - **3. query, key의 dot product(유사도)를 통해 attention score를 계산한다**  
         - attention score : 유사도를 수치화한 것
        <br/>
        <br/>
      - **4. attention score를 softmax를 사용해 정규화를 한다**  
         - dots가 음수가 나올 수도 있음 - 이 경우에는 지수함수를 곱해줘 양수화 한다
         - 계산된 score들을 softmax 함수를 통해 0~1 사이의 값으로 정규화하여 가중치로 만든다
         - softmax란?
           - 여러 개의 숫자를 확률처럼 해석 가능한 값들로 바꿔주는 함수
        <br/>
        <br/>
      - **5. 이 정규화된 값의 value를 가중합 한다**  
         - 각 Query는 전체 Value들을 해당 가중치만큼 곱해서 문맥을 반영한 새로운 벡터로 만든다
        <br/>
        <br/>
      - **6. 가중합 해서 나온 결과 벡터를 출력한다**  
         - 이 가중합 결과가 Self-Attention의 출력이며, 다음 레이어로 넘어가거나 최종 결과로 사용된다
         - Transformer에서는 새로운 Self-Attention으로 넘어가 새로운 결과벡터를 만들어낸다.<br/>
         - 입력데이터(문장, 이미지등) 임베딩하거나 패치로 나눠 벡터 형태의 시퀀스 데이터로 변환
        <br/>
        <br/>
      - **2. 각 레이어에 가중치 행렬을 곱해 Query, Key, Value값을 만든다**  
         - 각각의 입력 벡터를 서로 다른 3개의 가중치 행렬과 곱해 Query, Key, Value 벡터를 생성한다
         - 여기서 가중치 행렬은 랜덤으로 정해진다.
        <br/>
        <br/>         
      - **3. query, key의 dot product(유사도)를 통해 attention score를 계산한다**  
         - attention score : 유사도를 수치화한 것
        <br/>
        <br/>
      - **4. attention score를 softmax를 사용해 정규화를 한다**  
         - dots가 음수가 나올 수도 있음 - 이 경우에는 지수함수를 곱해줘 양수화 한다
         - 계산된 score들을 softmax 함수를 통해 0~1 사이의 값으로 정규화하여 가중치로 만든다
         - softmax란?
           - 여러 개의 숫자를 확률처럼 해석 가능한 값들로 바꿔주는 함수
        <br/>
        <br/>
      - **5. 이 정규화된 값의 value를 가중합 한다**  
         - 각 Query는 전체 Value들을 해당 가중치만큼 곱해서 문맥을 반영한 새로운 벡터로 만든다
        <br/>
        <br/>
      - **6. 가중합 해서 나온 결과 벡터를 출력한다**  
         - 이 가중합 결과가 Self-Attention의 출력이며, 다음 레이어로 넘어가거나 최종 결과로 사용된다
         - Transformer에서는 새로운 Self-Attention으로 넘어가 새로운 결과벡터를 만들어낸다.<br/>
  
- ## Program code
  - 1, 2 : Unsupervised Learning, 3 : Supervised Learning
  - 현재 코드는 전반적으로 개 망했다고 봐도 무방하다 1, 2는 결과가 안좋고 3은 실행이 안된다(**fxxk**)
  - ### 1. Basic transformer  
    ```python
    from transformers import ViTModel, ViTFeatureExtractor
    from torchvision import datasets, transforms
    from sklearn.cluster import KMeans
    import torch
    from tqdm import tqdm
    import os
    import shutil
    from PIL import Image
    import time
    
    start_time_1 = time.time()  # 시작 시간 기록
    
    # ✅ 1. 사전학습된 ViT 모델 및 Feature Extractor 로드
    model = ViTModel.from_pretrained("google/vit-base-patch16-224-in21k")
    model.eval()
    feature_extractor = ViTFeatureExtractor.from_pretrained("google/vit-base-patch16-224-in21k")
    
    # ✅ 2. 이미지 전처리 정의
    transform = transforms.Compose([
        transforms.Resize((224, 224)),
        transforms.ToTensor(),
        transforms.Lambda(lambda x: feature_extractor(images=x, return_tensors="pt")["pixel_values"][0])
    ])
    
    # ✅ 3. 경로 설정
    base_path = r"C:\Users\hwiya\Unsupervised Learning\Service-Learning"
    image_path = os.path.join(base_path, "test")
    normal_path = os.path.join(base_path, "Normal Apple")
    foreign_path = os.path.join(base_path, "Another Apple")
    
    # ✅ 4. 결과 저장 경로 생성
    os.makedirs(normal_path, exist_ok=True)
    os.makedirs(foreign_path, exist_ok=True)
    
    # ✅ 5. 이미지 로딩 (ImageFolder 폴더 트릭 사용)
    # 모든 이미지를 'dummy'라는 임시 폴더에 넣어야 함 (ImageFolder 특성상)
    dummy_folder = os.path.join(image_path, "dummy")
    if not os.path.exists(dummy_folder):
        os.makedirs(dummy_folder)
        # test 폴더에 있는 모든 이미지 -> dummy로 이동 (초기 세팅만)
        for f in os.listdir(image_path):
            full_path = os.path.join(image_path, f)
            if os.path.isfile(full_path):
                shutil.move(full_path, os.path.join(dummy_folder, f))
    
    dataset = datasets.ImageFolder(root=image_path, transform=transform)
    loader = torch.utils.data.DataLoader(dataset, batch_size=1, shuffle=False)
    
    # ▶️ 분류 시작 시간 기록
    start_time_2 = time.time()
    
    # ✅ 6. CLS 벡터 추출
    features = []
    file_paths = []
    
    with torch.no_grad():
        for i, batch in enumerate(tqdm(loader)):
            img_tensor = batch[0]
            output = model(img_tensor)
            cls_vector = output.last_hidden_state[:, 0, :]
            features.append(cls_vector.squeeze().numpy())
    
            file_paths.append(dataset.samples[i][0])  # 이미지 경로 저장
    
    # ✅ 7. KMeans 클러스터링 (2개 군집)
    features = torch.tensor(features).numpy()
    kmeans = KMeans(n_clusters=2, random_state=42).fit(features)
    labels = kmeans.labels_
    
    # ✅ 8. 다수 이미지에서 일반 사과가 포함된 클러스터 자동 추론
    # (가장 많은 이미지가 들어간 쪽을 일반 사과로 간주)
    from collections import Counter
    cluster_counts = Counter(labels)
    normal_cluster = cluster_counts.most_common(1)[0][0]
    
    # ✅ 9. 이미지 이동 + 개수 카운트
    normal_count = 0
    foreign_count = 0
    
    for path, label in zip(file_paths, labels):
        filename = os.path.basename(path)
        if label == normal_cluster:
            dest = os.path.join(normal_path, filename)
            normal_count += 1
        else:
            dest = os.path.join(foreign_path, filename)
            foreign_count += 1
    
        shutil.copy(path, dest)
        print(f"{filename} → {'정상 사과' if label == normal_cluster else '이물질 사과'} → {dest}")
    
    # ▶️ 분류 종료 시간 기록
    end_time_2 = time.time()
    classify_time = end_time_2 - start_time_2
    
    # ▶️ 전체 코드 종료 시간
    end_time_1 = time.time()
    all_code_time = end_time_1 - start_time_1
    
    print(f"  ✅ 정상 사과: {normal_count}개")
    print(f"  ⚠️  이물질 사과: {foreign_count}개")
    
    # ✅ 백분율 계산
    total_count = normal_count + foreign_count
    if total_count > 0:
        percent = (normal_count / total_count) * 100
        print(f"  📊 정상 사과 비율: {percent:.2f}%")
    else:
        print("  ⚠️ 전체 이미지 수가 0입니다.")
    
    print(f"\n✅ 전체 실행 시간: {all_code_time:.2f}초")
    print(f"⏳ 순수 분류 처리 시간 (ViT + KMeans + 파일 이동): {classify_time:.2f}초")
    ```
  - ### 2. Basic Transformer + Mean Pooling + Normalization
    ```python
    Mean Pooling + 정규화 적용된 코드
    사과1 : 106  오답률 : 106:22 : 17.19%
    사과2 : 84   오답률 : 84:1   : 1.18%
    실행 시간 : 33.93초 (순수 분류 시간 : 29.19초초)    
    
    # ⏱ 전체 시작 시간
    start_time_1 = time.time()
    
    # ✅ 1. 사전학습 ViT 모델 및 Feature Extractor 로드
    model = ViTModel.from_pretrained("google/vit-base-patch16-224-in21k")
    model.eval()
    feature_extractor = ViTFeatureExtractor.from_pretrained("google/vit-base-patch16-224-in21k")
    
    # ✅ 2. 이미지 전처리 정의
    transform = transforms.Compose([
        transforms.Resize((224, 224)),
        transforms.ToTensor(),
        transforms.Lambda(lambda x: feature_extractor(images=x, return_tensors="pt")["pixel_values"][0])
    ])
    
    # ✅ 3. 경로 설정
    base_path = r"C:\Users\hwiya\Unsupervised Learning\Service-Learning"
    image_path = os.path.join(base_path, "test")
    normal_path = os.path.join(base_path, "Normal Apple")
    foreign_path = os.path.join(base_path, "Another Apple")
    
    # ✅ 4. 결과 저장 폴더 생성
    os.makedirs(normal_path, exist_ok=True)
    os.makedirs(foreign_path, exist_ok=True)
    
    # ✅ 5. ImageFolder 트릭용 dummy 폴더 구성
    dummy_folder = os.path.join(image_path, "dummy")
    if not os.path.exists(dummy_folder):
        os.makedirs(dummy_folder)
        for f in os.listdir(image_path):
            full_path = os.path.join(image_path, f)
            if os.path.isfile(full_path):
                shutil.move(full_path, os.path.join(dummy_folder, f))
    
    # ✅ 6. 이미지 로딩
    dataset = datasets.ImageFolder(root=image_path, transform=transform)
    loader = torch.utils.data.DataLoader(dataset, batch_size=1, shuffle=False)
    
    # ⏱ 분류 시작 시간
    start_time_2 = time.time()
    
    # ✅ 7. 특징 추출 (Mean Pooling 사용)
    features = []
    file_paths = []
    
    with torch.no_grad():
        for i, batch in enumerate(tqdm(loader)):
            img_tensor = batch[0]  # shape: [1, 3, 224, 224]
            output = model(img_tensor)
            mean_vector = output.last_hidden_state.mean(dim=1)  # Mean Pooling: [1, 768]
            features.append(mean_vector.squeeze().numpy())
            file_paths.append(dataset.samples[i][0])
    
    # ✅ 8. 정규화 + KMeans 클러스터링
    features = StandardScaler().fit_transform(features)
    kmeans = KMeans(n_clusters=2, random_state=42).fit(features)
    labels = kmeans.labels_
    
    # ✅ 9. 다수 이미지 클러스터 = 정상 사과
    cluster_counts = Counter(labels)
    normal_cluster = cluster_counts.most_common(1)[0][0]
    
    # ✅ 10. 이미지 이동 및 결과 출력
    normal_count = 0
    foreign_count = 0
    
    for path, label in zip(file_paths, labels):
        filename = os.path.basename(path)
        if label == normal_cluster:
            dest = os.path.join(normal_path, filename)
            normal_count += 1
        else:
            dest = os.path.join(foreign_path, filename)
            foreign_count += 1
        shutil.copy(path, dest)
        print(f"{filename} → {'✅ 정상 사과' if label == normal_cluster else '⚠️ 이물질 사과'} → {dest}")
    
    # ⏱ 분류 종료 시간
    end_time_2 = time.time()
    classify_time = end_time_2 - start_time_2
    end_time_1 = time.time()
    all_time = end_time_1 - start_time_1
    
    # ✅ 최종 결과 출력
    total = normal_count + foreign_count
    normal_ratio = (normal_count / total * 100) if total > 0 else 0
    
    print("\n📊 분류 결과 요약")
    print(f"✅ 정상 사과: {normal_count}개")
    print(f"⚠️ 이물질 사과: {foreign_count}개")
    print(f"📈 정상 사과 비율: {normal_ratio:.2f}%")
    print(f"⏱ 전체 실행 시간: {all_time:.2f}초")
    print(f"⏳ 순수 분류 처리 시간: {classify_time:.2f}초")
    ```
  - ### 3.Supervised Learning Transformer
    ```python
    import os
    import shutil
    import numpy as np
    import time
    from PIL import Image
    from sklearn.metrics import accuracy_score
    from torchvision import datasets, transforms
    from torch.utils.data import Dataset, DataLoader
    from transformers import ViTImageProcessor, ViTForImageClassification, Trainer, TrainingArguments
    import torch
    
    start_time = time.time()
    
    # ✅ 경로 설정
    base_path = r"C:\Users\hwiya\Unsupervised Learning\Service-Learning\labeled_apples"
    train_path = os.path.join(base_path, "train")
    val_path = os.path.join(base_path, "val")
    test_path = os.path.join(base_path, "test")
    output_path = os.path.join(base_path, "predicted_output")
    os.makedirs(output_path, exist_ok=True)
    
    # ✅ 클래스 정의
    class_names = ["normal_apple", "foreign_apple"]
    num_labels = len(class_names)
    
    # ✅ 최신 전처리기 사용 (추천)
    processor = ViTImageProcessor.from_pretrained("google/vit-base-patch16-224-in21k")
    transform = transforms.Compose([
        transforms.Resize((224, 224)),
        transforms.ToTensor(),
        transforms.Lambda(lambda x: processor(images=x, return_tensors="pt")["pixel_values"][0])
    ])
    
    # ✅ 학습용 데이터
    train_dataset = datasets.ImageFolder(train_path, transform=transform)
    val_dataset = datasets.ImageFolder(val_path, transform=transform)
    
    # ✅ 모델 불러오기
    model = ViTForImageClassification.from_pretrained(
        "google/vit-base-patch16-224-in21k",
        num_labels=num_labels
    )
    
    # ✅ 학습 설정
    training_args = TrainingArguments(
        output_dir=os.path.join(base_path, "vit-output"),
        per_device_train_batch_size=8,
        per_device_eval_batch_size=8,
        num_train_epochs=4,
        evaluation_strategy="epoch",  # 최신버전에서도 지원됨
        save_strategy="epoch",
        logging_dir=os.path.join(base_path, "logs"),
        load_best_model_at_end=True,
        metric_for_best_model="accuracy"
    )
    
    # ✅ 정확도 계산 함수
    def compute_metrics(p):
        preds = np.argmax(p.predictions, axis=1)
        return {"accuracy": accuracy_score(p.label_ids, preds)}
    
    # ✅ Trainer 설정 및 학습 시작
    trainer = Trainer(
        model=model,
        args=training_args,
        train_dataset=train_dataset,
        eval_dataset=val_dataset,
        compute_metrics=compute_metrics
    )
    
    print("\n📚 학습 시작 중...")
    trainer.train()
    print("✅ 학습 완료!")
    
    # ✅ 모델 저장
    model.save_pretrained(os.path.join(base_path, "vit-final"))
    
    # ✅ 테스트 이미지 Dataset 클래스
    class TestImageDataset(Dataset):
        def __init__(self, folder, transform):
            self.paths = [os.path.join(folder, f) for f in os.listdir(folder) if f.lower().endswith(('.jpg', '.png'))]
            self.transform = transform
    
        def __len__(self):
            return len(self.paths)
    
        def __getitem__(self, idx):
            path = self.paths[idx]
            img = Image.open(path).convert("RGB")
            return self.transform(img), path
    
    # ✅ 테스트 데이터 로드
    test_dataset = TestImageDataset(test_path, transform)
    test_loader = DataLoader(test_dataset, batch_size=1)
    
    # ✅ 분류 및 저장
    model.eval()
    normal_count = 0
    foreign_count = 0
    
    with torch.no_grad():
        for img_tensor, path in test_loader:
            output = model(img_tensor)
            pred_label = torch.argmax(output.logits, dim=1).item()
            class_name = class_names[pred_label]
    
            if pred_label == 0:
                normal_count += 1
            else:
                foreign_count += 1
    
            class_folder = os.path.join(output_path, class_name)
            os.makedirs(class_folder, exist_ok=True)
    
            filename = os.path.basename(path[0])
            shutil.copy(path[0], os.path.join(class_folder, filename))
            print(f"{filename} → {class_name}")
    
    end_time = time.time()
    print(f"\n⏱ 경과 시간: {end_time - start_time:.2f}초")
    print("\n✅ 테스트 이미지 분류 및 저장 완료!")
    print(f"→ 정상 사과: {normal_count}장")
    print(f"→ 이물질 사과: {foreign_count}장")
    print(f"📂 결과 폴더: {output_path}")
    ```

    
      
      
