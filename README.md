**Implémentation des protocoles MhéO pour GeoNature Monitoring** 

Implémentations de cinq protocoles de la boîte à outil MhéO pour le module monitoring de GeoNature. Les fichiers `README.md` donnent quelques informations sur comment ont été traduits les concepts MhéO dans GeoNature. Pour une compréhension du formatage des fichiers se référer à [la documentation technique de gn-monitoring](https://github.com/PnX-SI/gn_module_monitoring/blob/main/README.md) et en particulier à [la configuration des attributs](https://github.com/PnX-SI/gn_module_monitoring/blob/main/docs/sous_module.md#configuration-des-objets).

Ce travail est basé sur [le document de référence de la BàO Rhoméo](https://rhomeo-bao.fr/sites/all/themes/corporateclean/pdf/ZH_Boite-outils-complete.pdf) pour la spécification des protocoles et sur les documents spécifiant les formats d'échange SANDRE pour les champs de chacun des protocoles. 

Contacts :

- Honorine BALDENWECK-RUFFENACH (PatriNat)
- Robin VIGNAUD (PatriNat)

Protocoles implémentés et testés avec **gn-monitoring v1.0.0**

Le reste de ce document donne quelques éléments ayant guidé l'implémentation des protocoles pour gn-monitoring. Les informations concernant spécifiquement un protocole se trouve dans le fichier `README.md` de ce protocole.


# Propriété d'attribut `code_sandre`

La plupart des attributs configurés ont une propriété `code_sandre`. Par exemple :

```json
{
  "attribut_label": "Identifiant SINP",
  "type_widget": "text", 
  "code_sandre": "IdStNP"
}
```

La propriété `code_sandre` fait référence au code du champ dans les documents décrivant le format d'échange pour les protocoles MhéO. Cette propriété est purement indicative et n'a pas d'incidence sur le fonctionnement de gn-monitoring.

# Ordre des attributs spécifiques dans la configuration

L'ordre suivant est généralement respecté pour les définitions des attributs dans les fichiers JSON :

- attributs spécifiques dans l'ordre des champs du format d'échange SANDRE
- attributs génériques renommés
- attributs génériques cachés

# Choix du type de champ pour les listes de valeurs

Pour de nombreux champs les valeurs possibles sont définies par des listes pré-établies par des référentiels. Deux types de champ peuvent proposer des listes de valeurs dans GeoNature : les champs « select » et les champs « nomenclature ». Les deux se présente sous la forme d'une liste déroulante. Voici les critéres qui ont permis de décider quel type utiliser pour chaque champ des protocoles MhéO :

(les deux types de champ permettent de différencier le libellé affiché sur le formulaire et la valeur effective enregistrée en base de données)

## Type de champ « select »

- permet d'ordonner les valeurs présentées dans la liste déroulante
- les libellés et valeurs ne peuvent pas être mutualisés, il faut les saisir pour chaque champ.
- seules les valeurs sont utilisables pour d'éventuels exports

Dans le cadre des protocoles MhéO des champ de type « select » sont utilisés pour :

- les listes spécifiques et/ou courtes : Oui/Non, Faible/Moyen/Important, etc.
- les listes de valeurs devant être présentées ordonnées : par exemple les niveaux de précision des coordonnées.

Concrètement toutes les listes provenant de l'onglet « Référentiels » dans les documents décrivant les formats d'échange ont ce type de champ.

## Type de champ « nomenclature »

- permet d'ajouter une définition à chaque valeur. Sur le formulaire la définition d'une valeur s'affiche au survol de la valeur dans la liste.
- ne permet pas (pas encore ?) d'ordonner les valeurs présentées dans la liste déroulante. L'ordre est alphabétique par rapport aux libellés.
- permet de partager l'ensemble des libellés/valeurs/définitions (c-à-d une nomenclature) entre plusieurs champs.
- toutes les informations sont utilisables pour d'éventuels exports

Dans le cadre des protocoles MhéO des champ de type « nomenclature » sont utilisés pour :

- les listes de valeurs issues d'une nomenclature du SANDRE (par exemple : https://id.eaufrance.fr/nsa/957)
- quand la liste de valeurs correspond à une nomenclature déjà présente par défaut dans GeoNature.

## Cas particulier de la nomenclature pour la précision de la localisation

C'est une nomenclature du SANDRE (avec descriptions de chaque valeur) dont les valeurs sont manifestement ordonnées (ce que ne permet pas encore le type de champ `nomenclature`) : le code de chaque valeur a été ajouté devant son libellé pour que l'ordre d'affichage soit respecté (par exemple « 16 - Précision décamétrique supérieure à 50 mètres »).
