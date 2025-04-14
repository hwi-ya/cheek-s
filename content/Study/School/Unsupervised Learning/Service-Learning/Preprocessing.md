---
created: 2025-04-14
updated: 2025-04-14
dg-publish: true
---

- ## One-point
    
    ```python
    import os
    import cv2
    import numpy as np
    import json
    
    # 이미지와 segmentation 정보를 매칭하는 함수
    def Image_mask_area(img_path, json_path):
        image_name_list = os.listdir(img_path)
        files_json = os.listdir(json_path)
    
        json_info = {}
        for file in files_json:
            try:
                with open(os.path.join(json_path, file), 'r', encoding='utf-8') as f:
                    data = json.load(f)
                json_info[file] = {
                    "img_file_name": data["images"]["img_file_name"],
                    "segmentation": data["annotations"]["segmentation"]
                }
            except:
                continue
    
        # 이미지 이름으로 json 이름을 빠르게 찾기 위한 dict
        img_to_json = {info["img_file_name"]: name for name, info in json_info.items()}
    
        # 이미지와 segmentation 매칭
        img_and_segmentation_Match = {
            img: json_info[img_to_json[img]]["segmentation"]
            for img in image_name_list if img in img_to_json
        }
    
        return img_and_segmentation_Match
    
    # 직사각형 이미지를 제거
    def del_img(img_path, img_and_segmentation_Match):
        filtered = {}
        for img, segmentation in img_and_segmentation_Match.items():
            image = cv2.imread(os.path.join(img_path, img))
            if image is None:
                continue
            h, w, _ = image.shape
            if h == w:  # 정사각형만 유지
                filtered[img] = segmentation
        return filtered
    
    # 마스킹 후 저장
    def image_masking_anti_aliasing(img_path, img_and_segmentation_Match, save_path):
        os.makedirs(save_path, exist_ok=True)
    
        for idx, (img, segmentation) in enumerate(img_and_segmentation_Match.items(), start=1):
            image = cv2.imread(os.path.join(img_path, img))
            if image is None:
                continue
    
            segmentation_spot = np.array(segmentation, dtype=np.int32).reshape((-1, 2))
            mask = np.zeros(image.shape[:2], dtype=np.uint8)
            cv2.fillPoly(mask, [segmentation_spot], 255)
    
            masked_image = cv2.bitwise_and(image, image, mask=mask)
            resized = cv2.resize(masked_image, (128, 128))
    
            cv2.imwrite(os.path.join(save_path, f'output_{idx}.png'), resized)
    
    # Canny 기반 이물질 탐지
    def foreign_object_detection(img_path):
        image = cv2.imread(img_path)
        if image is None:
            return
    
        resized = cv2.resize(image, (64, 64))
        gray = cv2.cvtColor(resized, cv2.COLOR_BGR2GRAY)
    
        # 엣지 탐지
        edges = cv2.Canny(gray, 50, 150)
    
        # 분산으로 이물질 여부 판단
        edge_variance = np.var(edges)
        if edge_variance >= 300:
            print('나뭇가지 감지됨:', img_path)
    
    # 전체 실행 예시
    if __name__ == "__main__":
        img_path = '/your/image/folder/path'
        json_path = '/your/json/folder/path'
        save_path = '/your/output/folder/path'
    
        print("1. 이미지와 segmentation 매칭 중...")
        matched = Image_mask_area(img_path, json_path)
    
        print("2. 직사각형 이미지 필터링 중...")
        filtered = del_img(img_path, matched)
    
        print("3. 마스크 적용 및 저장 중...")
        image_masking_anti_aliasing(img_path, filtered, save_path)
    
        print("4. 이물질 탐지 중...")
        for file in os.listdir(save_path):
            if file.endswith(".png"):
                foreign_object_detection(os.path.join(save_path, file))
    ```
