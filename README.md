# Kubernetes

## 安裝 Minikube 的先決條件

最少 2 個 CPU。
至少 2GB 的物理內存 (RAM)。
20GB 磁盤空間。
Internet 連接以下載軟件包。
安裝 Docker 引擎——容器管理系統。
安裝 Conntrack。

## 安裝流程

### 1.Install Docker 

1.使用以下命令驗證已安裝和啟用的存儲庫

  yum repolist
  
2.添加了 Docker 存儲庫

yum -y install docker-ce

3.啟動並啟用 Docker

systemctl start docker

systemctl enable docker

4.查看 Docker 狀態

systemctl status docker

![image](https://user-images.githubusercontent.com/13865973/183815583-89d1eb51-9194-467b-9a02-fcdfd7e3066f.png)

### 2.Install Conntrack

1.在 CentOS 上安裝 Conntrack

yum -y install conntrack

### 3.Install Kubernets

1.下載 kubectl

curl -LO https://storage.googleapis.com/kubernetes-release/release/`curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt`/bin/linux/amd64/kubectl

2.為keubectl 分配可執行權限

chmod +x kubectl

3.kubectl 包移動到您的 $PATH（例如 /usr/local/bin)

mv kubectl /usr/local/bin/

4.檢查 kubeclt 版本來驗證安裝 "-o json" 標誌將為您提供 JSON 格式的輸出

kubectl version --client -o json

![image](https://user-images.githubusercontent.com/13865973/183816213-8ce0dc7f-481b-45c1-98c5-f9d4b675887d.png)

5.獲取節點狀態和角色 kubectl

kubectl get nodes

![image](https://user-images.githubusercontent.com/13865973/183817678-2dea839f-62fd-4022-b877-ca90e6670880.png)

### 4.Install Minikube

1.下載minikube包

wget https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

2.賦予 minicube 包的可執行權限

chmod +x minikube-linux-amd64

3.將 Minikube 包移動到 /usr/local/bin

mv minikube-linux-amd64 /usr/local/bin/minikube

4.檢查minikube版本

minikube version

![image](https://user-images.githubusercontent.com/13865973/183816589-0e41ff6e-0f0a-447b-8b39-e554d4660a0a.png)

5.minikube start

![image](https://user-images.githubusercontent.com/13865973/183817111-4d2ebb44-5b40-4502-bec9-413e13d22517.png)

#### 這裡會遇到Docker 安全性問題所以流程要改一下
5.1 新增一個用戶

useradd testuser

5.2 將用戶組新增 到 Docker

usermod -aG docker testuser

5.3 啟動minikube

minikube start --force --driver=docker

6.檢查 Minikube 的狀態

minikube status

![image](https://user-images.githubusercontent.com/13865973/183817512-893bf79d-ae3c-42ad-9cef-85bb822da4e9.png)



### 5.訪問 Kubernetes UI 儀表板

1.通過 Web 瀏覽器訪問 Kubernetes 儀表板

minikube dashboard --url

![image](https://user-images.githubusercontent.com/13865973/183817908-01aefc5a-937d-4ab1-bd75-fd8ca919892a.png)

2.複製 URL 並將其黏貼到瀏覽器中。 就可以看到 Kubernetes Web 儀表板的外觀。


