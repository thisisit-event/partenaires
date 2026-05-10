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
2. **Je modifie** `data.json`, je commit, je push. Si tu m'as filé une adresse, je géocode et je stocke les coords pour la carte.
3. **Tu rafraîchis** la page · le dashboard est à jour.

Aucune saisie manuelle dans l'UI · le dashboard est read-only. Ça évite les fausses manips et garantit que le JSON reste cohérent.

---

## Les vues disponibles

| Vue | Quand l'utiliser |
|---|---|
| **Kanban** | Vue d'ensemble du pipeline, statut par statut. La vue par défaut du lundi matin. |
| **Tableau** | Quand tu veux tout voir d'un coup, trier, scanner les chiffres. |
| **Carte** | Pour planifier des tournées RDV ou voir où sont concentrées tes boîtes. |
| **Calendrier** | Vue mensuelle des prochaines actions, pour anticiper la charge de la semaine/du mois. |

---

## Le panneau "Cette semaine"

En haut du dashboard. Affiche automatiquement les 12 prochaines actions critiques :
- 🔴 **En retard** · `nextActionDate` passée
- 🟡 **Aujourd'hui** · action prévue pour aujourd'hui
- 🔵 **Sous 7 jours** · action à venir dans la semaine
- 🟡 **À relancer** · prospect en statut `contacté · attente` depuis plus de 14 jours sans `nextAction` définie

Tu cliques sur une ligne, ça t'ouvre la fiche du prospect.

---

## Structure de `data.json`

```jsonc
{
  "meta": {
    "objective": 50000,
    "phases": { "p1": {...}, "p2": {...} },
    "levels":   [ ... ],
    "statuses": [ ... ]
  },
  "prospects": [
    {
      "id": "carrefour-amberieu",
      "name": "Carrefour Ambérieu",
      "address": "12 rue de la République, 01500 Ambérieu",
      "city": "Ambérieu-en-Bugey",
      "coords": [45.9580, 5.3580],     // [lat, lng] · rempli par Claude après géocodage
      "website": "https://www.carrefour.fr",
      "contacts": [
        { "name": "Jean Dupont", "role": "Directeur magasin", "email": "j.dupont@…", "phone": "06 12 34 56 78" }
      ],
      "level": "officiel",
      "amountTarget": 1000,
      "amountSigned": null,
      "status": "rdv",
      "phase": "p1",
      "nextAction": "RDV présentation",
      "nextActionDate": "2026-05-22",
      "tags": ["retail", "local", "chaud"],
      "notes": "Texte libre. Sauts de ligne OK.",
      "timeline": [
        { "date": "2026-05-10", "type": "ajout",   "text": "Ajouté au pipeline" },
        { "date": "2026-05-15", "type": "contact", "text": "Premier appel, intéressé pour Officiel" }
      ],
      "createdAt": "2026-05-10",
      "updatedAt": "2026-05-20"
    }
  ]
}
```

### Champ `coords` (carte)
Optionnel. Format `[lat, lng]` en décimal. Quand tu me files une adresse, je géocode automatiquement via Nominatim (OpenStreetMap, gratuit) et je remplis ce champ. Si une boîte n'a pas de `coords`, elle n'apparaît juste pas sur la carte (les autres vues marchent normalement).

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

---

## Actions rapides (dans la fiche)

Dans le drawer de chaque prospect, 4 boutons :
- **Appeler** · `tel:` du premier contact
- **Mailer** · `mailto:` du premier contact (vide, à toi de rédiger)
- **Itinéraire** · ouvre Google Maps (utilise les coords si dispo, sinon l'adresse)
- **Site** · ouvre le site web

Si une donnée manque, le bouton correspondant est grisé.

---

## Mode tournée (carte)

Sur la vue carte, bouton **Mode tournée** :
1. Tu cliques sur 1 à N markers → ils passent en sélection (halo violet).
2. Bouton **Itinéraire (N)** s'active.
3. Clic → ouvre Google Maps avec les waypoints dans l'ordre de sélection.

Pratique pour préparer une journée RDV sur le 01.

---

## Changer le mot de passe

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
- 💡 Si on veut vraiment cacher : prochaine étape = chiffrement AES-GCM du `data.json` (V2).

---

## TODO V2

- [ ] Templates emails personnalisés (premier contact, relance, après RDV…)
- [ ] Chiffrement AES-GCM des données
- [ ] Export PDF "État du pipeline au [date]"
- [ ] Stats par niveau (taux conversion par tier)
- [ ] Notifications navigateur pour actions du jour
