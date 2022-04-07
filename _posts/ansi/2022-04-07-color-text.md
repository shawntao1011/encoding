---
title: color text
author: Tao Sun
date: 2022-04-07 11:03:00 +0800
category: ANSI
layout: post
---

## how to output color text

### ansi color
   Colored text output in console is realized by ANSI ESCAPE SEQUENCE. The format is 
   ```
   ESC[<foreground-color code>;<background-color code>m<text>ESC[0m
   ```
   "ESC[0m" is reset to previous color setting.

   ASCII code for ESC 27(decimal) 0x1B(hex) 033(octal) or \e(escape code).
   
   The following code will generate red "Hello" on a white background.
   ```
   echo -e "\x1b[31;4mHello\x1b[0m"
   ```


### difference in windows
   1.For windows cmd, no -e option is available. And the ESC character need to be entered directly.
   <font color=red>The Esc character must be entered with the key combination Ctrl+[</font>.

   In some text editors this will appear as ^[ or Esc[
   ```
   echo ^[[31;4mhello^[[0m
   ```
   
   2.For powershell, though the official sit claim the following will show up correctly:
   ```
   "`e[5;36mHello`e[0m"
   ```
   but from my experience, the above code does <font color=red>not</font> work properly.

   Code works:
   ```
   $Esc=[char]0x1b
   "$Esc[91;4mHello$Esc[0m"
   ```

