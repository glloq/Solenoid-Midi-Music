# Solenoid-Midi-Music

l'objectif est de permettre le controle de 1 a 128 solenoides avec des messages midi recue via usb.  
Nous utiliserons des pca23017 pour activer le solenoide voulu a la reception d'un message midi noteOn puis desactivé a la reception d'un message midi noteOff.
La partie puissance sera controlé avec des mofset, des ULN2803, ULN2804 etc ...
<img src="https://github.com/glloq/Solenoid-Midi-Music/blob/main/img/SchemaElec.png" alt="pluck" width=100% height=100%/>  

Afin de reduire la chaleur generé par les solenoides actif, nous utiliserons un decoupage PWM de l'alimentation generale pour reduire de 20/30% la tension des solenoides lorsqu'ils sont maintenu activé.

## Code 
Il suffit d'adapter le fichier settings pour votre cas d'utilisation 
