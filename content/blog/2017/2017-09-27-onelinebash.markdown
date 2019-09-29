---
title: bash oneliner - little rain color
date: 2017-09-27
---
## 2019 edit: It needs a review but, omg, it's so cool! LOL

 col=0;lin=0; while true; do x=$(shuf -i 1-7 -n 1); if (( $lin > 30 )); \
 then lin=0;fi; if (( $col > 100)); then col=0; fi; tput cup $lin $col; \
 tput setab $x;  a=$(shuf -i 1-3 -n 1); if (( a == 1 )); then printf "   " \
; elif (( a == 2 )); then printf ' %.0s' $(seq $y); else printf "   \
"; fi;((col++));((lin++)); done
