<a name="readme-top"></a>

[![Discord](https://img.shields.io/badge/Discord-7289DA?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/4q5srBqn89)
[![VSCode](https://img.shields.io/badge/Visual_Studio_Code-0078D4?style=for-the-badge&logo=visual%20studio%20code&logoColor=white)](https://code.visualstudio.com/)
[![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/downloads)
[![Photoshop](https://img.shields.io/badge/Adobe%20Photoshop-31A8FF?logo=adobephotoshop&logoColor=fff&style=for-the-badge)](https://www.adobe.com/fr/products/photoshop.html)
[![XDA](https://img.shields.io/badge/xda%20developers-2DAAE9?style=for-the-badge&logo=xda-developers&logoColor=white)](https://forum.xda-developers.com/)
[![Terminal](https://img.shields.io/badge/windows%20terminal-4D4D4D?style=for-the-badge&logo=windows%20terminal&logoColor=white)]()

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/EVilm1/doc-DJI-Hack">
    <img src="img/logo.png" alt="Logo" width="280">
  </a>

  <h3 align="center">WIKI HACK DJI OSD</h3>

  <p align="center">
    <a href="https://github.com/EVilm1/WIKI-HACK-DJI-OSD/blob/main/README_FR.md"><strong>Version Française ICI</strong></a><br />
    ✨ Customize your OSD ✨<br />
    <br />
    <a href="https://github.com/fpv-wtf/wtfos"><strong>Wiki WTFOS</strong></a>
    ·
    <a href="https://github.com/fpv-wtf/msp-osd"><strong>Wiki MSP-OSD</strong></a>
    ·
    <a href="https://fpv.wtf/"><strong>WTFOS Configurator</strong></a>
  </p>
</div>

<!-- TABLE OF CONTENTS -->

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#Intro">Intro</a>
      <ul>
        <li><a href="#Exemple">Example</a></li>
      </ul>
    </li>
  </ol>
  <ol>
    <li><a href="#1-installer-wtfos">Install WTFOS</a>
      <ul>
        <li><a href="#configurer-les-ports">Configure ports</a></li>
      </ul>
    </li>
    <li><a href="#2-déplacer-les-élements-de-msp-osd">Move elements of MSP-OSD</a></li>
    <li><a href="#3-fakehd">FakeHD</a></li>
      <ul>
        <li><a href="#activer-et-configurer-fakehd">Enable and configure FakeHD</a></li>
      </ul>
    </li>
    <li><a href="#4-splashscreen--screensaver-wtfos">Splashscreen & Screensaver WTFOS</a></li>
    <li><a href="#5-les-fonts-msp-osd">MSP-OSD Fonts</a></li>
    <li> <a href="#6-config-avancée--modifier-les-éléments-de-lhud-dji">(Advanced config): Modify the DJI HUD elements</a>
      <ul>
        <li><a href="#modifier-lemplacement-des-éléments-de-lhud-dji">Move the DJI HUD elements</a></li>
          <ul>
            <li><a href="#prévisualisation-script-python">Python script preview</a></li>
            <li><a href="#modifier-le-fichier-xml">Edit the .xml file</a></li>
          </ul>
        <li><a href="#modifier-la-police-de-lhud-dji">Change the font of the DJI HUD</a></li>
        <li><a href="#modifier-les-ic%C3%B4nes-de-lhud-dji">Change the DJI HUD icons</a></li>
      </ul>
    </li>
    <li><a href="#7-config-avancée-générer-sa-propre-font-pour-msp-osd">(Advanced config): Generate your own Font for MSP-OSD</a></li>
  </ol>
</details>

<!-- INTRO -->
# Intro

This documentation explains in detail how to modify your OSD in your DJI Googles.
The following examples will be made with the **DJI Googles V2 / Betaflight** combo.

In order to understand, it is necessary to establish the basics, it is necessary to differentiate the following terms:
* **``OSD Betaflight:``** This is the classic osd at the release of Betaflight, it is the one usually found in analog goggles.
* **``HUD DJI / CUSTOM OSD:``** Like the Betaflight osd, but interpreted by DJI, this is the default osd for DJI Googles. This feature is also called "Custom OSD" in the googles settings and is flawed because it does not use 100% of the information received from Betaflight.
* **``WTFOS MSP-OSD:``** The MSP-OSD package is installed through the WTFOS hack, it replaces the DJI HUD and allows new features.

<!-- EXEMPLE -->
## Example

We are going to make a mix between **``MSP-OSD``** for all the information at the output of Betaflight and the **``HUD DJI``** for all the other information which do not leave Betaflight (Ex: The battery of the googles, the quality of the VTX link, the VTX latency...)

We will also see how to change the location of the DJI HUD elements, change the DJI HUD font, create a new font for MSP-OSD... 

Here is a before/after example of what it is possible to do: (I updated the screenshots and this is my last version to date!)<br />
| Before (**MSP-OSD only**) | After (**MSP-OSD + FakeHD + Custom HUD DJI + Custom Fonts**) |
|-------|-------|
|<img src="img/before.png" width="600">|<img src="img/myosd.png" width="600">|

A video example (the DJI HUD has been added on the video for the example) :<br />

https://user-images.githubusercontent.com/51506790/208981180-be9528f5-7118-47d3-8a71-b43425f159c6.mp4

ℹ️ The info here is from my own experience, all <a href="#readme-top">sources</a> are quoted at the top or bottom of the doc.<br />
⚠️ The manipulations can involve risks (tiny if correctly done), you are the only ones responsible for the actions on your material.

<!-- INSTALL WTFOS -->
# 1. Install WTFOS

Before any manipulation, the googles have to be rooted, for that **WTFOS** has to be installed with [WTFOS-Configurator](https://fpv.wtf/), everything is very well explained in [the official doc](https://github.com/fpv-wtf/wtfos) of fpv-wtf. I advise you to look for tutorials on Youtube.

|![wtfos1](img/wtfos.png)|![wtfos2](img/wtfos2.png)|
|-------|-------|

⚠️ **IMPORTANT:** Before rooting the googles, make sure that the googles and the VTX (Vista/AirUnit) are in the same version.<br />

The software [DJI Assistant 2 FPV](https://www.dji.com/fr/downloads/softwares/dji-assistant-2-dji-fpv-series) allows you to check the version, upgrade or downgrade the firmware of the googles and the VTX. The version **``v01.00.06.06`` known as **``"606"``** is the most used and the one that fits best.

<!-- SERIALPORTS CONFIG -->
## Configure ports

Once the mask is rooted you have to configure the ports on Betaflight. Run this code in the **BetaFlight-Configurator** ``CLI`` :
```
set osd_displayport_device = MSP
set displayport_msp_serial = $
set vcd_video_system = PAL
save
```

*With ``$``, the VTX port number **- 1**.<br /> Example: the VTX is on ``UART1``, so ``displayport_msp_serial = 0``.*

<!-- MOVE MSP-OSD -->
# 2. Move elements of MSP-OSD

Une fois **MSP-OSD** installé (avec ports configurés sur Betaflight) nous pouvons maintenant désactiver le ``"Custom OSD"`` du masque DJI dans :
```
Settings > Display > Custom OSD : off
```
Nous avons maintenant l'OSD complet de Betaflight débloqué. Nous pouvons ajouter / supprimer / changer l'emplacement des éléments directement depuis la section ``OSD`` dans Betaflight :

![osd betaflight](img/osd-betaflight.png)

Nous remarquons que l'OSD Betaflight est obligatoirement dans un format 4:3. Peu importe le format que vous avez choisi pour votre VTX (4:3 ou 16:9) Betaflight ne peut pas afficher un osd plus large que le 4:3. Pour cela il existe une solution du nom de ``FakeHD`` grâce à WTFOS que nous allons détailler dans la section suivante.

<!-- FAKEHD -->
# 3. FakeHD

``FakeHD`` est une solution pour afficher notre OSD dans un format 16:9. Pour comprendre comment le configurer il faut comprendre son fonctionnement :<br/>
L'OSD Betaflight est une grille de 30 lignes et 16 colonnes. Il est impossible de "rajouter" des cases pour étirer le format 4:3 vers un format 16:9. Pour contourner ce probleme, ``FakeHD`` permet de déplacer des "blocs" du format 4:3 pour en faire un format 16:9.<br/>
Explications pas très claires, schéma plus simple :

| Avant (dans Betaflight Configurator) | Après avec ``FakeHD`` (dans le masque) |
| -------|-------|
|![FakeHD Before](/img/fakehd_before.png)|![FakeHD After](/img/fakehd_after.png)|

Sur le schéma on voit les cases de couleur déplacées dans les angles et sur les côtés, mais il y a aussi des cases entièrement blanches. Comme dit plus haut, il est impossible de "rajouter" des cases, ces cases sont donc vides et il est impossible d'afficher des caractères dans les zones blanches.

Exemple simple pour mieux comprendre :
| J'affiche l'élément "Avertissements" de Betaflight mal centré comme ceci :  | Résultat ``FakeHD`` |
| -------|-------|
|![FakeHD Before](/img/osd-betaflight2.png)|![FakeHD After](/img/osd-betaflight3.png)|

C'est un peu bizarre et il faut le prendre en compte quand on place les éléments dans Betaflight.<br/>
Pour plus d'infos et de paramètres n'hésitez pas à vous rendre sur la [doc officielle de FakeHD](https://github.com/fpv-wtf/msp-osd#fakehd).

<!-- INSTALL FAKEHD -->
## Activer et configurer **FakeHD**

Pour activer ``FakeHD``, on connecte le masque à WTFOS [Configurator](https://fpv.wtf/), dans le ``CLI`` on exécute :

```
package-config set msp-osd fakehd_enable true
package-config apply msp-osd
```
C'est fini ``FakeHD`` est activé !<br/>

Malheureusement ça serait trop simple, en effet, à cause de l'exemple du texte coupé vu juste avant, l'écran de fin de vol (les stats) ne peut pas s'afficher correctement. Pour corriger ça, ``FakeHD`` est capable de s'activer pour le vol et se désactiver pour l'écran de fin grâce à un "caractère switch" (Si le caractère s'affiche à l'écran alors ``FakeHD`` s'active, sinon il se désactive).<br/>
Ce "caractère switch" est paramétré par défaut sur le caractère "Thottle icon". Si vous ne voulez pas afficher ce caractère ou souhaitez changer, je vous laisse consulter [la doc](https://github.com/fpv-wtf/msp-osd#menu-switching---getting-rid-of-gaps-when-displaying-menu--post-flight-stats--displaying-centered) qui explique ça très bien.

<!-- WTFOS SPLASHSCREEN -->
# 4. Splashscreen & Screensaver WTFOS
Grâce à WTFOS nous pouvons changer l'écran de fond par défaut du masque DJI. pour cela nous devons avoir installé dans le [WTFOS-Configurator](https://fpv.wtf/) les packages ``image-changer`` et ``image-configurator`` :

![wtfos4](/img/wtfos4.png)

Ensuite nous pouvons laisser le fond de WTFOS ou ajouter un fond personnalisé nommé ``splashscreen.png`` à placer à la racine de la carte SD du masque DJI.
Le format optimal est ``1920x1080``. Plus l'image est grande, plus votre masque est lent au démarrage !

<!-- MSP-OSD FONTS -->
# 5. Les Fonts MSP-OSD

Il est possible de changer la police de l'``OSD MSP-OSD`` (à bien différencier avec L'``HUD DJI``).<br/>
Les fichiers de police se composent en 4 fichiers ``.bin`` à placer à la racine de la carte SD du masque DJI. Ces fichiers seront lus automatiquement au démarrage du masque.<br/>
Dans notre exemple avec Betaflight j'ai : ``font_bf.bin``, ``font_bf_2.bin``,	``font_bf_hd.bin`` et ``font_bf_hd_2.bin``.<br/>
Si ``FakeHD`` n'est pas installé, il vous faut les 4 fichiers, sinon les deux derniers sont suffisants.

Il existe plusieurs polices déja créées (par moi ou d'autres utilisateurs très sympatiques) :

 - [EVilm1's font](https://github.com/EVilm1/EVilm1-OSD-Font)
 - [KNIFA's Material](https://github.com/Knifa/material-osd)
 - [Shannon Baker](https://drive.google.com/drive/folders/1buxrXqhU46AxE3fwaFDsMb97IiGLVa95)
 - [SNEAKY_FPV's colour fonts for INAV, ARDU and BF](https://sites.google.com/view/sneaky-fpv/home)
 - [VICEWIZE Italic](https://github.com/vicewize/vicewizeosdfontset)

Pour une configuration différente ou plus de paramètres voir la [doc officielle de MSP-OSD](https://github.com/fpv-wtf/msp-osd#choose-a-font).
Il est également possible de générer sa propre police (avancé) qui sera détaillé un peu plus bas dans cette doc.

<!-- MOVE HUD DJI -->
# 6. (Config avancée) : Modifier les éléments de l'``HUD DJI``

⚠️ Cette partie consiste à modifier les fichiers de configuration interne du masque DJI, inutile de préciser qu'il faut procéder avec une **EXTREME PRUDENCE**.
Réservé aux utilisateurs avec un minimum d'expérience sur un terminal. **N'exécutez pas de commande que vous ne comprenez pas**. ⚠️

ℹ️ Acceder aux fichiers de configuration nécessite obligatoirement que le masque soit rooté.

Pour acceder aux fichiers internes nous allons utiliser les outils de développement Android ``ADB and Fastboot``.
Par souci de simplicité je vous conseille [Minimal ADB and Fastboot](https://androidmtk.com/download-minimal-adb-and-fastboot-tool) qui est une version allégée mais qui integre toutes les fonctions dont nous avons besoin. Voici une [liste des commandes](https://www.android-mt.com/tutoriel/liste-des-commandes-adb-et-fastboot-loutil-indispensable-du-super-utilisateur-android/74897/) possible.<br/>

Brancher le masque DJI au PC.<br/>
Lancer ``Minimal ADB and Fastboot``. Exécuter :
```
adb start-server
```
Puis, pour afficher les appareils reconnus, exécuter :
```
adb devices
```
Vous devriez obtenir ce résultat :
```
List of devices attached
XXXXXXXXXABCDEF device
```
Si aucun appareil ne s'affiche, assurez-vous que le port série n'est pas déjà occupé par WTFOS-Configurator ou Betaflight ouvert en arrière-plan.<br/>

Par sécurité, nous allons effectuer une sauvegarde du répertoire ou nous allons modifier les fichiers. Exécuter :
```
adb pull system/ [destination]
```
Remplacer ``[destination]`` par le dossier cible sur votre ordinateur ou la sauvegarde sera copié.
Une fois la sauvegarde faite, passez à la suite.

## Modifier l'emplacement des éléments de l'``HUD DJI``
La position des éléments de l'``HUD DJI`` est définie en X et Y dans le fichier nommé ``racing_chnl_osd_win.xml`` situé dans ``/system/gui/xml/``.<br/>
Nous téléchargeons le fichier pour le modifier localement. Exécuter :
```
adb pull /system/gui/xml/racing_chnl_osd_win.xml [destination]
```
Nous pouvons également récupérer ce fichier dans la sauvegarde mais il est préférable de ne pas toucher au dossier par sécurité pour garder le fichier original.
Une fois le fichier récupéré, ouvrez-le avec votre éditeur de code préféré.

### Prévisualisation script Python
Pour nous aider à visualiser les éléments du masque virtuellement nous pouvons utiliser le script python de [Druckgott](https://github.com/druckgott/dji_stuff/tree/581dcb42ac6aa2f282d7b5c5085d97d4312492bd). Téléchargez le ZIP contenant ``show_xml.py`` depuis sa page principale puis décompressez le fichier dans le même répertoire que ``racing_chnl_osd_win.xml``.<br/>
Téléchargez et installez la dernière version de python [ici](https://www.python.org/downloads/).<br/> Pour éxecuter le fichier python, ouvrez un terminal ou Powershell, accédez au répertoire contenant ``show_xml.py`` puis exécuter :
```
python.exe show_xml.py -i racing_chnl_osd_win.xml
```
Une fenêtre de visualisation apparaît :

![show xml](/img/show_xml.jpg)

Nous pouvons cliquer dans la fenêtre pour connaitre la position en px du curseur.<br/>
Pour actualiser cette fenêtre, fermez-la et réexécutez la commande.

### Modifier le fichier ``.xml``

Comme nous pouvons le voir dans la prévisualisation, les éléments s'affichent dans des "blocs". 
Voici un exemple avec la batterie du masque nommé ``gs_voltage`` placé dans le bloc ``racing_gs_voltage_win`` ayant lui-même une positon (``dx`` et ``dy``), une taille (``w`` et ``h``) et un point d'ancrage (``alignment``).

![vscode1](/img/vscode1.png)

Nous pouvons modifier cette position, la taille ou le point d'ancrage (représenté par un point rouge dans la prévisualisation).<br/>
Sauvegarder le fichier, puis actualiser la prévisualisation ``show_xml.py`` pour vérifier les changements.

ℹ️ On notera la présence d'une icône nommée ``gs_battery_icon`` et d'un paramètre de ``gs_voltage`` nommé ``font.name`` qui sera détaillé plus tard dans cette doc.

ℹ️ Le fichier XML que j'ai modifié et que j'ai utilisé dans les exemples au début de la doc est disponible [ici](https://github.com/EVilm1/WIKI-HACK-DJI-OSD/blob/main/racing_chnl_osd_win.xml)

Enfin, une fois les changements effectués, pour uploader ``racing_chnl_osd_win.xml`` dans le masque, avec ``ADB`` exécuter :
```
adb push [cible]/racing_chnl_osd_win.xml /system/gui/xml/
```
Remplacez [cible] par le répertoire contenant votre fichier ``.xml``.<br/>
(Cela aura pour effet d'écraser ``racing_chnl_osd_win.xml`` présent sur le masque, d'où l'importance de la sauvegarde)

Redémarrer le masque pour appliquer les changements.<br/><br/>
⚠️ Si deux éléments se touchent, si un bloc est mal écrit ou incomplet, alors l'élement ne s'affichera pas ou même le masque n'arrivera pas à charger l'osd et risque de redémarrer en boucle.

## Modifier la police de l'``HUD DJI``

Les fichiers de police sont situés dans le dossier : ``system/fonts``. La police par défaut est ``WM150font.ttf``<br/>
Il est possible de copier un nouveau fichier de police au format ``.ttf`` uniquement dans ce même dossier.<br/>
Dans mon cas, j'ai utilisé la police [Conthrax](https://www.dafont.com/fr/conthrax.font?text=EVilm1%27s+Font) que j'ai également utilisé dans [la police que j'ai générée](https://github.com/EVilm1/EVilm1-OSD-Font) pour le ``MSP-OSD``.<br/>

ℹ️ Ne pas renommer le fichier ``.ttf`` sinon ça ne marchera pas et le masque n'arrivera pas à charger l'osd.

Enfin il faut modifier le paramètre ``font.name`` dans le fichier ``racing_chnl_osd_win.xml`` modifié précédemment :

![vscode1](/img/vscode2.png)

Enregistrer le fichier, l'uploader et redémarrer le masque pour appliquer les changements.

## Modifier les icônes de l'``HUD DJI``

Les icônes sont situées dans le dossier : ``system/gui/image``.<br/>
Il est possible de modifier une icône en la téléchargeant, en la modifiant à l'aide d'un logiciel d'édition d'image (de précision) tel que Adobe Photoshop ou Gimp, puis de l'uploader sur le masque dans le même répertoire pour écraser l'icône que vous souhaitez modifier.<br/>

ℹ Il est important de garder la même extension d'image et la même taille (varie selon les icônes).<br/>

Toujours dans le fichier ``racing_chnl_osd_win.xml``, voici le paramètre ``image.name`` où est renseignée l'icône de la batterie du masque par exemple :

![vscode1](/img/vscode3.png)

à vous de modifer les icônes comme bon vous semble.

# 7. (Config avancée) Générer sa propre Font pour ``MSP-OSD``

Pour générer une police, nous utilisons une image ``.png`` au format ``576 x 1728``. Télécharger le projet [mcm2img](https://github.com/Knifa/mcm2img/tree/templates) de [Knifa](https://github.com/Knifa) sur GitHub.<br/>
Pour créer notre OSD nous nous basons sur une grille template.

Pour générer une grille template, se placer à la racine du dossier et exécuter ``template_overlay.py`` avec python :
```
python3 template2img.py template.png
```
Une image ``template_overlay.png`` à été généré à la racine du dossier.<br/>
Ouvrir l'image générée avec votre logiciel d'édition préféré (J'utilise Photoshop mais Gimp est aussi très bien).<br/>
J'ai créé un fichier Photoshop ``template_overlay.psd`` utilisant le fichier ``template_overlay.png`` (avec des repères en plus) que vous pouvez télécharger [ici](https://github.com/EVilm1/WIKI-HACK-OSD-DJI/blob/master/template_overlay.psd) si vous utilisez Photoshop.<br/><br/>
![Photoshop](/img/photoshop_template.png)

Pour savoir ou placer les icones dans la grille, nous pouvons nous calquer sur les fonts classiques de Betaflight [ici](https://github.com/betaflight/betaflight-configurator/tree/master/resources/osd/2) ou sur des fonts HD comme [EVilm1's font](https://github.com/EVilm1/EVilm1-OSD-Font) ou [d'autres fonts HD](https://github.com/EVilm1/WIKI-HACK-DJI-OSD/edit/main/README.md#5-les-fonts-msp-osd).

Exporter l'image toujours en ``.png`` au format ``576 x 1728`` avec un fond alpha (transparent).<br/>

Pour convertir l'image en 4 fichiers ``.bin``, exécuter avec python (en remplaçant le nom de votre image) :<br/>
```
python3 template2img.py [NomDeVotreImage].png
```
4 fichiers ``.bin`` ont été générés à la racine du dossier. Les renommer en ``font_bf.bin``, ``font_bf_2.bin``,	``font_bf_hd.bin``, ``font_bf_hd_2.bin`` (pour Betaflight uniquement).
Enfin, utiliser uniquement ``font_bf_hd.bin`` et ``font_bf_hd_2.bin`` si [FakeHD](https://github.com/EVilm1/WIKI-HACK-DJI-OSD/edit/main/README.md#3-fakehd) est installé, sinon les 4.

Un OSD de qualité demande du temps, bonne chance !<br/>

## Sources / Remerciements

https://github.com/fpv-wtf<br/>
https://github.com/Knifa<br/>
https://github.com/druckgott<br/>
Merci à Sneaky-fpv : https://sites.google.com/view/sneaky-fpv/home<br/>
Merci à Motard Geek et à son article : https://www.wearefpv.fr/tuto-wtfos-hack-dji-full-osd-20221130/<br/>

If this doc helped you and you liked it, you can buy me a coffee 😉 : https://www.buymeacoffee.com/evilm1

<p align="right"><a href="#readme-top">[back to top]</a></p>
