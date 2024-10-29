## 使用Google Colaboratory跑深度学习-CSDN博客

# 使用Colaboratory
![image](https://github.com/user-attachments/assets/6748f25e-0b6e-4c67-af77-f23b596f241e)
![image](https://github.com/user-attachments/assets/31938645-2a8f-44c9-956d-5bad3a8b78b8)
# 更改運行類型
![image](https://github.com/user-attachments/assets/14203697-f07e-4007-a7f4-07ea07c0d4dd)
![image](https://github.com/user-attachments/assets/7b0a744f-e65e-43bd-88a0-16d38138b05a)
驗證一下，輸入如下程式碼運行:
![image](https://github.com/user-attachments/assets/67025a67-19b6-464f-a131-4750157dea4f)
出現如下結果則表示是GPU運作：
![image](https://github.com/user-attachments/assets/f246714e-6fe5-410a-a3d5-a168ac2a5ea7)

# 安裝Miniconda3
這裡提前說一下在Colaboratory的問題：

就是在這個類似命令列的頁面端無法進行conda虛擬環境的創建，只能使用base，而且需要特殊的方式來使用conda。 先使用命令列下載Miniconda3的sh安裝包：
```
!wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
```
安裝權限配置：
```
!chmod +x Miniconda3-latest-Linux-x86_64.sh
```
安裝到指定位置，這裡建議安裝在/root/
```
!bash ./Miniconda3-latest-Linux-x86_64.sh -b -f /root/
```
激活conda:
```
!source /root/miniconda3/bin/activate
```
使用命令將conda配置成預設的命令列使用
```
!conda init
```
# 安装PyTorch
這裡試過進行env的創建，但是創建成功之後無法進行命令列的切換，因此這裡就直接在base上進行了。
安裝pytorch，這裡去pytorch官網選擇對應的版本進行安裝：

![image](https://github.com/user-attachments/assets/9f0f6316-59e2-4f5d-994c-b444a51d4400)
```
!conda install pytorch torchvision cudatoolkit=10.1 -c pytorch
```
使用指令查看conda env：
```
!conda info --env
```
![image](https://github.com/user-attachments/assets/0d29f7c0-4acb-4576-a8de-6bb7604fa4d1)


# 驗證pytorch是否能夠使用
首先直接編寫程式碼進行驗證能否直接使用自己安裝的conda python:
```
import torch  
print(torch.version)
```
安裝MMDetection
安裝mmcv
```
!git clone https://github.com/open-mmlab/mmcv.git  
!cd mmcv  
!pip install -U openmim
```
![image](https://github.com/user-attachments/assets/083d141c-3929-4e1b-a1c4-d454163bbfbb)


# 安装cpython等需求包
```
!https://gitee.com/zyp521/upload_image/raw/master/cGUR6D.png
```
安裝mmdetection
官方文件的安裝方法：
```
!git clone https://github.com/open-mmlab/mmdetection.git  
!cd mmdetection  
!pip install -r requirements/build.txt  
!pip install "git+https://github.com/cocodataset/cocoapi.git#subdirectory=PythonAPI"  
!pip install -v -e . # or "python setup.py develop"
```
我們使用:
```
!cp /content/mmcv/mmcv/version.py /content/mmcv
!python /content/mmcv/setup.py install
```
![image](https://github.com/user-attachments/assets/b3ad49c8-5504-4f53-8c93-c98ba2023c2d)


到此，我們就完成了mmdetection及其依賴函式庫的安裝。
有一個比較大的缺陷需要聲明一下，就是如果你超過12小時不登入Colaboratory的話，google會自動將你的伺服器重置分配給別人，你的資料和程式碼都被自動清楚了。
