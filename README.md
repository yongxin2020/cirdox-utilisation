# cirdox-utilisation

## Install cirdox
```
git clone git@gricad-gitlab.univ-grenoble-alpes.fr:portetf/cirdox.git
cd cirdox/
more INSTALL 
mkdir -p files/output/hyp files/output/log files/output/wav files/output/xml asr/tmp
sudo apt-get install glib2.0 libportaudio2 portaudio19-dev libsndfile1-dev libcurl4-nss-dev libjson-c-dev libjson-c4 curl tk8.6

./cirdox
```

If you see "remote: The project you were looking for could not be found or you don't have permission to view it", use `cirdox.zip` for your installation.

## Utilisation cirdox
### Modifier sa fréquence d'échantiollonage 
Un exemple de mon fichier audio :
```
sox GROUP_34_CLIENT_2_EMO_S_MOOD_NEG_04_05_14.wav -c 1 -b 16 -r 16k -e signed-integer GROUP.wav
```
### Vérifier la fréquence des fichiers
```
play GROUP.wav 
rm audio.wav 
```
### renommer ton ficher 
```
mv GROUP.wav audio.wav
```
### Vérifier le contenue des fichiers
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
