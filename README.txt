vcs-merge-status - report what changes have been merged or missing

  dc at aplikacja.info

Sometimes you have to check merge status between your release branches to see
what changes are missing on particular branch. vcs-merge-status can produce
such report, an real-life example:

  $ git checkout master
  $ vcs-merge-status RELEASE_1.0.7_base..RELEASE_1.0.7_branch
  + 0246359 Marcin (#11911) XYZ>Infopage>Redmine: 2719> A message appears:  Videotheek - Geen item of geen abonnement  needs to be updated.
  + f200e8e robal (#10641) fixes in help videos screen stylesheet g
  + f1bbe6b Mateusz (#11018, #) - Increased non-AC-3 volume by 4dB, volume should be set properly at startup.
  + 9a5e8b7 Dariusz Fixed runtime assert during audio init: audio.c:840: initialized != true (#11018)
  + bb869ab Dariusz (#11147) (LOEWE) Use most current vout state during sink state update processingg
  + e9ab214 Dariusz Proper import of VIDEO_MODE_1080P25 and VIDEO_MODE_1080P50 Reno video modes (#10182)
  + 541d49b Dariusz Hiding 34_169 selection only when HDMI is connected (#12647)
  C f86a81b Hong code style fix
  C 41d24d5 Hong (#11911) ui/VodIml - popup text change
  + fabfff7 Dariusz Fixed ABC TV On Demand path in VODConfig.plist (#11109)
  + c9ec8fb Dariusz Fixed VOD categories mappings to skins (#11109)
  C cee31f6 Dariusz Visual fixes in QSS (#11109)
  C ebbec83 Dariusz Skins updates (#11109)
  + 0faea22 Dariusz Fixed key = 0 infinite loop (#11794)
  + f0a989d Dariusz TM notified on new address (bridge mode) + UI system info screen updated (#13600)
  + 588cd81 Dariusz Fixed missing OCI call with iprenew (#13600)
  + 7a167fc Dariusz Revert  Fixed key = 0 infinite loop (#11794)
  C 332c4dc Piotr (#12547) Pause stream when ClearPLTV popup appears from MainMenug
  + 33d2dc8 Piotr (#12610) Fixed left/right nav arrows in NET5 and DiscoveryChannel PG screensg
  + 6eafd11 Dariusz Revert  Revert  Fixed key = 0 infinite loop (#11794)
  already merged: 7
  to be merged (+): 15
  to be merged, but with conflict (C): 5

You can restrict merge status to single author, for example:

  $ git-merge-status RELEASE_1.0.7_base..RELEASE_1.0.7_branch --author=dc@
  C 9a5e8b7 Dariusz Fixed runtime assert during audio init: audio.c:840: initialized != true (#11018)
  + e9ab214 Dariusz Proper import of VIDEO_MODE_1080P25 and VIDEO_MODE_1080P50 Reno video modes (#10182)
  + 541d49b Dariusz Hiding 34_169 selection only when HDMI is connected (#12647)
  + fabfff7 Dariusz Fixed ABC TV On Demand path in VODConfig.plist (#11109)
  + c9ec8fb Dariusz Fixed VOD categories mappings to skins (#11109)
  C cee31f6 Dariusz Visual fixes in QSS (#11109)
  C ebbec83 Dariusz Skins updates (#11109)
  + 0faea22 Dariusz Fixed key = 0 infinite loop (#11794)
  + f0a989d Dariusz TM notified on new address (bridge mode) + UI system info screen updated (#13600)
  + 588cd81 Dariusz Fixed missing OCI call with iprenew (#13600)
  + 7a167fc Dariusz Revert  Fixed key = 0 infinite loop (#11794)
  + 6eafd11 Dariusz Revert  Revert  Fixed key = 0 infinite loop (#11794)
  already merged: 1
  to be merged (+): 9
  to be merged, but with conflict (C): 3

And so on.

Script leaves your local working copy with "+"-es included, so you can push them (if you prefer) or reset to origin state:

   git reset --hard origin/master


