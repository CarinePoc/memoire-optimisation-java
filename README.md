# Optimisation de performance d'un outil Java existant (MetaDONE)

Mémoire de master en Sciences Informatiques (Software Engineering), Université de Namur, 2025-2026.

## En bref

J'ai analysé et optimisé les performances de **MetaDONE**, un outil de métamodélisation (MetaCASE) en Java, avec peu de documentation préalable de ses points de lenteur.  
Résultat : temps de démarrage ramené de **18 à 1,5 secondes** (scénario 1, chapitre 5.1), et des gains algorithmiques sur la création de métamodèles et d'arcs.

## Ma démarche

Pour chacun des quatre scénarios d'usage, j'ai appliqué le même cycle :

1. **Mesurer** : benchmark du scénario (JFR, JMC, async-profiler).
2. **Analyser** : identifier la cause racine du ralentissement.
3. **Optimiser** : concevoir une amélioration compatible avec l'architecture et le principe de Design by Contract (les préconditions et invariants de l'outil doivent rester respectés).
4. **Valider** : tests d'intégration et nouvelle mesure.

## Résultats principaux

- **Construction de métamodèles** : mise en cache de la vérification d'appartenance, de O(N²) à O(N).
- **Création d'arcs** : correction d'une asymétrie de conception dans `_createRole`, de O(N²) à environ O(N log N), avec un gain médian de 3,5× pour N = 5 000.
- **Deux optimisations rejetées** sur la base des mesures : l'une sans effet sur le backend utilisé, l'autre violant le Design by Contract.

## Contenu du dépôt

- `memoire.pdf` : le mémoire complet. Pour un aperçu rapide, commencer au chapitre 5.1.
- `latex/` : les sources LaTeX pour recompiler le document.


## Technologies

Java, JPA, JFR (Java Flight Recorder), JMC (Java Mission Control), async-profiler, LaTeX.

## Contact

Carine Pochet : linkedin.com/in/carine-pochet-91754533b · carinepochet@icloud.com
