# TP4-Filtrage Analogique
## Introduction
    Le filtrage analogique est un type de filtrage qui utilise des circuits électroniques pour filtrer des signaux analogiques, c'est-à-dire des signaux continus
    de tension ou de courant. Il peut être utilisé pour séparer différentes bandes de fréquences d'un signal, pour supprimer les bruits indésirables ou pour 
    améliorer la qualité générale d'un signal. Les filtres analogiques peuvent être construits à l'aide de composants électroniques tels que des résistances, 
    des condensateurs et des inductances.
    
## Ojectifs
    1. Appliquer un filtre réel pour supprimer les composantes indésirables d’un signal. 
    2. Améliorer la qualité de filtrage en augmentant l’ordre du filtre.
    
## Réalisation du TP
#### Partie 1 : Filtrage et diagramme de Bode
      * Nous souhaitons appliquer un filtre passe-haut pour supprimer la composante à 50 Hz
      1. Signal x(t)=sin(2.pi.500.t) + sin(2.pi.400.t) + sin(2.pi.50.t) sur t = [0 5] avec Te = 0,0005 s
      2. Traçage du signal et sa TF
        * Apès définir le signal sur t=0:Te:5 et avec Te=5e-4, on a calculé la TF du signal par la fonction "fft" et on a utilisé la fonction "fftshift" pour 
        centrer les fréquences autour de zéro. Ainsi, par la fonction "plot", on a pu tracer dans le premier graphe le signal temporel et sa transformée de Fourier 
        dans le deuxième sous-graphe
        
<img width="840" alt="1 2" src="https://user-images.githubusercontent.com/86896531/213861413-43bc2939-eb56-41ba-b5ff-db51ac563049.png">

      3. Transmittance complexe H(f) du filtre passe haut de premier ordre est donnée par : H(f) = (K.j.w/wc) / (1 + j. w/wc). Avec K le gain du signal, 
          w la pulsation et wc la pulsation de coupure.
          3.1. Traçage du module de la fonction H(f) avec K=1 et wc = 50 rad/s.
            * La courbe de gain est tracée dans le premier sous-graphe en utilisant la fonction "abs" pour calculer la valeur absolue de Hf et la fonction "log" pour 
             calculer le logarithme décimal de cette valeur.La fonction Matlab "semilogx" pour tracer la courbe de gain en décibels de la transmittance complexe 
             d'un filtre passe-haut de premier ordre dans le domaine fréquentiel.
             Ensuite, dans le deuxième sous-graphe, la fonction "plot" est utilisée pour tracer la courbe de phase de la transmittance complexe en utilisant la 
             fonction "angle" pour calculer l'angle de Hf.
<img width="908" alt="1" src="https://user-images.githubusercontent.com/86896531/213862059-b65c72f5-8470-4666-a10f-2f5037950716.png">

          3.2. Traçage 20.log(|H(f)|) pour différentes pulsations de coupure wc
             * Le script trace différents graphes de gain et de phase pour différentes fréquences de coupure wc=50, wc1=100, wc2=150 et wc3=200. La courbe de gain 
             est tracée dans le premiergraphe en utilisant la fonction "abs" pour calculer la valeur absolue de Hf et la fonction "log" pour calculer le logarithme 
             décimal de cette valeur.La fonction Matlab "semilogx" pour tracer la courbe de gain en décibels de la transmittance complexe d'un filtre passe-haut de 
             premier ordre dans le domaine fréquentiel.
             Et de meme pour les graphes de phase.
             
<img width="893" alt="2 1" src="https://user-images.githubusercontent.com/86896531/213862468-67b16ae4-a0ca-4295-8c1a-8711f6b7aef9.png">
<img width="893" alt="2 2" src="https://user-images.githubusercontent.com/86896531/213862479-95398abd-5e37-49f7-b02b-51539544f36e.png">

          3.3. Choisissez différentes fréquences de coupure et appliquez ce filtrage dans l'espace des fréquences.
            * Pour appliquer un filtrage fréquentiel, il faut d'abord effectuer un filtrage temporel sur le signal en utilisant différentes fréquences de coupure  
            wc=50, wc1=100, wc2=150 et wc3=200. Pour ce faire, on utilise la fonction Hf" pour définir la transmittance complexe pour chaque fréquence de coupure 
            et multiplie la transformée de Fourier du signal "y" par la transmittance complexe pour obtenir les signaux filtrés "filtre", "filtre1", "filtre2" et 
            "filtre3".On utilise ensuite la fonction "ifft" pour obtenir les signaux filtrés dans le domaine temporel.
            Enfin, on utilise à nouveau la fonction ""fft" pour obtenir les transformées de Fourier des signaux filtrés dans le domaine fréquentiel.
<img width="858" alt="3 1" src="https://user-images.githubusercontent.com/86896531/213862859-8319d516-5113-48e4-87a4-7e383ca9b2b4.png">
<img width="856" alt="3 2" src="https://user-images.githubusercontent.com/86896531/213862864-f56ba6af-07f9-4b8d-b51a-432a9c56be47.png">

          3.4. Choisissez wc qui vous semble optimal.
          3.5. Observez le signal y(t) obtenu, puis Comparer-le avec le signal que vous auriez souhaité obtenir. Conclusions ?
#### Partie 2 : Dé-bruitage d'un signal sonore
      * Le débruitage est un processus utilisé pour supprimer les bruits indésirables d'une image, d'un signal audio ou d'autres types de données. Il existe 
      différentes techniques de débruitage, chacune ayant ses propres avantages et inconvénients en fonction de l'application. Certaines méthodes utilisent des 
      filtres pour supprimer les fréquences indésirables, tandis que d'autres utilisent des algorithmes pour reconstruire les données à partir de données bruyantes. 
      Le débruitage peut être utilisé pour améliorer la qualité des images, pour réduire le bruit dans les communications, pour améliorer la qualité audio et pour de 
      nombreuses autres applications.

      1. Proposer une méthode pour supprimer ce bruit sur le signal.
          *Un filtre pas-bas permet de laisser passer les fréquences basses du signal, tout en atténuant les fréquences hautes considérées comme du bruit.
      2. Mettez-la en oeuvre. Quelle influence à le paramètre K du filtre que vous avez utilisé ?
          * On définit une fréquence de coupure "fc" de 4500 Hz et on utilise cette valeur pour créer la transmittance complexe "Hf" d'un filtre passe-
          bas de 1er ordre.Cette transmittance est utilisée pour filtrer le signal audio en la multipliant par la transformée de Fourier du signal.La 
          fonction "ifft" est pour obtenir le signal filtré dans le domaine temporel.
          
<img width="848" alt="5" src="https://user-images.githubusercontent.com/86896531/213880459-89364f75-079a-4243-add4-e46f6bb85fc7.png">          

      3. Quelles remarques pouvez-vous faire notamment sur la sonorité du signal final.
          * La sonorité du signal final dépendra de la fréquence de coupure choisie pour le filtre. Si la fréquence de coupure est trop élevée, certaines fréquences
          importantes pour la musique pourraient être supprimées, ce qui aurait pour conséquence d'altérer la qualité sonore. Il est donc important de choisir une 
          fréquence de coupure qui ne supprime pas les fréquences importantes pour la musique.
      4. Améliorer la qualité de filtrage en augmentant l’ordre du filtre. 
          * Pour améliorer la qualité de filtrage, on va augmenter l'ordre du filtre à 1000. Plus l'ordre du filtre est élevé, plus la réponse en fréquence sera 
          plate, ce qui permettra de supprimer efficacement les bruits haute fréquence tout en préservant les fréquences importantes pour la musique.
          
<img width="839" alt="4" src="https://user-images.githubusercontent.com/86896531/213863401-5762eaca-31fb-431b-94c7-b6acbff0be10.png">

## Conclusions
         Le filtrage analogique utilise des circuits électroniques pour filtrer les signaux analogiques. Dans cette manipulation, pour filtrer un signal audio, on a 
         utilisé une transmittance complexe pour créer un filtre passe-bas. Cette méthode est similaire à l'utilisation d'un circuit électronique pour créer un 
         filtre passe-bas analogique. 
         Le filtrage analogique est généralement plus robuste et moins sujet aux erreurs, mais il peut être moins précis et moins flexible, par rapport au filtrage 
         numérique
