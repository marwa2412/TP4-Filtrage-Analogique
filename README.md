# TP4-Filtrage Analogique
## Ojectifs
    1. Appliquer un filtre réel pour supprimer les composantes indésirables d’un signal. 
    2. Améliorer la qualité de filtrage en augmentant l’ordre du filtre.
    
## Introduction
    Le filtrage analogique est un type de filtrage qui utilise des circuits électroniques pour filtrer des signaux analogiques, c'est-à-dire des signaux continus
    de tension ou de courant. Il peut être utilisé pour séparer différentes bandes de fréquences d'un signal, pour supprimer les bruits indésirables ou pour 
    améliorer la qualité générale d'un signal. Les filtres analogiques peuvent être construits à l'aide de composants électroniques tels que des résistances, 
    des condensateurs et des inductances.
## Réalisation du TP
#### Partie 1 : Filtrage et diagramme de Bode
      *Nous souhaitons appliquer un filtre passe-haut pour supprimer la composante à 50 Hz
      1. Signal x(t)=sin(2.pi.500.t) + sin(2.pi.400.t) + sin(2.pi.50.t) sur t = [0 5] avec Te = 0,0001 s
      2. Traçage du signal et sa TF
      3. Transmittance complexe H(f) du filtre passe haut de premier ordre est donnée par : H(f) = (K.j.w/wc) / (1 + j. w/wc). Avec K le gain du signal, 
          w la pulsation et wc la pulsation de coupure.
          3.1. Traçage du module de la fonction H(f) avec K=1 et wc = 50 rad/s.
          3.2. Traçage 20.log(|H(f)|) pour différentes pulsations de coupure wc
          3.3 Choisissez différentes fréquences de coupure et appliquez ce filtrage dans l'espace des fréquences.
          3.4 Choisissez wc qui vous semble optimal.
          3.5 Observez le signal y(t) obtenu, puis Comparer-le avec le signal que vous auriez souhaité obtenir. Conclusions ?
#### Partie 2 : Dé-bruitage d'un signal sonore
      1. Proposer une méthode pour supprimer ce bruit sur le signal.
          * Une méthode couramment utilisée pour supprimer les bruits haute fréquence sur un signal est l'utilisation d'un filtre passe-bas. Ce filtre permet de 
          laisser passer les fréquences basses du signal, tout en atténuant les fréquences hautes considérées comme du bruit.
      2. Mettez-la en oeuvre. Quelle influence à le paramètre K du filtre que vous avez utilisé ?
          * Pour mettre en oeuvre cette méthode, vous pouvez utiliser un filtre de Butterworth, qui est un filtre passe-bas de type analogique dont la réponse en 
          fréquence est maximale à la fréquence de coupure choisie. Le paramètre K du filtre Butterworth détermine l'atténuation des fréquences hautes en dehors de
          la bande passante. Plus K est élevé, plus l'atténuation sera importante.
      3. Quelles remarques pouvez-vous faire notamment sur la sonorité du signal final.
          * La sonorité du signal final dépendra de la fréquence de coupure choisie pour le filtre. Si la fréquence de coupure est trop élevée, certaines fréquences
          importantes pour la musique pourraient être supprimées, ce qui aurait pour conséquence d'altérer la qualité sonore. Il est donc important de choisir une 
          fréquence de coupure qui ne supprime pas les fréquences importantes pour la musique.
      4. Améliorer la qualité de filtrage en augmentant l’ordre du filtre. 
          * Pour améliorer la qualité de filtrage, vous pouvez augmenter l'ordre du filtre. Plus l'ordre du filtre est élevé, plus la réponse en fréquence sera 
          plate, ce qui permettra de supprimer efficacement les bruits haute fréquence tout en préservant les fréquences importantes pour la musique.
          Il est important de noter que l'augmentation de l'ordre du filtre peut augmenter le temps de calcul nécessaire pour filtrer le signal.

## Conclusions
