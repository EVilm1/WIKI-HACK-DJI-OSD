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
  --- English version almost finished! ---<br /><br />

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
    <li><a href="#intro">Intro</a>
      <ul>
        <li><a href="#example">Example</a></li>
      </ul>
    </li>
  </ol>
  <ol>
    <li><a href="#1-install-wtfos">Install WTFOS</a>
      <ul>
        <li><a href="#configure-ports">Configure ports</a></li>
      </ul>
    </li>
    <li><a href="#2-move-elements-of-msp-osd">Move elements of MSP-OSD</a></li>
    <li><a href="#3-fakehd">FakeHD</a></li>
      <ul>
        <li><a href="#enable-and-configure-fakehd">Enable and configure FakeHD</a></li>
      </ul>
    </li>
    <li><a href="#4-splashscreen--screensaver-wtfos">Splashscreen & Screensaver WTFOS</a></li>
    <li><a href="#5-msp-osd-fonts">MSP-OSD Fonts</a></li>
    <li> <a href="#6-advanced-setup-modify-the-dji-hud-elements">(Advanced config): Modify the DJI HUD elements</a>
      <ul>
        <li><a href="#move-the-dji-hud-elements">Move the DJI HUD elements</a></li>
          <ul>
            <li><a href="#python-script-to-preview">Python script to preview</a></li>
            <li><a href="#edit-the-xml-file">Edit the .xml file</a></li>
          </ul>
        <li><a href="#change-the-font-of-the-dji-hud">Change the font of the DJI HUD</a></li>
        <li><a href="#change-the-dji-hud-icons">Change the DJI HUD icons</a></li>
      </ul>
    </li>
    <li><a href="#7-advanced-config-generate-your-own-font-for-msp-osd">(Advanced config): Generate your own Font for MSP-OSD</a></li>
    <li><a href="#sources--credits">Sources / Credits</a></li>
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

Once the googles is rooted you have to configure the ports on Betaflight. Run this code in the **BetaFlight-Configurator** ``CLI`` :
```
set osd_displayport_device = MSP
set displayport_msp_serial = $
set vcd_video_system = PAL
save
```

*With ``$``, the VTX port number **- 1**.<br /> Example: the VTX is on ``UART1``, so ``displayport_msp_serial = 0``.*

<!-- MOVE MSP-OSD -->
# 2. Move elements of MSP-OSD

Once **MSP-OSD** is installed (with ports configured on Betaflight) we can now disable the "Custom OSD" of the DJI googles in :
```
Settings > Display > Custom OSD : off
```
We now have the full OSD of Betaflight unlocked. We can add / remove / change the location of elements directly from the "OSD" section in Betaflight :

![osd betaflight](img/osd-betaflight.png)

We note that the Betaflight OSD is necessarily in a 4:3 format. No matter what format you have chosen for your VTX (4:3 or 16:9) Betaflight cannot display an OSD wider than 4:3. For this there is a solution called ``FakeHD`` thanks to WTFOS which we will describe in detail in the next section.

<!-- FAKEHD -->
# 3. FakeHD

``FakeHD`` is a solution to display our OSD in a 16:9 format. To understand how to set it up you need to understand how it works:<br/>
The Betaflight OSD is a grid of 30 rows and 16 columns. It is impossible to "add" cells to stretch the 4:3 format to a 16:9 format. To get around this problem, ``FakeHD`` allows to move "blocks" of the 4:3 format to make a 16:9 format.<br/>
Explanations not very clear, simpler scheme :

| Before (in Betaflight Configurator) | After with ``FakeHD`` (in the googles) |
| -------|-------|
|![FakeHD Before](/img/fakehd_before.png)|![FakeHD After](/img/fakehd_after.png)|

On the scheme you can see the colored cells moved to the corners and sides, but there are also completely white cells. As mentioned above, it is impossible to "add" cells, so these cells are empty and it is impossible to display characters in the white areas.

A simple example to better understand :
| I display the "Warnings" element of Betaflight badly centered like this:  | ``FakeHD`` Result |
| -------|-------|
|![FakeHD Before](/img/osd-betaflight2.png)|![FakeHD After](/img/osd-betaflight3.png)|

This is a bit odd and should be taken into consideration when placing elements in Betaflight.<br/>
For more info and settings please visit the [official FakeHD doc](https://github.com/fpv-wtf/msp-osd#fakehd).

<!-- INSTALL FAKEHD -->
## Enable and configure **FakeHD**

To activate ``FakeHD``, connect the googles to WTFOS [Configurator](https://fpv.wtf/), in the ``CLI`` run :

```
package-config set msp-osd fakehd_enable true
package-config apply msp-osd
```
That's it ``FakeHD`` is enabled!<br/>

Unfortunately it would be too simple, because of the example of the cut text seen just before, the end of flight screen (the stats) cannot be displayed correctly. To correct this, ``FakeHD`` is able to turn on for the flight and turn off for the end screen thanks to a "character switch" (If the character is displayed on the screen then ``FakeHD`` turns on, otherwise it turns off).<br/>
This "character switch" is set by default on the character "Throttle Position". If you don't want to display this character or want to change it, I let you read [the doc](https://github.com/fpv-wtf/msp-osd#menu-switching---getting-rid-of-gaps-when-displaying-menu--post-flight-stats--displaying-centered) which explains it very well.
Personally, I use the crosshair icon (number 115) [in the doc again!](https://github.com/betaflight/betaflight/blob/master/docs/osd.md)

<!-- WTFOS SPLASHSCREEN -->
# 4. Splashscreen & Screensaver WTFOS
Thanks to WTFOS we can change the default background screen of the DJI googles. For this we need to have installed in the [WTFOS-Configurator](https://fpv.wtf/) the packages ``image-changer`` and ``image-configurator`` :

![wtfos4](/img/wtfos4.png)

Then we can keep the WTFOS background or add a custom background named ``splashscreen.png`` to be placed at the root of the SD card of the DJI googles.
The optimal format is ``1920x1080``. The larger the image, the slower your googles will start!

<!-- MSP-OSD FONTS -->
# 5. MSP-OSD Fonts

It is possible to change the font of the MSP-OSD (be careful to distinguish it from the DJI HUD).<br/>
The font files consist of 4 .bin files to be placed at the root of the SD card of the DJI googles. These files will be read automatically when the goggles start up.<br/>
In our example with Betaflight I have : ``font_bf.bin``, ``font_bf_2.bin``,	``font_bf_hd.bin`` and ``font_bf_hd_2.bin``.<br/>
If ``FakeHD`` is not installed, you need all 4 files, otherwise the last two are sufficient.

There are several fonts already created (by me or other very nice users) :

 - [EVilm1's font](https://github.com/EVilm1/EVilm1-OSD-Font)
 - [KNIFA's Material](https://github.com/Knifa/material-osd)
 - [Shannon Baker](https://drive.google.com/drive/folders/1buxrXqhU46AxE3fwaFDsMb97IiGLVa95)
 - [SNEAKY_FPV's colour fonts for INAV, ARDU and BF](https://sites.google.com/view/sneaky-fpv/home)
 - [VICEWIZE Italic](https://github.com/vicewize/vicewizeosdfontset)

For a different configuration or more parameters see the [official MSP-OSD doc](https://github.com/fpv-wtf/msp-osd#choose-a-font).
It is also possible to generate your own font (advanced) which will be detailed a bit lower in this doc.

<!-- MOVE HUD DJI -->
# 6. (Advanced Setup) Modify the ``DJI HUD`` elements

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

## Move the ``DJI HUD`` elements
La position des éléments de l'``HUD DJI`` est définie en X et Y dans le fichier nommé ``racing_chnl_osd_win.xml`` situé dans ``/system/gui/xml/``.<br/>
Nous téléchargeons le fichier pour le modifier localement. Exécuter :
```
adb pull /system/gui/xml/racing_chnl_osd_win.xml [destination]
```
Nous pouvons également récupérer ce fichier dans la sauvegarde mais il est préférable de ne pas toucher au dossier par sécurité pour garder le fichier original.
Une fois le fichier récupéré, ouvrez-le avec votre éditeur de code préféré.

### Python script to preview
Pour nous aider à visualiser les éléments du masque virtuellement nous pouvons utiliser le script python de [Druckgott](https://github.com/druckgott/dji_stuff/tree/581dcb42ac6aa2f282d7b5c5085d97d4312492bd). Téléchargez le ZIP contenant ``show_xml.py`` depuis sa page principale puis décompressez le fichier dans le même répertoire que ``racing_chnl_osd_win.xml``.<br/>
Téléchargez et installez la dernière version de python [ici](https://www.python.org/downloads/).<br/> Pour éxecuter le fichier python, ouvrez un terminal ou Powershell, accédez au répertoire contenant ``show_xml.py`` puis exécuter :
```
python.exe show_xml.py -i racing_chnl_osd_win.xml
```
Une fenêtre de visualisation apparaît :

![show xml](/img/show_xml.jpg)

Nous pouvons cliquer dans la fenêtre pour connaitre la position en px du curseur.<br/>
Pour actualiser cette fenêtre, fermez-la et réexécutez la commande.

### Edit the ``.xml`` file

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

## Change the font of the ``DJI HUD``

Les fichiers de police sont situés dans le dossier : ``system/fonts``. La police par défaut est ``WM150font.ttf``<br/>
Il est possible de copier un nouveau fichier de police au format ``.ttf`` uniquement dans ce même dossier.<br/>
Dans mon cas, j'ai utilisé la police [Conthrax](https://www.dafont.com/fr/conthrax.font?text=EVilm1%27s+Font) que j'ai également utilisé dans [la police que j'ai générée](https://github.com/EVilm1/EVilm1-OSD-Font) pour le ``MSP-OSD``.<br/>

ℹ️ Ne pas renommer le fichier ``.ttf`` sinon ça ne marchera pas et le masque n'arrivera pas à charger l'osd.

Enfin il faut modifier le paramètre ``font.name`` dans le fichier ``racing_chnl_osd_win.xml`` modifié précédemment :

![vscode1](/img/vscode2.png)

Enregistrer le fichier, l'uploader et redémarrer le masque pour appliquer les changements.

## Change the ``DJI HUD`` icons

Les icônes sont situées dans le dossier : ``system/gui/image``.<br/>
Il est possible de modifier une icône en la téléchargeant, en la modifiant à l'aide d'un logiciel d'édition d'image (de précision) tel que Adobe Photoshop ou Gimp, puis de l'uploader sur le masque dans le même répertoire pour écraser l'icône que vous souhaitez modifier.<br/>

ℹ Il est important de garder la même extension d'image et la même taille (varie selon les icônes).<br/>

Toujours dans le fichier ``racing_chnl_osd_win.xml``, voici le paramètre ``image.name`` où est renseignée l'icône de la batterie du masque par exemple :

![vscode1](/img/vscode3.png)

à vous de modifer les icônes comme bon vous semble.

# 7. (Advanced config): Generate your own Font for ``MSP-OSD``

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

## Sources / Credits

https://github.com/fpv-wtf<br/>
https://github.com/Knifa<br/>
https://github.com/druckgott<br/>
Thanks to Sneaky-fpv: https://sites.google.com/view/sneaky-fpv/home<br/>
Thanks to Motard Geek and his article : https://www.wearefpv.fr/tuto-wtfos-hack-dji-full-osd-20221130/<br/>

**If this doc helped you and you liked it, you can buy me a coffee 😉 :** https://www.buymeacoffee.com/evilm1

<p align="right"><a href="#readme-top">[back to top]</a></p>
