# linux
Algumas anotações gerais Linux

## Virtualbox

```bash

```


## xorg.conf.d

`01-arquivos.conf`
```xorg.conf
Section "Files"
                ModulePath   "/usr/lib/xorg/modules"
                FontPath     "built-ins"
                FontPath     "/usr/lib/xorg/cmap"
                FontPath     "/usr/lib/xorg/cMap"
                FontPath     "/usr/lib/xorg/opentype"
                FontPath     "/usr/lib/xorg/truetype"
                FontPath     "/usr/lib/xorg/type1"
                FontPath     "/usr/share/fonts/X11/100dpi"
                FontPath     "/usr/share/fonts/X11/75dpi"
                FontPath     "/usr/share/fonts/X11/misc"
                FontPath     "/usr/share/fonts/X11/Type1"
                FontPath     "/usr/share/fonts/X11/encodings"
                #FontPath     "/usr/share/fonts/misc"
                #FontPath     "/usr/share/fonts/cyrillic"
                #FontPath     "/usr/share/fonts/100dpi/:unscaled"
                #FontPath     "/usr/share/fonts/75dpi/:unscaled"
                #FontPath     "/usr/share/fonts/Type1"
                #FontPath     "/usr/share/fonts/100dpi"
                #FontPath     "/usr/share/fonts/75dpi"
                #FontPath     "/usr/share/fonts/urwfonts/"
                #FontPath     "/usr/share/fonts/TrueType"
EndSection
```

`02-modulos.conf`
```xorg.conf
Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection
```

`03-teclado.conf`
```xorg.conf
Section "InputDevice"
        Identifier      "Teclado0"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "abnt2"
        Option          "XkbLayout"     "br"
        Option          "xkb_options" "terminate:ctrl_alt_bksp"
EndSection
```

`04-mouse.conf`
```xorg.conf
Section "InputDevice"
        Identifier "Mouse0"
        Driver  "vboxmouse"
        #Driver "mouse"
        Option  "Protocol" "auto"
        Option  "Device" "/dev/input/mice"
        Option  "ZAxisMapping" "4 5 6 7"
EndSection
```

`05-placa-video.conf`
```xorg.conf
Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"                  # [<bool>]
        #Option     "kmsdev"                    # <str>
        #Option     "ShadowFB"                  # [<bool>]
        #Option     "AccelMethod"               # <str>
        #Option     "PageFlip"                  # [<bool>]
        #Option     "ZaphodHeads"               # <str>
        #Option     "DoubleShadow"              # [<bool>]
        #Option     "Atomic"                    # [<bool>]
        Identifier "Placa0"
                Driver  "modesetting"
        VendorName "InnoTek Systemberatung GmbH"
        BoardName "VirtualBox Graphics Adapter"
                #BusID     "pci0:0:2:0"
EndSection
```

`06-monitores.conf`
```xorg.conf
Section "Monitor"
        Identifier   "notebook-positivo-n4350-virtualbox"
        Option "VendorName" "Positivo"
        Option "ModelName" "Monitor do Notebook Positivo-n4350 virtualizado VirtualBox"
        Option "DPMS" "true"
        Modeline "1280x800_59.08"   83.50  1280 1352 1480 1680   800  803  809  831 -hsync +vsync #(49.7 kHz UP)
        Option "PreferredMode" "1280x800_59.08"
EndSection

Section "Monitor"
   Identifier   "HDMI"
EndSection

Section "Monitor"
   Identifier   "VGA"
EndSection

Section "Monitor"
   Identifier   "TV"
EndSection
```

`07-telas.conf`
```xorg.conf
Section "Screen"
   Identifier   "Tela0"
   Device      "Placa0"
   Monitor      "notebook-positivo-n4350-virtualbox"
   DefaultDepth   24
        SubSection "Display"
                Viewport   0 0
                Depth     1
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                                #Modes   "1440x900"
        EndSubSection
EndSection

Section "Screen"
   Identifier   "HDMI"
   Device      "Placa0"
   Monitor      "HDMI"
   DefaultDepth   24
        SubSection "Display"
                Viewport   0 0
                Depth     1
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                                #Modes   "1440x900"
        EndSubSection
EndSection

Section "Screen"
   Identifier   "VGA"
   Device      "Placa0"
   Monitor      "VGA"
   DefaultDepth   24
        SubSection "Display"
                Viewport   0 0
                Depth     1
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                                #Modes   "1440x900"
        EndSubSection
EndSection

Section "Screen"
   Identifier   "TV"
   Device      "Placa0"
   Monitor      "TV"
   DefaultDepth   24
        SubSection "Display"
                Viewport   0 0
                Depth     1
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
                                #Modes   "1440x900"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                                #Modes   "1440x900"
        EndSubSection
EndSection
```

`08-layout.conf`
```xorg.conf
Section "ServerLayout"
        Identifier      "Layout Padrão"
        Screen          "Tela0"
        InputDevice     "Teclado0"
        InputDevice     "Mouse0"
EndSection
```

`09-dri.conf`
```xorg.conf
Section "DRI"
        Mode    0666
EndSection
```



