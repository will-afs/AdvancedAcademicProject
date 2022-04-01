# 📚 🛠️ AdvancedAcademicProject overview

Visualize relations between individuals of a community through knowledge graphs

An exemple of knowledge graph :

<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Graph%20visualization.JPG" width="700">

Main steps
----------

The project can be summed up in 4 main steps:

<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Main%20steps%20of%20the%20project.JPG" width="700">


**Step 1**

<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Step%201.JPG" width="700">

**Step 2**

<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Step%202.JPG" width="700">

**Step 3**

<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Step%203.JPG" width="700">

**Step 4**

<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Step%204.JPG" width="700">

Subprojects and integration
---------------------------
This project is an aggregate of different programs :
- [<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/ArXivParser.png" width="30"> ArXivParser](https://github.com/will-afs/ArXivPDFExtractor)
- [<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/pickaxe.png" width="30"> PDFExtractor](https://github.com/will-afs/PDFExtractor)
- [<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/CooldownManager.png" width="30"> CooldownManager](https://github.com/will-afs/CooldownManager)
- [<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/OntologyMaker.png" width="30"> OntologyMaker](https://github.com/will-afs/OntologyMaker)

They can be integrated as follows :

<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Deployment%20architecture.JPG" width="700">

The installation, tests, and deployment procedures of each one of these subprojects are described in their own README.md

Installing Redis
----------------
The solution relies on Redis as a message broker

It needs to be installed on a machine, and accessible to the ArXivParser and OntologyMaker:

    sudo apt update
    sudo apt install redis-server
    
Edit redis configuration file by replacing "supervised no" by "supervised systemd" :

    sudo nano /etc/redis/redis.conf
    sudo systemctl restart redis.service
    
To avoid reloading Redis anytime the server is reloaded:

    sudo systemctl disable redis

Launch the service:

    sudo systemctl enable redis-server

Check the service is running:

    sudo systemctl start redis.service

(in a future version)

    sudo docker run --name redis-arxivpdfextractor -d redis
    
By default, this command should make the service accessible at the address : redis://localhost:6379/0

