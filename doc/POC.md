# POC: ArgoCD

## Інструкція на отримання доступу до інтерфейсу ArgoCD

 ### Створення локального кластеру для встановлення ArgoCD

$ k3d cluster create argo   
$ kubectl cluster-info   
$ k version   
$ k get all -A  

### Інсталяція ArgoCD
$ kubectl create namespace argocd  
$ k get   
$ kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml  
$ k get all -n argocd  

### Доступ до інтерфейсу ArgoCD GUI https://127.0.0.1:8080

$ kubectl port-forward svc/argocd-server -n argocd 8080:443&  

### Отримання паролю 

$ k -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"  
$ k -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}"|base64 -d;echo  

### Створення та синхронізація застосунку

![ezgif-6ac14a2327d57d](https://github.com/user-attachments/assets/945f6671-dda6-4cf4-8c58-ef05c69b7339)
