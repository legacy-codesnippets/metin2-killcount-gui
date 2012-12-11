# Metin2 Kill-Counter mit GUI

## Beschreibung
Ein serverseitiger Kill-Counter mit grafischer Benutzeroberfläche (GUI) für Metin2. Dieses Projekt richtet sich an Entwickler und Modder, die das Spiel erweitern möchten.

---

## Implementierung

### Datei: `game.py`

#### Schritt 1: GUI-Elemente hinzufügen

Öffne die Datei `game.py` und suche nach:

```python
self.SetSize(wndMgr.GetScreenWidth(), wndMgr.GetScreenHeight())
```

Füge direkt darunter folgendes hinzu:

```python
##START_KILLGUI
KillGuiBg = ui.AniImageBox()
KillGuiBg.AppendImage("d:/ymir work/ui/blue_killgui_interface.dds")
self.KillGuiBg = KillGuiBg

self.KillGuiBg.SetPosition(wndMgr.GetScreenWidth()-465, 0)

self.KillBlauReich = ui.TextLine()
self.KillBlauReich.SetDefaultFontName()
self.KillBlauReich.SetPosition((wndMgr.GetScreenWidth()-465)+120, 35)
self.KillBlauReich.SetText("Blaues Reich:   NaN")
self.KillBlauReich.SetOutline()

self.KillGelbReich = ui.TextLine()
self.KillGelbReich.SetDefaultFontName()
self.KillGelbReich.SetPosition((wndMgr.GetScreenWidth()-465)+120, 55)
self.KillGelbReich.SetText("Gelbes Reich:    NaN")
self.KillGelbReich.SetOutline()

self.KillRotReich = ui.TextLine()
self.KillRotReich.SetDefaultFontName()
self.KillRotReich.SetPosition((wndMgr.GetScreenWidth()-465)+120, 75)
self.KillRotReich.SetText("Rotes Reich:    NaN")
self.KillRotReich.SetOutline()

self.KillMob = ui.TextLine()
self.KillMob.SetDefaultFontName()
self.KillMob.SetPosition((wndMgr.GetScreenWidth()-465)+120, 95)
self.KillMob.SetText("Monster:    NaN")
self.KillMob.SetOutline()
##END_KILLGUI
```

---

#### Schritt 2: Server-Kommandos erweitern

Suche nach:

```python
serverCommandList={
```

Erweitere das Dictionary um folgende Einträge:

```python
##KILLGUI
"ShowKillGui": self.__showkillgui,
"HideKillGui": self.__hidekillgui,
"KillBlauReich": self.__KillBlauReich,
"KillGelbReich": self.__KillGelbReich,
"KillRotReich": self.__KillRotReich,
"KillMob": self.__KillMob,
##END_KILLGUI
```

---

#### Schritt 3: Methoden am Ende der Datei hinzufügen

Gehe ans Ende der `game.py` und füge folgendes hinzu:

```python
def __hidekillgui(self):
    self.KillGuiBg.Hide()
    self.KillBlauReich.Hide()
    self.KillGelbReich.Hide()
    self.KillRotReich.Hide()
    self.KillMob.Hide()

def __showkillgui(self):
    self.KillGuiBg.Show()
    self.KillBlauReich.Show()
    self.KillGelbReich.Show()
    self.KillRotReich.Show()
    self.KillMob.Show()

def __KillBlauReich(self, KillBlauReich):
    self.KillBlauReich.SetText("Blaues Reich:    " + KillBlauReich)

def __KillGelbReich(self, KillGelbReich):
    self.KillGelbReich.SetText("Gelbes Reich:    " + KillGelbReich)

def __KillRotReich(self, KillRotReich):
    self.KillRotReich.SetText("Rotes Reich:    " + KillRotReich)

def __KillMob(self, KillMob):
    self.KillMob.SetText("Monster:    " + KillMob)
```

---

## Sonstiges

Die Datei `blue_killgui_interface.dds` muss in die `etc.eix/epk` eingefügt werden:

```
ymir work/ui/blue_killgui_interface.dds
```
