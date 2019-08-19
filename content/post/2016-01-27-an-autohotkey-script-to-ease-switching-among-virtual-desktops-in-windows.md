---
title: An AutoHotKey Script to Ease Switching Among Virtual Desktops in Windows
author: 'kurtis'
date: '2016-01-27'
slug: an-autohotkey-script-to-ease-switching-among-virtual-desktops-in-windows
categories:
  - Research
tags:
  - coding
  - tools
  - AutoHotKey
draft: no
summary:
image:
  caption: ''
  focal_point: ''
highlight_languages: ["autohotkey"]

---

*Update: as of 2019 I have switched to Linux and no longer use this script. I have no reason to believe it has stopped working, but I make no guarantees.*

I am a big fan of [AutoHotKey][]. It lets me make a lot of parts of computer interaction faster and easier for me. My most recent project was to make it faster and easier to switch between virtual desktops on my Windows 10 computer. Apple and Linux machines have employed virtual desktops for a long time, but Windows really lagged behind in this area. As a result, I was late to the party in adopting them. The easiest way to think about multiple desktops is to think about them as being literally multiple desktops that you are working on. If you have an office with a swivel chair, you know how easy it can be to swivel from the work you are doing on one desk to the reference documents you have laid out on another desk. Using virtual desktops works the same way.

Unfortunately, Windows hasn't made creating or switching between multiple desktops very easy. First, you have to create all of the virtual desktops manually, which you can do by pressing the Windows key and the Tab key simultaneously. Then you need to click on the "New Desktop" link in the lower right corner of the screen. After that, you can switch between them by going to this selection screen, or with a keyboard shortcut by holding down the Windows key and the Control key while using the arrow keys to switch back and forth.

This system is terrible. Using three keys at once is a pain, and the keys aren't even on the same side of the keyboard, so I can't switch one handed. Fortunately, I know how to fiddle with AutoHotKey to make things work better. I wrote this short script so I could hold down the blank key in the middle of my number pad (the "5" key when NumLock is on) and switch back and forth by using the left and right arrows. This key didn't do anything anyway, so it isn't really a loss. This was my initial script:

```autohotkey
; switch to previous virtual desktop with NumLock Off
NumpadClear & NumpadLeft::sendInput {LWin down}{LCtrl down}{Left}{LWin up}{LCtrl up}
; switch to next virtual desktop with NumLock off
NumpadClear & NumpadRight::sendInput {LWin down}{LCtrl down}{Right}{LWin up}{LCtrl up}
```

That's right, it's only two lines long, but it worked great! Soon, I realized that I use it a lot and toggling NumLock was annoying. In addition, if I added a couple lines to the script, the "5" key would always function normally anyway, unless I pressed another button while it was down. I added a few lines to the script and it was even better:

```autohotkey
; switch to previous virtual desktop with NumLock On
Numpad5 & Numpad4::sendInput {LWin down}{LCtrl down}{Left}{LWin up}{LCtrl up}
; switch to next virtual desktop with NumLock On
Numpad5 & Numpad6::sendInput {LWin down}{LCtrl down}{Right}{LWin up}{LCtrl up}
; switch to previous virtual desktop with NumLock Off
NumpadClear & NumpadLeft::sendInput {LWin down}{LCtrl down}{Left}{LWin up}{LCtrl up}
; switch to next virtual desktop with NumLock off
NumpadClear & NumpadRight::sendInput {LWin down}{LCtrl down}{Right}{LWin up}{LCtrl up}
Numpad5::sendInput {Numpad5}
NumpadClear::sendevent {NumpadClear}
```

Now the script worked when NumLock was on and when it was off. It was perfect, except about 2 weeks later I was using my mouse and got annoyed with having to go back and forth between the keyboard and the mouse, since my number pad is also on the right side of my laptop. Then it hit me, I could switch back and forth using the left and right clicks on the mouse wheel, which I have never used for scrolling anyway. So, I added a few more lines to the script.

```autohotkey
; use Numpad keys to Navigate multiple virtual desktops

; switch to previous virtual desktop with NumLock On
Numpad5 & Numpad4::sendInput {LWin down}{LCtrl down}{Left}{LWin up}{LCtrl up}
; switch to next virtual desktop with NumLock On
Numpad5 & Numpad6::sendInput {LWin down}{LCtrl down}{Right}{LWin up}{LCtrl up}
; switch to previous virtual desktop with NumLock Off
NumpadClear & NumpadLeft::sendInput {LWin down}{LCtrl down}{Left}{LWin up}{LCtrl up}
; switch to next virtual desktop with NumLock off
NumpadClear & NumpadRight::sendInput {LWin down}{LCtrl down}{Right}{LWin up}{LCtrl up}
Numpad5::sendInput {Numpad5}
NumpadClear::sendevent {NumpadClear}

; use mouse wheel scroll left & right to navigate virtual desktops

; switch to previous virtual desktop
WheelLeft::SendInput {LWin down}{LCtrl down}{Left}{LWin up}{LCtrl up}
; switch to next virtual desktop
WheelRight::SendInput {LWin down}{LCtrl down}{Right}{LWin up}{LCtrl up}
```

Now it's perfect. I can spin my virtual chair between as many virtual desktops as I like. Now I can keep my e-mail and calendar up on one desktop and check it in a moment, rather than keeping it buried in a tab in my minimized browser. Now I can write in my dissertation and quickly skip over to look through a reference or my Zotero library quickly. I love it.

[AutoHotKey]: https://autohotkey.com/
