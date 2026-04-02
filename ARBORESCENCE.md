# ARBORESCENCE COMPLÈTE — THIS IS IT EVENT · 2027
# Document de référence pour la construction des dossiers
# Créé le : 02/04/2026

projet/
│
├── index.html                          ← Fichier principal du site (remplace l'ancien)
│
├── images/
│   └── test.png                        ← Logo actuel (conservé tel quel)
│
└── assets/
    │
    ├── images/
    │   │
    │   ├── hero/
    │   │   └── hero-salle-comble.jpg           ← Photo salle comble (la plus large, la plus impressionnante)
    │   │                                          Format : paysage · min 1920x1080px · JPG
    │   │
    │   ├── events/
    │   │   ├── enjoylife-salle-pleine.jpg       ← Vue large salle comble (Section 02)
    │   │   ├── enjoylife-balcon-vip.jpg          ← Balcon VIP avec invités (Section 06)
    │   │   ├── enjoylife-ecran-geant.jpg         ← Écran géant avec logo partenaire visible (Section 03 + 04)
    │   │   ├── enjoylife-photocall.jpg           ← Zone photocall (Section 04 + 06)
    │   │   ├── enjoylife-pancartes-vote.jpg      ← Pancartes dans les mains du public (Section 04 + 06)
    │   │   ├── enjoylife-scene-ambiance.jpg      ← Ambiance générale scène (poster vidéo Section 06)
    │   │   ├── enjoylife-bénévoles-tshirts.jpg   ← Bénévoles en T-shirts logotés (Section 05 — optionnel)
    │   │   └── enjoylife-affichage-flyers.jpg    ← Affichage / flyers en situation (Section 05 — optionnel)
    │   │
    │   ├── logos-events/
    │   │   ├── logo-enjoylife.png               ← Logo Enjoylife (Section 02 — carte Enjoylife)
    │   │   └── logo-nuit-amateurs.png           ← Logo La Nuit des Amateurs (Section 02 — carte LNDA)
    │   │
    │   ├── team/
    │   │   └── team-morgan-laurie.jpg           ← Photo Morgan Spirli + Laurie Daussy (La Cotière · Fév 2026)
    │   │                                          = IMG_1213.PNG de tes archives
    │   │
    │   └── presse/
    │       ├── presse-leprogres-oct2025.jpg     ← Article Le Progrès Octobre 2025
    │       │                                      = leprogres_octobre2025.jpg de tes archives
    │       ├── presse-lacotiere-fev2026.jpg     ← Article La Cotière 12 Février 2026
    │       │                                      = IMG_1213.PNG de tes archives (la page article, pas la photo équipe)
    │       └── presse-lavoixdelain-fev2026.jpg  ← Article La Voix de l'Ain 13 Février 2026
    │                                              = IMG_1425.JPG de tes archives
    │
    ├── logos/
    │   │
    │   ├── majeur/                             ← Logos en PNG fond transparent · version MONOCHROME
    │   │   ├── logo-credit-agricole.png
    │   │   ├── logo-mcdonalds.png
    │   │   └── logo-cer-francine.png
    │   │
    │   ├── officiel/                           ← Logos en PNG fond transparent · version MONOCHROME
    │   │   ├── logo-marinelli.png
    │   │   ├── logo-pixelchrom.png
    │   │   ├── logo-rituel-sport.png
    │   │   ├── logo-aux-delicatesses.png
    │   │   ├── logo-siligreen.png
    │   │   └── logo-night-animation.png
    │   │
    │   ├── partenaire/                         ← Logos en PNG fond transparent · version MONOCHROME
    │   │   ├── logo-marie-bachere.png
    │   │   ├── logo-but-amberieu.png
    │   │   ├── logo-safti.png
    │   │   ├── logo-ronzat.png
    │   │   ├── logo-girel.png
    │   │   ├── logo-atol.png
    │   │   └── logo-sttp.png
    │   │
    │   ├── mecene-institution/                 ← Logos en PNG fond transparent · version MONOCHROME
    │   │   ├── logo-nowbrains.png
    │   │   ├── logo-mairie-vlm.png
    │   │   └── logo-ccpa.png
    │   │
    │   ├── technique/                          ← Logos en PNG fond transparent · version MONOCHROME
    │   │   ├── logo-neon-live.png
    │   │   ├── logo-svprod.png
    │   │   └── logo-dmc-animations.png
    │   │
    │   └── media/                             ← Logos en PNG fond transparent · version MONOCHROME
    │       ├── logo-nrj.png
    │       ├── logo-beb-media.png
    │       ├── logo-lacotiere.png
    │       ├── logo-cinema-horloge.png
    │       ├── logo-cine-festival.png
    │       └── logo-voix-ain.png
    │
    ├── videos/
    │   ├── hero-ambiance-loop.webm             ← Vidéo fond hero · muette · boucle · 10-30 sec max
    │   ├── hero-ambiance-loop.mp4              ← Même vidéo en MP4 (fallback Safari/iOS)
    │   ├── enjoylife-recap-highlights.webm     ← Vidéo highlights à regarder · avec son · 1-3 min
    │   └── enjoylife-recap-highlights.mp4      ← Même vidéo en MP4
    │
    └── data/
        └── partenaires.xlsx                    ← Fichier Excel fiches partenaires
                                                   (utilisé pour compléter les popups de la Section 07)


═══════════════════════════════════════════════════════════════════════
FICHIER EXCEL PARTENAIRES — partenaires.xlsx
Structure des colonnes attendues :
═══════════════════════════════════════════════════════════════════════

Colonne A : id                    ← identifiant technique (ex: credit-agricole)
Colonne B : nom                   ← Nom complet de l'entreprise
Colonne C : categorie             ← majeur / officiel / partenaire / mecene / technique / media
Colonne D : type_activite         ← Description courte du secteur (ex: Banque & Services financiers)
Colonne E : description           ← Texte libre de présentation (2-4 phrases)
Colonne F : email                 ← Email de contact (optionnel)
Colonne G : telephone             ← Téléphone (optionnel)
Colonne H : site_web              ← URL sans http (ex: www.example.fr)
Colonne I : adresse               ← Adresse physique (optionnel)
Colonne J : contact_nom           ← Nom du contact principal (optionnel)


═══════════════════════════════════════════════════════════════════════
RÈGLES DE NOMMAGE
═══════════════════════════════════════════════════════════════════════

LOGOS :
• Format : PNG avec fond transparent
• Version : monochrome (noir ou blanc selon le fond)
• Taille : 300x150px minimum · fond transparent
• Nommage : tout-en-minuscules · tirets · pas d'espaces · pas d'accents
  Exemple : logo-credit-agricole.png ✓ | Logo Crédit Agricole.PNG ✗

IMAGES PHOTOS :
• Format : JPG
• Résolution : 1920x1080px minimum pour les grandes images
• Résolution : 800x600px minimum pour les petites images
• Nommage : contexte-description.jpg
  Exemple : enjoylife-salle-pleine.jpg ✓ | IMG_5432.JPG ✗

VIDÉOS :
• TOUJOURS fournir les 2 formats : .webm + .mp4
• Le .webm est prioritaire (plus léger, Chrome/Firefox)
• Le .mp4 est le fallback (Safari, iOS)
• Nommage : contexte-description.webm / .mp4

IMAGES D'ARTICLES DE PRESSE :
• Photographier ou scanner l'article entier
• Orientation : portrait
• Résolution : 1200px minimum de hauteur


═══════════════════════════════════════════════════════════════════════
NOTES IMPORTANTES
═══════════════════════════════════════════════════════════════════════

1. Si un fichier image est manquant, le site affiche un fallback texte automatiquement.
   Aucune erreur visible — tu peux ajouter les fichiers progressivement.

2. Les vidéos sont optionnelles. Si absentes, l'image hero-salle-comble.jpg s'affiche.
   Pour la section 06, le lecteur vidéo n'apparaît que si le fichier existe.

3. Les popups partenaires (Section 07) contiennent des données pré-remplies dans le code.
   Pour les compléter (email, téléphone, site web) : modifier directement dans index.html
   la variable partnerData au bas du fichier, ou utiliser le fichier Excel comme référence.

4. Le bouton "Télécharger en PDF" utilise l'impression native du navigateur.
   Pour un meilleur rendu PDF : Chrome > Imprimer > Enregistrer en PDF > Format A4 Paysage.
