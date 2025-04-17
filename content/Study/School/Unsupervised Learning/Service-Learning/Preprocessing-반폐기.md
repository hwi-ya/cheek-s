---
created: 2025-04-14
updated: 2025-04-14
dg-publish: true
---

- ## Preprocessing
    
    ```python
    import os
    import cv2 #이미지 처리를 위한 라이브러리
    from matplotlib import pyplot as plt #이미지 출력을 위한 라이브러리
    import numpy as np
    import json  #json파일을 읽기 위한 라이브러리
    
    img_path = r"C:\Users\leeks\mine\Service_Learning(Unsupervised_Learning)\test"
    
    os.chdir(img_path)   #작업환경 변경
    files_img = os.listdir(img_path) #폴더 안에 있는 것들 확인
    image_name_list = []
    
    
    
    for file in files_img:
            image_name_list.append(file)
    b = 0
    for img in image_name_list:
        image = cv2.imread(img)
    
        height, width, a = image.shape 
        
        zero_matrix = np.zeros((128, 128))
    
        neighbors = [   #이웃 픽셀 리스트
                    (x-1, y-1), (x-1, y), (x-1, y+1),  # 상좌, 상, 상우
                    (x, y-1), (x, y+1),                # 좌, 우
                    (x+1, y-1), (x+1, y), (x+1, y+1)   # 하좌, 하, 하우
                ]
        
        for x in range(height):
            for y in range(width):
                for n_x, n_y in neighbors:  #이웃 픽셀 불러오기
                    if 0 <= n_x < 128 and 0 <= n_y < 128:  # 경계 체크 
                        current_pixel = image[x, y].astype(int) #overflow 방지용
                        neighbor_pixel = image[n_x, n_y].astype(int) #overflow 방지용
                        
                        # current_pixel과 neighbor_pixel이 모두 검정색이 아닌지 확인
                        if not np.all(current_pixel == [0, 0, 0]) and not np.all(neighbor_pixel == [0, 0, 0]):
                            if sum(current_pixel)/3 <= sum(neighbor_pixel)/3 - 40:  # 이상치 탐지
                                image[x, y] = [0, 0, 255]
                                zero_matrix[x, y] = sum(current_pixel) 
    
        zero_matrix = zero_matrix.reshape(-1)
        
        if np.var(zero_matrix) >= 250:
            b += 1
            print('나뭇가지',img)
            #cv2.imshow("Masked Image", image)
            #cv2.waitKey(0)
            #cv2.destroyAllWindows
    
    print(b)

    ```
