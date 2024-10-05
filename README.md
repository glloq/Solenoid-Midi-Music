# Solenoid-Midi-Music

l'objectif est de permettre le controle de 1 a 128 solenoides avec des messages midi recue via usb.  
Nous utiliserons des pca23017 ou des mcp9685 pour activer le solenoide voulu a la reception d'un message midi noteOn puis desactivé a la reception d'un message midi noteOff.
La partie puissance sera controlé avec des mofset, des ULN2803, ULN2804 en fonction des caracteristiques des solenoids et des besoins du systeme.  

Afin de reduire la chaleur generé par les solenoides actif, nous utiliserons un decoupage PWM de l'alimentation generale pour reduire de 20/30% la tension des solenoides lorsqu'ils sont maintenu activé.

chaque code devra permettre de gerer jusqu'a 128 solenoides pour activer des note utilisant une gamme chromatique ou diatonique.
le solenoide activera la premiere note (la note la plus grave utilsé) via la premiere sortie de la carte MCP ou PCA, les notes suivantes seront activé par les pins suivant.

## applications
il y a 3 versions du code :
  - impulsion/percussion => active le solenoide pendant un court instant a la reception d'un message noteOn
  - Activation simple => active le solenoide avec un message noteOn, desactive avec un message noteOff sans gestion de velocité
  - Activation PWM => active le solenoide avec un message noteOn, desactive avec un message noteOff avec gestion de la velocité 
    
### Impulsion/Percussion

Ce code utilise des mcp23017 pour activer des solenoide pendant un certain temps afin de jouer des sur un systeme de percussions (xylophone, glockenspiel, marimba, cloches, etc ...) 
la partie puissance devra idelaement passer par ULN2803 pour limiter le nombre de composants, si vous utilisez des mofset=> pensez à utiliser une diode de roue libre !  
Voici un exemple de controle de 32 solenoides en utilisant des ULN2803 :  
<img src="https://github.com/glloq/Solenoid-Midi-Music/blob/main/img/SchemaPercussions.png" alt="pluck" width=100% height=100%/>  

voici les parametres a adapter a l'utilisation dans settings :
- le numero midi de la premiere note (MIDI_FIRST_NOTE)
- le nombre de solenoides utilisé ( SOLENOIDS_NUMBER )
- le type de gamme utilisé ( DIATONIC_OCTAVE a 1 si on utilise un accordage diatonique et a 0 si chromatique)
- le temps actif pour frapper la note ( TIME_POWERED )
