# Mission Control · 50k

Dashboard privé pour piloter la prospection sponsors & mécènes 2027.
URL : `partenaires.enjoylife-emx.fr/50k/`
Mot de passe initial : `enjoylife50k` (à changer · voir plus bas)

---

## Le workflow nous deux

C'est Morgan qui pilote, Claude qui code/push.

1. **Tu m'écris dans la conversation** ce que tu veux faire :
   - *"Ajoute Carrefour Ambérieu, niveau Officiel, contact Jean Dupont, on l'a vu mardi, RDV le 22 mai"*
   - *"Passe Coca en négociation, dis-moi qu'on attend leur retour pour le 15 juin"*
   - *"Mets un refus poli sur Décathlon, ils ont leur partenariat club"*
2. **Je modifie** `data.json`, je commit, je push.
3. **Tu rafraîchis** la page · le dashboard est à jour.

Aucune saisie manuelle dans l'UI · le dashboard est read-only. Ça évite les fausses manips et garantit que le JSON reste cohérent.

---

## Structure de `data.json`

```jsonc
{
  "meta": {
    "objective": 50000,            // objectif total en €
    "phases": { "p1": {...}, "p2": {...} },
    "levels":   [ ... ],           // les 4 niveaux du pitch deck
    "statuses": [ ... ]            // 7 étapes du pipeline
  },
  "prospects": [
    {
      "id": "carrefour-amberieu",  // slug unique, kebab-case
      "name": "Carrefour Ambérieu",
      "address": "12 rue de la République, 01500 Ambérieu",
      "city": "Ambérieu-en-Bugey",
      "website": "https://www.carrefour.fr",
      "contacts": [
        { "name": "Jean Dupont", "role": "Directeur magasin", "email": "j.dupont@…", "phone": "06 12 34 56 78" }
      ],
      "level": "officiel",         // partenaire | officiel | majeur | mecenat
      "amountTarget": 1000,        // si null/0 → utilise le montant du niveau
      "amountSigned": null,        // rempli quand signé
      "status": "rdv",             // a-contacter | contacte | rdv | negociation | accepte | refus | sans-suite
      "phase": "p1",               // p1 ou p2
      "nextAction": "RDV présentation",
      "nextActionDate": "2026-05-22",
      "tags": ["retail", "local", "chaud"],
      "notes": "Texte libre. Sauts de ligne OK.",
      "timeline": [
        { "date": "2026-05-10", "type": "ajout",   "text": "Ajouté au pipeline" },
        { "date": "2026-05-15", "type": "contact", "text": "Premier appel, intéressé pour 1 niveau Officiel" },
        { "date": "2026-05-20", "type": "rdv",     "text": "RDV planifié le 22 mai 14h en magasin" }
      ],
      "createdAt": "2026-05-10",
      "updatedAt": "2026-05-20"
    }
  ]
}
```

---

## Les statuts (ordre du pipeline)

| ID | Label | Quand l'utiliser |
|---|---|---|
| `a-contacter` | À contacter | Identifié, pas encore approché |
| `contacte` | Contacté · attente | Premier contact envoyé, en attente de retour |
| `rdv` | RDV planifié | Rendez-vous fixé |
| `negociation` | En négociation | Discussion engagée, retours attendus sur offre |
| `accepte` | Accepté · signé | Engagement confirmé (`amountSigned` à remplir) |
| `refus` | Refusé | Réponse négative claire |
| `sans-suite` | Sans suite | Ghosté, plus de réponse · à abandonner |

---

## Les phases

- **Phase 1** · 10 mai → 31 août 2026 · *Tarifs préférentiels · closing prioritaire*
- **Phase 2** · 1er sept → 31 décembre 2026 · *Closing final · derniers signataires avant lancement com 2027*

Chaque prospect est rattaché à une phase (`"phase": "p1"` ou `"phase": "p2"`).
Le dashboard affiche les comptes à rebours J−X pour chaque phase.

---

## Changer le mot de passe

Le mot de passe est stocké en hash SHA-256 dans `index.html` (constante `PWD_HASH`).
Pour le changer :

```bash
echo -n "TON_NOUVEAU_PASSWORD" | shasum -a 256 | awk '{print $1}'
```

Coller le hash dans `index.html` :
```js
const PWD_HASH = "le-nouveau-hash-ici";
```

Commit + push, et le nouveau password est actif.

---

## Confidentialité · à savoir

Le repo `partenaires` est **public** sur GitHub.
Le fichier `data.json` est donc **lisible par quiconque trouve le repo**, même si l'URL `/50k/` n'est pas listée sur le site.
Le password de la page n'est qu'un rideau visuel · il ne protège pas le contenu du fichier brut.

**Conséquence concrète** :
- ✅ OK pour : noms d'entreprises, niveaux ciblés, statuts, montants génériques.
- ⚠️ À éviter : numéros de téléphone perso d'un dirigeant, emails personnels (gmail/hotmail), notes franches type *"le DG est un con"*.
- 💡 Si on veut vraiment cacher : prochaine étape = chiffrement AES-GCM du `data.json` (V2). Demander à Claude.

---

## TODO V2 (idées d'évolution si besoin)

- [ ] Chiffrement AES-GCM des données (Web Crypto API)
- [ ] Vue cartographique (Mapbox/Leaflet) avec marqueurs colorés par statut
- [ ] Export PDF d'un rapport "où on en est"
- [ ] Notifications Telegram quand `nextActionDate` arrive
- [ ] Vue calendrier des prochaines actions
- [ ] Stats par niveau (taux conversion par tier)
