---
layout: single
title: OBS Virtual Camera unter macOS
categories: macos
tags: macos conferencing
---

Ich nutze seit einiger Zeit OBS um meine Webcam zu tunen und in Konferenzen oder Trainings ein paar zusätzliche Möglichkeiten zum haben.

Blöderweise wird die OBS Virtual Camera nicht von allen Tools gleichermaßen erkannt.

Mit Zoom funktioniert sie recht gut, ebenso mit Conferencing-Tools in Firefox oder Chrome.
Microsoft Teams, Skype, Discord und Miro erkennen aber die virtuelle Kamera nicht.

Die Lösung dafür findet sich nach einigem Googlen, ich schreibe sie hier aber trotzdem nochmal auf, um mich nicht daran erinnern zu müssen.
Damit die OBS Virtual Camera benutzt werden kann, müssen bei den  Programmen die Signaturen einiger Helper Apps entfernt werden.

## Skype

```
sudo codesign --remove-signature "/Applications/Skype.app/Contents/Frameworks/Skype Helper (Renderer).app"
sudo codesign --remove-signature "/Applications/Skype.app/Contents/Frameworks/Skype Helper (GPU).app"
sudo codesign --remove-signature "/Applications/Skype.app/Contents/Frameworks/Skype Helper (Plugin).app"
sudo codesign --remove-signature "/Applications/Skype.app/Contents/Frameworks/Skype Helper.app"
```

## Microsoft Teams

```
sudo codesign --remove-signature "/Applications/Microsoft Teams.app/Contents/Frameworks/Microsoft Teams Helper.app"
sudo codesign --remove-signature "/Applications/Microsoft Teams.app/Contents/Frameworks/Microsoft Teams Helper (GPU).app"
sudo codesign --remove-signature "/Applications/Microsoft Teams.app/Contents/Frameworks/Microsoft Teams Helper (Plugin).app"
sudo codesign --remove-signature "/Applications/Microsoft Teams.app/Contents/Frameworks/Microsoft Teams Helper (Renderer).app"
```

## Discord

```
sudo codesign --remove-signature "/Applications/Discord.app/Contents/Frameworks/Discord Helper.app/"
sudo codesign --remove-signature "/Applications/Discord.app/Contents/Frameworks/Discord Helper (GPU).app"
sudo codesign --remove-signature "/Applications/Discord.app/Contents/Frameworks/Discord Helper (Plugin).app"
sudo codesign --remove-signature "/Applications/Discord.app/Contents/Frameworks/Discord Helper (Renderer).app"
```

## Miro

```
sudo codesign --remove-signature "/Applications/Miro.app/Contents/Frameworks/Miro Helper.app"
sudo codesign --remove-signature "/Applications/Miro.app/Contents/Frameworks/Miro Helper (GPU).app"
sudo codesign --remove-signature "/Applications/Miro.app/Contents/Frameworks/Miro Helper (Plugin).app"
sudo codesign --remove-signature "/Applications/Miro.app/Contents/Frameworks/Miro Helper (Renderer).app"
```

## Disclaimer

Die Signaturen gibt es nicht umsonst.
Das Entfernen der Signaturen ist aus Perspektive von Sicherheit bedenklich.
Es sollte nur von Menschen gemacht werden, die sich der Konsequenzen bewusst sind.

## Quellen

* [obs-mac-virtualcam Compatibility](https://github.com/johnboiles/obs-mac-virtualcam/wiki/Compatibility)
* [FYI: macOS Virtual Cam on OBS 26.1](https://obsproject.com/forum/threads/fyi-macos-virtual-cam-on-obs-26-1.135468/page-2)