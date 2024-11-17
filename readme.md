# TP 1 : Manipulation du système de fichiers HDFS

Ce TP guide à travers les commandes pour manipuler le système de fichiers HDFS avec Hadoop.

---

## 1. Démarrage des processus Hadoop
```bash
# Démarrer HDFS
start-dfs.sh

# Démarrer Yarn
start-yarn.sh

# Vérifier que les processus sont actifs
jps

````
2. Création de l'arborescence HDFS
 ```bash
        hdfs dfs -mkdir /BDDC
        hdfs dfs -mkdir /BDDC/CPP
        hdfs dfs -mkdir /BDDC/CPP/Cours
        hdfs dfs -mkdir /BDDC/CPP/TPs
        hdfs dfs -mkdir /BDDC/JAVA
        hdfs dfs -mkdir /BDDC/JAVA/Cours
        hdfs dfs -mkdir /BDDC/JAVA/TPs

   ````
3. Création des fichiers dans HDFS avec contenu

# Créer les fichiers dans /BDDC/CPP/Cours
 ```bash

# Créer les fichiers dans /BDDC/CPP/Cours
hdfs dfs -touchz /BDDC/CPP/Cours/CoursCPP1
hdfs dfs -touchz /BDDC/CPP/Cours/CoursCPP2
hdfs dfs -touchz /BDDC/CPP/Cours/CoursCPP3

# Ajouter du contenu dans les fichiers
echo "Contenu de CoursCPP1" | hdfs dfs -appendToFile - /BDDC/CPP/Cours/CoursCPP1
echo "Contenu de CoursCPP2" | hdfs dfs -appendToFile - /BDDC/CPP/Cours/CoursCPP2
echo "Contenu de CoursCPP3" | hdfs dfs -appendToFile - /BDDC/CPP/Cours/CoursCPP3

   ````

4. Afficher le contenu des fichiers
 ```bash
    hdfs dfs -cat /BDDC/CPP/Cours/CoursCPP1
    hdfs dfs -cat /BDDC/CPP/Cours/CoursCPP2
    hdfs dfs -cat /BDDC/CPP/Cours/CoursCPP3

   ````

5. Copier les fichiers dans JAVA/Cours
 ```bash
    hdfs dfs -cp /BDDC/CPP/Cours/CoursCPP1 /BDDC/JAVA/Cours
    hdfs dfs -cp /BDDC/CPP/Cours/CoursCPP2 /BDDC/JAVA/Cours
    hdfs dfs -cp /BDDC/CPP/Cours/CoursCPP3 /BDDC/JAVA/Cours

   ````

6. Supprimer et renommer les fichiers
# Supprimer CoursCPP3 de JAVA/Cours
 ```bash
    # Supprimer CoursCPP3 de JAVA/Cours
    hdfs dfs -rm /BDDC/JAVA/Cours/CoursCPP3
    
    # Renommer les fichiers
    hdfs dfs -mv /BDDC/JAVA/Cours/CoursCPP1 /BDDC/JAVA/Cours/CoursJAVA1
    hdfs dfs -mv /BDDC/JAVA/Cours/CoursCPP2 /BDDC/JAVA/Cours/CoursJAVA2

   ````

7. Création des fichiers dans le système de fichiers local

# Créer un répertoire local et les fichiers
 ```bash

mkdir ~/HDFS_TP
cd ~/HDFS_TP
touch TP1CPP TP2CPP TP1JAVA TP2JAVA TP3JAVA
   ````

8. Copier TP1CPP et TP2CPP vers CPP/TPs
 ```bash
    hdfs dfs -copyFromLocal ~/HDFS_TP/TP1CPP /BDDC/CPP/TPs
    hdfs dfs -copyFromLocal ~/HDFS_TP/TP2CPP /BDDC/CPP/TPs

   ````
   
9. Copier TP1JAVA et TP2JAVA vers JAVA/TPs
 ```bash
    hdfs dfs -copyFromLocal ~/HDFS_TP/TP1JAVA /BDDC/JAVA/TPs
    hdfs dfs -copyFromLocal ~/HDFS_TP/TP2JAVA /BDDC/JAVA/TPs

   ````
   
10. Afficher le contenu de BDDC de manière récursive
 ```bash
  hdfs dfs -ls -R /BDDC

   ````
    
11. Supprimer TP1CPP de CPP/TPs
 ```bash
  hdfs dfs -rm /BDDC/CPP/TPs/TP1CPP
   ````
    
12. Supprimer le répertoire JAVA avec son contenu
 ```bash
  hdfs dfs -rm -r /BDDC/JAVA

   ````
  