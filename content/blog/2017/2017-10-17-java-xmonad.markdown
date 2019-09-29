---
title: Fix GUI when using java apps in xmonad
date: 2017-10-17
---

### Fix GUI when using java apps on xmonad

You need to set the right startupHook , which is

import XMonad.Hooks.SetWMName
...

main = do
    xmonad $ defaultConfig
    { modMask = mod4Mask
    , startupHook = setWMName "LG3D"
    -- other customizations
    }

The complete guide is found at
https://wiki.haskell.org/Xmonad/Frequently_asked_questions#Preferred_Method

