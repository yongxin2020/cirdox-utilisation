# cirdox-utilisation

## Install cirdox
### méthode 1
```
git clone git@gricad-gitlab.univ-grenoble-alpes.fr:portetf/cirdox.git
cd cirdox/
cirdox 
more INSTALL 
mkdir -p files/output/hyp files/output/log files/output/wav files/output/xml asr/tmp
 sudo apt-get install glib2.0 libportaudio2 portaudio19-dev libsndfile1-dev libcurl4-nss-dev libjson-c-dev libjson-c4 curl tk8.6
./cirdox
 2916  cp Commande_pour_cirdox/LumOFF1c.wav audio.wav
 2917  cd tools
 2918  ls -l
 2919  python3 cirdox2trs.py 17-01-2020_10:07:02.414:evt_1_channel_0 ../files/output/xml/
```

If no access and you see "remote: The project you were looking for could not be found or you don't have permission to view it", use `cirdox.zip` for your installation.

### méthode 2
```
git clone git@gricad-gitlab.univ-grenoble-alpes.fr:portetf/cirdox.git
ls 
cd cirdox/
mkdir -p files/output/hyp files/output/log files/output/wav files/output/xml asr/tmp
ls files/output/
sudo apt-get install glib2.0
sudo apt-get install tk8.6
sudo apt-get install portaudio19-dev
sudo apt-get install libportaudio2
sudo apt-get install libsndfile-dev
sudo apt-get install libcurl4-nss-dev
sudo apt-get install libjson-c-dev
sudo apt-get install libjson-c4 curl
```
## Utilisation cirdox
### Modifier sa fréquence d'échantiollonage 
Un exemple de mon fichier audio :
```
sox GROUP_34_CLIENT_2_EMO_S_MOOD_NEG_04_05_14.wav -c 1 -b 16 -r 16k -e signed-integer GROUP.wav
```
### Vérifier la fréquence des fichiers (optional)
```
play GROUP.wav 
rm audio.wav 
```
### renommer ton ficher 
```
mv GROUP.wav audio.wav
```
### Vérifier le contenue des fichiers (optional)
```
play audio.wav 
```
### Préparer cirdox (effacer le contenue des anciennes transcription)
```
make clean_all
. ./setenv.sh 
make
```
### Lancer le transcription
```
./cirdox
```
Normalement tu entend ton audio, il prendra presque la même durée de ton audio pour le transcrire.

### Afficher le contenue de la transcription
ATTENTION pour la dernière étape il faut que tu récupère le nom extact tu fichier dans `files/output/wav`

il faut utiliser le **fichier glocbal**, c'est lui qui contient l'integralité du fichier 

```
cd tools
python3 cirdox2trs.py 15-09-2021_12:25:45.319:global_channel_0.wav ../files/output/xml >Resultat_trascription.trs
```

La sortie de la transciption est dans le dossier `tools` 
