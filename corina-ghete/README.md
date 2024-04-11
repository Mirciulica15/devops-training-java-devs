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
