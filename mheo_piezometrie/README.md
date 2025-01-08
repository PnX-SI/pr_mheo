# Personnalisation des libellés pour les concepts GeoNature

- Groupes de sites => « Zone humide »
- Site => « Point »
- Visite => « Mesure »

# Type(s) de géométrie autorisé(s) pour les Sites

Géométrie ponctuelle


# Valeurs par défaut pour les champs de Mesure basés sur des nomenclatures

Certains champs ont une valeur par défaut (c-à-d la valeur pré-sélectionnée dans la liste déroulante) quand une valeur est manifestement celle choisie quasi-systématiquement.

Par exemple le champ `mode_obtention` basé sur la nomenclature `MODE_OBTENTION_MESURE` reçoit par défaut la valeur `1` pour « Valeur mesurée ».


# Correspondance champ protocole `producteur` => concept GeoNature Observers

Le champ du protocole Piézométrie « Code du producteur » (`CdIntervenant`) est mis en correspondance avec  la notion d'observateurs (`observers`) d'une Visite de GeoNature monitorings.

Deux champs spécifiques ont été ajoutés pour les champs gestionnaire et valideur du protocole.

En bref : « libellé mhéo » (`code SANDRE`) : « libellé GeoNature » (`code champ GeoNature`) 

- « Code du producteur » (`CdIntervenant`) : « Producteurs » (`observers`)
- « Code du gestionnaire » (`CdIntervenant2`) : « Gestionnaire » (`gestionnaire`)
- « Code du valideur » (`CdIntervenant3`) : « Valideur » (`valideur`)

Remarque : bien qu'un unique producteur soit attendu par le standard il n'est pas possible en l'état de passer le widget de saisie pour `obervers` en mode choix unique, ça provoque une erreur lors de l'enregistrement de la visite.


# TODO / questions

- il manque une unité sur certains champs, par exemple le champ `hauteur_repère` du niveau Point. Est-ce que la valeur est attendue en mètres ou en centimètres ?
- idem pour champ `valeur_mesure` du niveau Mesure.


# Source de l'image de la vignette du module

Description : Piezzomètre, destiné à surveiller le niveau de la nappe, et éventuellement sa qualité, dans la zone de l'Union, non loin du Canal de Roubaix,

Date : 21 juin 2011

Par Lamiot — Travail personnel, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=15644636
