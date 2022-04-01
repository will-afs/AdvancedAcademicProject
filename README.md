# 📚 🛠️ AdvancedAcademicProject overview

Visualize relations between individuals of a community through knowledge graphs

An exemple of knowledge graph :

<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Graph%20visualization.JPG" width="700">

Subprojects and integration
---------------------------

This project is an aggregate of different programs - an overview of the functionning of the whole system is given below, but the installation, tests, and deployment procedures of each one of these subprojects are described in their respectives README.md :
- [<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Icons/ArXivParser.png" width="30"> ArXivParser](https://github.com/will-afs/ArXivPDFExtractor)
- [<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Icons/PDFExtractor.png" width="30"> PDFExtractor](https://github.com/will-afs/PDFExtractor)
- [<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Icons/CooldownManager.png" width="30"> CooldownManager](https://github.com/will-afs/CooldownManager)
- [<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Icons/OntologyMaker.png" width="30"> OntologyMaker](https://github.com/will-afs/OntologyMaker)

These subprograms can be integrated as follows :

<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Deployment%20architecture/Deployment%20architecture.JPG" width="700">

Main steps
----------

The project can be summed up in 4 main steps:

<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Steps/Main%20steps%20of%20the%20project.JPG" width="700">


**Steps 1 and 2**

<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Steps/Steps%201%20and%202%20-%20Extracting%20PDF%20data%20from%20ArXiv.JPG" width="700">

**Step 3**

<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Steps/Step%203%20-%20Building%20the%20ontology.JPG" width="700">

**Step 4**

<img src="https://github.com/will-afs/AdvancedAcademicProject/blob/main/doc/Steps/Step%204%20-%20Visualize%20Knowledge%20Graphs.JPG" width="700">


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

