Version 6.2 : 14/01/2019
-----------
- Modification des fichiers gen/Makefile* :
==> Cr�ation du r�pertoire obj par le Makefile 
    de sorte � compenser que Github ne peut pas fournir de r�pertoire vide dans l'archive fournie au t�l�chargement.
- Modification du fichier inc/SOS.h :
==> Le nombre de couches du profil par d�faut passe de 26 � 100 (constante SOS_OS_NT dans SOS.h)
    pour ne pas avoir des couches de trop grande �paisseur optique.

Version 6.1 : 05/09/2017
-----------
- Le code SOS passe sous licence � GNU GPL V3.0 or later �:
==> Ajout du fichier COPYING.txt au niveau du r�pertoire des codes sources (src), des �x�cutables (exe) et de la documentation (doc).
==> Introduction du copyright dans le manuel utilisateur 
    (version fran�aise et anglaise, r�pertoire doc).
==> Introduction du copyright dans les codes sources (r�pertoire src).
- Modification d'une variable pour la lecture du fichier des angles (routines SOS_AEROSOLS.F, SOS_SURFACE.F et SOS.F)

Version 6.0 : 20/01/2016
-----------
- Adaptation du code pour une compilation sous linux / gfortran
==> Modification du fichier "Aerosols" de sortie de SOS_AEROSOLS
    et du fichier utilisateur de fonctions de phase externes. 
- Modification de la d�finition des granulom�tries LND 
en faveur de la d�finition usuelle des LND.
==> La valeur de la variance change en param�tre d'entr�e.
Sig_new = Sig_old * ln(10) pour ln = log n�p�rien.
Voir le manuel pour plus de pr�cisions.
- Quelques corrections d'incoh�rence de sortie en erreur pour cause de
  param�tres non d�finis (mais inutiles pour le cas de simulation souhait�).
- Changement de la pr�cision du fichier de profil : l'�paisseur optique 
qui �tait cod�e en F9.5 devient cod�e en F10.6 (pour r�gler des probl�mes
de couche � �paisseur optique interpr�t�e nulle, en milieu tr�s t�nu).
- Correction de quelques anomalies dans les fichiers de spectre d'indice de r�fraction 
des mod�les d'a�rosols de Shettle&Fenn et de la WMO, ainsi que dans le fichier de 
granulom�trie des mod�les de Shettle&Fenn (particules "Large Rural" � 70% d'humidit� relative).
- Correction du calcul de la r�flexion solaire directe sur mer plate.


Version 5.2 : 23/10/2014
-----------
Ajout d'un makefile pour gfortran


Version 5.1 : 24/06/2010
-----------

- Les �tiquettes de FORMAT en ,X, passent en ,1X, pour �viter des erreurs de compilation.
- Correction pour effacer le fichier FICOS_TMP � la fin des calculs de transmission.



Version 5.0 : 01/06/2010
-----------

- Complete reprise du parametrage : utilisation de "-keyword value".

- Introduction d'une fonction SOS_ANGLES.F qui gere la definition des angles de Gauss
  et l'utilisation d'angles utilisateurs. Elle gere �galement les ordres limites des developpements.
	
- Definition de tableaux (luminances, fonctions de phase) sur des domaines plus importants 
  que le domaine utilis� : permet un usage du code avec une possibilit� de modification du 
  nombre d'angles utilis�s sans recompilation (et l'ajout d'angles utilisateurs variables).
  
- Adaptation de la routine SOS_AEROSOLS.F pour permettre l'utilisation d'un fichier 
  de fonctions de phase externes (utile pour des particules non-spheriques).
  
- Adaptation de la routine SOS.F pour permettre le calcul des transmissions diffuses.
	    
- Tracabilit� des constantes par copie du fichier SOS.h sur l'espace de compilation 
  et sur l'espace des resultats (modification du main_SOS.ksh).

- Mise a jour du Manuel Utilisateur + version anglaise.

       
######################################################       
       
Version 4.1 : 08/09/2008
-----------

- Int�gre une prise en compte des modeles bimodaux (Dubovik) avec correctifs / version 4.0.

- Evolutions depuis la version 4.0 :
     - Adaptation de la routine SOS_AEROSOLS.F (VERSION:2.1):
        *  Correction de depassements de zone d'indentation pour compilation f77.
	
        * Suppression de la sortie des calculs pour fin de fichier de MIE atteinte.
          Car si c'est le cas, il s'agit d'une erreur : le fichier de MIE est 
          incomplet (probable manque d'espace disque � sa g�n�ration).
          --> Gestion du cas d'erreur.
	  
        * Correction pour le calcul des proportions de composants des mod�les bimodaux
          Dubovik :
	  Cas du calcul � partir des rapports d'�paisseur optique des deux modes
          (fin et grossier) et de l'�paisseur optique totale pour une longueur
           d'onde de r�f�rence 
	  --> utilisation de l'indice de r�fraction des particules pour la longueur 
	  d'onde de r�f�rence (uniquement).
	    
     - Evolution du script main_SOS.ksh pour l'appel de la fonction SOS_AEROSOLS.exe
       (gestion des arguments)


