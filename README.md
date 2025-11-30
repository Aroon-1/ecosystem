ATSOBOLO ELONG AROON AN-ING 1
25P924

*PROJET DE SIMULATION D'ECOSYSTEME intelligent*
---
**🎯 Objectif Pédagogique :**

Créer un simulateur d'écosystème en C++ utilisant la POO, SDL3 pour la visualisation, et mettant en pratique :
---
développer un écosystème virtuel où différentes entités (animaux, plantes) interagissent selon des règles biologiques simples. Le but est d'observer l'évolution de la population et les comportements émergents.
---

📁 Structure des Fichiers
---
ecosystem_simulator/
├── include/
│   ├── Core/
│   │   ├── Structs.hpp
│   │   ├── Entity.hpp
│   │   └── Ecosystem.hpp
│   └── Graphics/
│       ├── Window.hpp
│       └── Renderer.hpp
├── src/
│   ├── Core/
│   │   ├── Entity.cpp
│   │   └── Ecosystem.cpp
│   ├── Graphics/
│   │   ├── Window.cpp
│   │   └── Renderer.cpp
│   └── main.cpp
├── assets/
│   └── (futures textures)
└── README.md
---

***fonctions implementes : ***
---
_Vector2D StayInBounds(float worldWidth, float worldHeight) const;_
---
cette fonction permet de garder les entites dans la zone delimite par la fenetre, nous avons utilise
plusieurs condition dans le but de d'eviter que les entites sortent des 4 cotes notemment :
---
    if(p.x < 12.0f) p.x=12.0f;
    if(p.x > worldWidth) p.x =worldWidth-12.0f;
    if(p.y <12.0f) p.y =12.0f;
    if(p.y > worldHeight) p.y =worldHeight-12.0f;
---
l'entite sera donc renvoye a la limite a chque fois qu'elle essaiera de la franchir.
_la seconde fonction implemente est : Vector2D Entity::SeekFood(const std::vector<Food>& foodSources)
 const;_

 le but ici est de trier un ensemble de position a fin d'envoyer les coordonnes de celle qui est la plus proche.

 au depart, on stock la position et la distance initiale, puis on parcourt les suivantes en stockant la plus petite a chaque incrementation.
 comme suite :
 ---
 
    for(size_t i=1; i<=foodSources.size(); i++)
    {

        // Calcule la distance entre l'entité et cette nourriture
            float d = (foodSources[i].position).Distance(position);

            // Si cette distance est plus petite que celle déjà enregistrée
            if (d <d1)
            {
                d1 = d;
                p1= foodSources[i].position;
            }
    }
---
puis on normalise le resultat pour retourner sa position a la sortie de la fonction.

a cause des soucis d'appel dans Move(), l'efficacite de cette fonction est mise en doute...

_merci de m'avoir lu !_
