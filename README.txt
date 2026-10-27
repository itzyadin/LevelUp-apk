LEVEL UP - ANDROID APP (APK) BUILT BY GITHUB, FREE
===================================================

This opens your hosted Level Up app full screen, like a normal app. Google sign-in works
(it runs inside Chrome) and Level Up can link with Forma through the same Google account.
To change the app later you only redeploy the website - the APK updates itself.

BEFORE YOU BUILD - you need your Level Up web address
-----------------------------------------------------
1. Deploy levelup-web.zip to Netlify as a NEW site (Netlify > Add new site > Deploy manually,
   drag the levelup-web folder). Netlify gives you an address like
       https://sparkly-name-123.netlify.app
   (you can rename it in Site configuration > Change site name).
2. Tell Claude that address and you get this project back finished - OR do it yourself:
   open these two files in Notepad and replace  YOUR-LEVELUP-SITE  with the part before
   .netlify.app (3 places in total):
       app/src/main/AndroidManifest.xml     (2 places)
       app/src/main/res/values/strings.xml  (1 place)
3. Check this opens in Chrome and shows text starting with  [ { "relation" ...
       https://YOUR-ADDRESS.netlify.app/.well-known/assetlinks.json

STEP 1 - Put this folder on GitHub (PowerShell, inside this folder)
-------------------------------------------------------------------
New empty repo on github.com named  LevelUp-apk  (Add a README = OFF). Then:

   cd "C:\path\to\LevelUpAPK"
   git init
   git add .
   git commit -m "Level Up APK"
   git branch -M main
   git remote add origin https://github.com/YOUR-GITHUB-NAME/LevelUp-apk.git
   git push -u origin main

(If git says "Please tell me who you are": git config --global user.name "Yadin" and
 git config --global user.email "your-github-email@example.com", then commit again.)

STEP 2 - GitHub builds it (3-5 minutes)
---------------------------------------
Repo > Actions > "Build APK" > green check > open the run > Artifacts > LevelUp-apk.
Unzip it: inside is LevelUp.apk.

STEP 3 - Install on the phone
-----------------------------
Send LevelUp.apk to the phone, tap it, allow "install unknown apps", Install anyway if
Play Protect warns. NOTE: your old Level Up (the one with local files) has a different
package name, so this installs NEXT TO it. Open the new one, tap Profile > Connect with
Google. Your old progress does not move over automatically - ask Claude for an export if
you want to bring it across.

If the build fails: open the failed run, click the red step, copy the last ~30 lines and
send them to Claude. The Android build could not be run while this was prepared, so the
first run is the real test.

Package name: app.levelup.life   Signing key: signing/forma-debug.keystore (password: android)
