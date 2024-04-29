DOCKER

Imagine Docker:
a.	O imagine Docker este un șablon de bază care conține toate dependențele și configurările necesare pentru a rula o aplicație sau un serviciu.
b.	Este compusă dintr-un strat de bază (base layer) și straturi suplimentare care conțin toate pachetele și dependențele necesare pentru aplicație.
c.	Imaginile sunt statice și nu pot fi modificate în timpul execuției.
d.	Imaginile Docker sunt create folosind fișiere Dockerfile și pot fi distribuite și partajate prin intermediul unui registru Docker, cum ar fi Docker Hub.
Container Docker:
e.	Un container Docker este o instanță în execuție a unei imagini Docker.
f.	Atunci când o imagine Docker este rulată, este instanțiată într-un container, care poate fi văzut ca o instanță a aplicației sau a serviciului.
g.	Un container Docker are propriul său spațiu de lucru izolat, inclusiv sistemul de fișiere, rețelele și variabilele de mediu.
h.	Containerul este un mediu dinamic în care aplicația sau serviciul este executat și poate fi pornit, oprit și șters în orice moment.


Cele mai uzuale comenzi Docker:
1.	docker run: Această comandă este folosită pentru a crea și a rula un container dintr-o imagine Docker specificată. Poate fi utilizată pentru a specifica opțiuni precum numele containerului, porturile, variabilele de mediu și multe altele.
Exemplu: docker run -d --name my_container -p 8080:80 nginx
2.	docker build: Această comandă este folosită pentru a construi o imagine Docker dintr-un Dockerfile și din alte fișiere asociate. Aceasta este esențială pentru crearea de imagini personalizate.
Exemplu: docker build -t my_image .
3.	docker pull: Folosită pentru a descărca o imagine Docker dintr-un registru, cum ar fi Docker Hub.
Exemplu: docker pull ubuntu
4.	docker push: Această comandă este folosită pentru a încărca o imagine Docker într-un registru Docker.
Exemplu: docker push my_image
5.	docker ps: Folosită pentru a afișa toate containerele care rulează în prezent.
Exemplu: docker ps
6.	docker stop: Folosită pentru a opri un container care rulează.
Exemplu: docker stop my_container
7.	docker rm: Folosită pentru a șterge un container existent.
Exemplu: docker rm my_container
8.	docker rmi: Folosită pentru a șterge o imagine Docker.
Exemplu: docker rmi my_image



KUBERNETES

Kubernetes este un sistem open-source de orchestrare a containerelor, dezvoltat inițial de Google și acum gestionat de Cloud Native Computing Foundation (CNCF). Principala sa funcție este de a facilita gestionarea și scalarea aplicațiilor containerizate într-un mediu de infrastructură distribuit.
Poduri: Un pod este cea mai mică unitate de bază în Kubernetes, o colecție de containere (de preferat un container al unei singure aplicatii) care împărtășesc resursele, cum ar fi spațiul de stocare și rețeaua. Podurile sunt scalabile și replicabile. 
Fiecare pod primeste automat propria adresa IP dinamica, care se va schimba la repornirea automata a pod-ului, daca a fost o problema cu el.
Replici și controlere: Replicile sunt instanțe identice ale unui pod, gestionate de controlere precum Deployment sau StatefulSet. Aceste controlere monitorizează starea podurilor și se asigură că numărul specificat de replici este întotdeauna în stare activă. 
Servicii: Serviciile Kubernetes permit expunerea aplicațiilor și serviciilor în cadrul sau în afara clusterului Kubernetes, oferind un set de IP-uri stabile și un singur punct de intrare pentru a accesa aplicațiile.
Fiecare pod va avea propriul serviciu atasat. Fiecare serviciu are o adresa IP permanenta. Pod-urile comunica unele cu altele prin service-uri.
Ingress permite accesarea serviciului prin url, nu prin adresa IP si port. ConfigMap reprezinta configurarea externa a aplicatiei tale ex: username, pe care le foloseste pod-ul. Secret e unConfigMap codat in base64 pt parole.
Deployment : Replicile containerului sunt atasate la acelasi service ca si containerul. Prin deployment setam cate replici vrem. Daca o replica nu e disponibila se va folosi alta replica.
StatefullSet : Se foloseste pentru replicile volumelor.
Volume: Sunt folosite pentru stocarea datelor: baze de date. Daca pastram db in containere, datele nu sunt persistate la repornire si de aceea folosim volume care salveaza datele pe un hdd.
Nodes: Reprezinta o colectie de pods, volume-pods, servicii, ConfigMaps, etc care ruleaza impreuna. Fiecare nod are un Container Runtime, un Kubelet si un Kube Proxy.
Master Nodes: Manageriaza celelalte noduri. Acesta are : API Server, Scheduler, Controller Manager, etcd (cluster brain).
Minikube : Creeaza o cutie virtuala (1 nod K8s cluster) pe local in care ruleaza master nodes si worker nodes, pentru a testa functionarea locala a app in containere. 

Principalele comenzi Kubernetes (kubectl) – pt Minikube si Cloud clusters
minikube start –vm-driver=hyperkit – initializeaza minikube pe local
minikube service <nume service> - seteaza o adresa ip publica pt accesarea externa a serviciului care a fost configurat ca si LoadBalancer
minikube addons enable ingress – porneste implementarea controlerului de Ingress, adica pod-ul de Ingress Controller in cluster
kubectl create: Folosit pentru a crea resurse Kubernetes, cum ar fi poduri, servicii sau replici, bazându-se pe fișiere de manifest sau argumente de la linia de comandă.
kubectl apply: Utilizat pentru a aplica sau actualiza configurările Kubernetes din fișiere de manifest. Acesta compară starea actuală cu cea dorită și aplică modificările necesare.
kubectl get: O comandă utilă pentru a obține informații despre resursele Kubernetes. Poate fi folosită pentru a lista resursele, pentru a afișa informații detaliate despre o resursă specifică și pentru a filtra rezultatele.
kubectl describe: Oferă detalii despre o resursă specifică, cum ar fi poduri, servicii sau noduri, inclusiv starea, evenimentele asociate și etichetele asociate.
kubectl delete: Folosit pentru a șterge resurse Kubernetes, fie prin specificarea numelui resursei, fie prin specificarea unui fișier de manifest.
ssh <host> - te conectezi cu ssh la host
k config  - get-contexts – arata toate contextele disponibile.
-	use-context <name> - schimba contextual de lucru la name

k get pod – afiseaza toate pod-urile din context
k run <nume-pod> --image=... – creezi un pod cu denumirea nume-pod
k delete pod <nume-pod> -  stergi nume-pod
k create deployment <nume> --imagine = … - creem un deploy <nume> al imaginii (un pod)…
k set image deployment <nume> nginx = … - schimba imaginea deploymentului
k delete deployment <nume> - stergi deploymentul
k edit deployment <nume> - ne arata pod-ul pe care il putem modifica si apoi salvam
k logs <nume> - arata logul
k apply -f fisier.yaml – aplica configuratiile din fisier
helm – o colectie de comenzi prin care poti folosi yaml files create anterior, care au fost puse la dispozitie intr-un helm charts.

