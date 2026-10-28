# Coût des requêtes OpenAI déclenchées par les tests — 28 octobre 2026

## Demande et résultat

Yanis demande le coût en dollars des requêtes OpenAI réalisées par toutes les campagnes de tests, avec un détail par test. Les consommations de l’agent Codex qui prépare, corrige ou documente les tests sont exclues.

**Montant enregistré par OpenCode : 11,275955745 USD, soit 11,28 $.** Il couvre les **23 campagnes et essais retrouvés**, du 27 au 28 octobre 2026, avec les reprises rattachées aux mêmes projets de test. La collecte contient **1 014 messages de réponse OpenAI**, dont une tentative avec des compteurs nuls après un dépassement de contexte.

**Recalcul aux tarifs officiels consultés le 28 octobre : 11,089087385 USD, soit 11,09 $.** L’écart de 0,186868360 USD est expliqué plus bas. Les deux colonnes sont conservées dans chaque tableau.

Ces montants sont reconstitués à partir des compteurs de jetons et des estimations stockées, hors taxes et remises éventuelles. La facture OpenAI n’a pas été consultée pour confirmer le débit final.

## Répartition utile

| Périmètre | Réponses | Coût enregistré USD | Recalcul actuel USD |
| --- | --- | --- | --- |
| Anciens scénarios de refonte retirés | 580 | 9,427994 | 9,241126 |
| Campagne finale des 29 scénarios réussis | 101 | 1,362543 | 1,362543 |
| Nouveau test 01 du contrôleur de lab | 2 | 0,035528 | 0,035528 |
| Autres campagnes et contrôles techniques | 331 | 0,449890 | 0,449890 |
| **Total** | 1014 | 11,275955745 | 11,089087385 |

Les anciens cas retirés représentent **83,61 %** du coût enregistré. Leur consommation passée est comptée ; leurs scénarios restent retirés de la suite active.

## Méthode et rattachement des reprises

La collecte associe le projet du scénario à ses traitements, puis aux sessions OpenCode et à leurs réponses. Elle lit chaque réponse une seule fois ; les totaux des sessions ne sont pas ajoutés une seconde fois. Les deux collectes indiquent une authentification par clé API.

Les 22 rapports de l’ancien staging regroupent 1 012 réponses ; le nouvel essai ajoute deux réponses. Toutes les réponses historiques sont rattachées à un seul scénario et à un seul rapport.

**Le rattachement est fait au projet du test, pas seulement à la fenêtre horaire du rapport.** Certaines tentatives ont continué ou ont été reprises après que le scénario avait déclaré un échec ou un blocage. La collecte retrouve **374 réponses commencées après la fin enregistrée de leur scénario** : elles sont incluses dans son coût historique. Cela explique pourquoi un test interrompu peut coûter davantage qu’un test finalement réussi ; il ne s’agit pas de 374 scénarios supplémentaires.

Les compilations et les vérifications hors ligne utilisent des remplaçants déclarés des tests unitaires : aucune consommation OpenAI n’est ajoutée pour ces vérifications. La préparation de ce document et la création initiale des pièces jointes par l’agent Codex restent hors périmètre.

## Les 23 campagnes et essais

Dates en heure de Paris. Les numéros ci-dessous servent à lire ce compte rendu ; les références techniques exactes restent dans les preuves d’origine. Les montants incluent les reprises sur les projets concernés.

| Campagne | Début à Paris | Réponses | Enregistré USD | Recalcul USD | Statut du rapport |
| --- | --- | --- | --- | --- | --- |
| Campagne 01 | 27/10 07:35:56 | 89 | 0,117731 | 0,117731 | Incomplète ou en échec |
| Campagne 02 | 27/10 16:17:22 | 3 | 0,004779 | 0,004779 | Assertions réussies, revue visuelle distincte |
| Campagne 03 | 27/10 16:22:51 | 37 | 0,056088 | 0,056088 | Preuve de version commune invalidée |
| Campagne 04 | 27/10 17:28:13 | 2 | 0,002104 | 0,002104 | Incomplète ou en échec |
| Campagne 05 | 27/10 17:59:54 | 3 | 0,008817 | 0,008817 | Incomplète ou en échec |
| Campagne 06 | 27/10 18:38:02 | 1 | 0,000116 | 0,000116 | Incomplète ou en échec |
| Campagne 07 | 27/10 18:39:58 | 7 | 0,004692 | 0,004692 | Incomplète ou en échec |
| Campagne 08 | 27/10 18:43:08 | 7 | 0,003806 | 0,003806 | Incomplète ou en échec |
| Campagne 09 | 27/10 18:47:48 | 11 | 0,019896 | 0,019896 | Preuve de version commune invalidée |
| Campagne 10 | 27/10 18:54:45 | 55 | 0,079342 | 0,079342 | Preuve de version commune invalidée |
| Campagne 11 | 27/10 19:37:12 | 2 | 0,004664 | 0,004664 | Preuve de version commune invalidée |
| Campagne 12 | 27/10 19:39:48 | 99 | 0,279703 | 0,260567 | Incomplète ou en échec |
| Campagne 13 | 27/10 20:42:06 | 34 | 0,483129 | 0,465474 | Preuve de version commune invalidée |
| Campagne 14 | 27/10 21:28:47 | 13 | 0,016169 | 0,016169 | Preuve de version commune invalidée |
| Campagne 15 | 27/10 21:33:19 | 17 | 0,026708 | 0,026708 | Incomplète ou en échec |
| Campagne 16 | 27/10 21:59:47 | 8 | 0,128268 | 0,101802 | Incomplète ou en échec |
| Campagne 17 | 27/10 22:19:39 | 88 | 4,101901 | 3,978291 | Preuve de version commune invalidée |
| Campagne 18 | 28/10 00:41:19 | 102 | 0,947111 | 0,947111 | Incomplète ou en échec |
| Campagne 19 | 28/10 02:01:05 | 26 | 0,140580 | 0,140580 | Incomplète ou en échec |
| Campagne 20 | 28/10 02:43:08 | 92 | 0,905176 | 0,905176 | Incomplète ou en échec |
| Campagne 21 | 28/10 03:51:47 | 215 | 2,547104 | 2,547104 | Preuve de version commune invalidée |
| Campagne 22 | 28/10 11:16:38 | 101 | 1,362543 | 1,362543 | Assertions réussies, revue visuelle distincte |
| Campagne 23 | 28/10 15:35:25 | 2 | 0,035528 | 0,035528 | Assertions réussies, revue visuelle distincte |

## Chaque test, toutes campagnes cumulées

Campagnes compte ici celles où une réponse a été retrouvée pour ce cas. La dernière colonne isole la campagne finale des 29 scénarios. Le nouvel essai 01 est inclus dans le cumul général et apparaît aussi dans le tableau précédent.

| Cas | Objet | Campagnes | Réponses | Cumul enregistré USD | Recalcul actuel USD | Campagne 29/29 USD |
| --- | --- | --- | --- | --- | --- | --- |
| 01 | Brief complet — poterie | 8 | 16 | 0,091458 | 0,091458 | 0,033904 |
| 02 | Restaurant sans réservation automatique | 6 | 11 | 0,043698 | 0,043698 | 0,030961 |
| 03 | Portfolio bilingue | 6 | 12 | 0,073127 | 0,073127 | 0,045391 |
| 04 | Association | 6 | 12 | 0,053053 | 0,053053 | 0,033187 |
| 05 | Portfolio sans références inventées | 6 | 12 | 0,052270 | 0,052270 | 0,033571 |
| 06 | Blog et article fourni | 6 | 14 | 0,060415 | 0,060415 | 0,032391 |
| 07 | Demande vague précisée | 5 | 25 | 0,111216 | 0,111216 | 0,091610 |
| 08 | Textes fournis progressivement | 5 | 22 | 0,093624 | 0,093624 | 0,072940 |
| 09 | Tarif contradictoire arbitré | 5 | 16 | 0,061948 | 0,061948 | 0,042005 |
| 10 | Changement de périmètre | 5 | 15 | 0,056751 | 0,056751 | 0,038420 |
| 11 | Langage familier et fautes | 5 | 15 | 0,049388 | 0,049388 | 0,034088 |
| 12 | Passage au français | 5 | 15 | 0,056813 | 0,056813 | 0,039936 |
| 13 | Liberté créative encadrée | 5 | 20 | 0,133277 | 0,133277 | 0,091216 |
| 14 | Projet vague : clôture | 4 | 13 | 0,009944 | 0,009944 | 0,007923 |
| 15 | Exigences incompatibles : clôture | 4 | 13 | 0,010980 | 0,010980 | 0,008762 |
| 16 | Hors sujet : clôture | 4 | 13 | 0,009893 | 0,009893 | 0,007990 |
| 17 | Fonction impossible : clôture | 4 | 10 | 0,007185 | 0,007185 | 0,005572 |
| 18 | Abandon explicite | 4 | 8 | 0,006725 | 0,006725 | 0,004977 |
| 19 | Photographie jointe | 4 | 18 | 0,068714 | 0,068714 | 0,051740 |
| 20 | Illustration jointe | 3 | 14 | 0,053358 | 0,053358 | 0,042596 |
| 21 | PDF principal et exemple | 3 | 13 | 0,129828 | 0,129828 | 0,114242 |
| 22 | PDF périmé et correction | 3 | 18 | 0,094286 | 0,094286 | 0,081132 |
| 23 | Catalogue Excel | 6 | 13 | 0,046664 | 0,046664 | 0,036795 |
| 24 | Programme Excel et formules | 6 | 13 | 0,050721 | 0,050721 | 0,041099 |
| 25 | Excel ambigu, gratuit et vide | 6 | 17 | 0,049970 | 0,049970 | 0,039870 |
| 26 | PDF, image et Excel | 6 | 22 | 0,144531 | 0,144531 | 0,111955 |
| 27 | Instruction parasite dans une source | 3 | 13 | 0,059694 | 0,059694 | 0,051161 |
| 28 | Ancienne refonte complète — cas retiré | 11 | 574 | 9,421836 | 9,234968 | — |
| 29 | Ancienne refonte progressive — cas retiré | 0 | 0 | 0,000000 | 0,000000 | — |
| 30 | Ancien contrôle des droits — cas retiré | 1 | 3 | 0,000705 | 0,000705 | — |
| 31 | Retouche et ancienne version | 2 | 8 | 0,100795 | 0,100795 | 0,087433 |
| 32 | Livraison WordPress | 3 | 8 | 0,059021 | 0,059021 | 0,049674 |
| 33 | Ancienne refonte par PDF — cas retiré | 1 | 3 | 0,005453 | 0,005453 | — |
| Contrôle de source | Contrôle technique de lecture de source | 3 | 15 | 0,008614 | 0,008614 | — |

Le cas 29 a été bloqué avant création du projet parce que ses sources n’étaient pas configurées, puis est resté non exécuté. Aucune consommation OpenAI n’est retrouvée pour ce cas.

## Jetons et tarifs

Un jeton est une unité de texte ou de contenu traitée par le modèle. Les entrées ordinaires, les lectures en cache et les écritures en cache ont des prix distincts. Le raisonnement est facturé comme de la sortie et est compté une seule fois.

| Modèle | Entrée / million | Cache lu / million | Cache écrit 30 min / million | Sortie / million |
| --- | --- | --- | --- | --- |
| GPT-6 Luna | 0,10 $ | 0,01 $ | 0,125 $ | 0,50 $ |
| GPT-6.1 Terra | 1,00 $ | 0,05 $ | 1,25 $ | 5,00 $ |

Sources officielles : [GPT-6 Luna](https://developers.openai.com/api/docs/models/gpt-6-luna), [GPT-6.1 Terra](https://developers.openai.com/api/docs/models/gpt-6.1-terra), [cache des entrées](https://developers.openai.com/api/docs/guides/prompt-caching) et [raisonnement](https://developers.openai.com/api/docs/guides/reasoning). Tarifs consultés le 28 octobre 2026 : traitement Standard, sans supplément régional dans ce recalcul.

La formule par réponse additionne les coûts des entrées ordinaires, du cache lu, du cache écrit et des sorties visibles plus le raisonnement, chaque volume étant divisé par un million. Pour les requêtes longues, les coefficients correspondants s’appliquent à toute la requête.

### Pourquoi les deux totaux diffèrent

La documentation officielle consultée fixe le seuil de contexte long à **272 000 jetons d’entrée**, avec un doublement des prix d’entrée et de cache et un coefficient de 1,5 pour la sortie. L’estimation stockée par l’ancienne version d’OpenCode correspond exactement au même calcul avec un seuil de **200 000 jetons**.

**Onze réponses Luna se situent entre ces seuils**, ce qui explique les **0,186868360 USD** d’écart. Les autres réponses coïncident à la précision contrôlée. Les 29 scénarios Terra et le nouvel essai 01 ont le même coût selon les deux calculs. La facture du compte serait nécessaire pour confirmer le montant effectivement débité.

### Volumes par modèle

| Modèle | Réponses | Entrée totale | Cache lu | Cache écrit | Sortie visible | Raisonnement | Enregistré USD | Recalcul USD |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| gpt-6-luna | 911 | 55369177 | 7608900 | 47708536 | 921807 | 435600 | 9,877884245 | 9,691015885 |
| gpt-6.1-terra | 103 | 413395 | 0 | 413086 | 164374 | 11907 | 1,398071500 | 1,398071500 |

### Coût par opération du produit

Ces sous-totaux sont inclus dans le total OpenAI ; ils ne représentent pas des factures supplémentaires.

| Opération | Réponses | Enregistré USD | Recalcul USD |
| --- | --- | --- | --- |
| Analyse, questions et lecture des sources | 680 | 7,595656 | 7,408787 |
| Construction et retouche des maquettes | 328 | 3,427872 | 3,427872 |
| Préparation de la livraison | 6 | 0,252428 | 0,252428 |

## Détail par campagne et par test

Les lignes incluent les cas effectivement lancés ou bloqués. Ceux simplement marqués non exécutés ne sont pas répétés. Une ligne à zéro indique l’absence de consommation retrouvée pour ce cas ; elle ne transforme pas un blocage en réussite. Les statuts bruts sont conservés : FAIL signifie échec, BLOCKED blocage, INVALIDATED résultat invalidé, et AUTOMATED_PASS assertions réussies.

| Campagne | Cas | Statut | Réponses | Entrée | Sortie avec raisonnement | Enregistré USD | Recalcul USD |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Campagne 01 | 01 | FAIL | 2 | 2393 | 7023 | 0,003792 | 0,003792 |
| Campagne 01 | 02 | FAIL | 2 | 2252 | 5466 | 0,002996 | 0,002996 |
| Campagne 01 | 03 | AUTOMATED_PASS | 2 | 2403 | 14604 | 0,007584 | 0,007584 |
| Campagne 01 | 04 | AUTOMATED_PASS | 2 | 2228 | 6477 | 0,003499 | 0,003499 |
| Campagne 01 | 05 | AUTOMATED_PASS | 2 | 2217 | 6981 | 0,003750 | 0,003750 |
| Campagne 01 | 06 | AUTOMATED_PASS | 3 | 10570 | 13664 | 0,008135 | 0,008135 |
| Campagne 01 | 07 | FAIL | 3 | 2751 | 6809 | 0,003716 | 0,003716 |
| Campagne 01 | 08 | AUTOMATED_PASS | 5 | 16032 | 13914 | 0,008928 | 0,008928 |
| Campagne 01 | 09 | AUTOMATED_PASS | 3 | 3401 | 8580 | 0,004673 | 0,004673 |
| Campagne 01 | 10 | AUTOMATED_PASS | 3 | 3282 | 7571 | 0,004159 | 0,004159 |
| Campagne 01 | 11 | AUTOMATED_PASS | 3 | 2969 | 5478 | 0,003076 | 0,003076 |
| Campagne 01 | 12 | AUTOMATED_PASS | 3 | 3218 | 6817 | 0,003774 | 0,003774 |
| Campagne 01 | 13 | AUTOMATED_PASS | 4 | 15415 | 13740 | 0,008777 | 0,008777 |
| Campagne 01 | 14 | FAIL | 4 | 2925 | 730 | 0,000658 | 0,000658 |
| Campagne 01 | 15 | FAIL | 4 | 3036 | 808 | 0,000708 | 0,000708 |
| Campagne 01 | 16 | FAIL | 4 | 2917 | 478 | 0,000531 | 0,000531 |
| Campagne 01 | 17 | FAIL | 4 | 3091 | 853 | 0,000736 | 0,000736 |
| Campagne 01 | 18 | FAIL | 3 | 2103 | 1651 | 0,001036 | 0,001036 |
| Campagne 01 | 19 | AUTOMATED_PASS | 3 | 7445 | 6128 | 0,003980 | 0,003980 |
| Campagne 01 | 20 | FAIL | 4 | 14979 | 9218 | 0,006466 | 0,006466 |
| Campagne 01 | 21 | FAIL | 3 | 4423 | 7289 | 0,004183 | 0,004183 |
| Campagne 01 | 22 | AUTOMATED_PASS | 4 | 4787 | 9511 | 0,005317 | 0,005317 |
| Campagne 01 | 23 | FAIL | 1 | 583 | 181 | 0,000149 | 0,000149 |
| Campagne 01 | 24 | FAIL | 1 | 589 | 84 | 0,000101 | 0,000101 |
| Campagne 01 | 25 | FAIL | 1 | 590 | 85 | 0,000102 | 0,000102 |
| Campagne 01 | 26 | FAIL | 1 | 589 | 71 | 0,000094 | 0,000094 |
| Campagne 01 | 27 | AUTOMATED_PASS | 3 | 3310 | 4702 | 0,002726 | 0,002726 |
| Campagne 01 | 28 | BLOCKED | 0 | 0 | 0 | 0,000000 | 0,000000 |
| Campagne 01 | 29 | BLOCKED | 0 | 0 | 0 | 0,000000 | 0,000000 |
| Campagne 01 | 30 | FAIL | 3 | 2156 | 978 | 0,000705 | 0,000705 |
| Campagne 01 | 31 | FAIL | 4 | 27592 | 19864 | 0,013362 | 0,013362 |
| Campagne 01 | 32 | FAIL | 2 | 2610 | 8525 | 0,004569 | 0,004569 |
| Campagne 01 | 33 | AUTOMATED_PASS | 3 | 5333 | 9603 | 0,005453 | 0,005453 |
| Campagne 02 | 32 | AUTOMATED_PASS | 3 | 10486 | 6936 | 0,004779 | 0,004779 |
| Campagne 03 | 01 | INVALIDATED | 2 | 2778 | 6664 | 0,003679 | 0,003679 |
| Campagne 03 | 02 | INVALIDATED | 2 | 2697 | 5447 | 0,003060 | 0,003060 |
| Campagne 03 | 03 | INVALIDATED | 2 | 2725 | 6392 | 0,003536 | 0,003536 |
| Campagne 03 | 04 | INVALIDATED | 2 | 2609 | 5894 | 0,003273 | 0,003273 |
| Campagne 03 | 05 | INVALIDATED | 2 | 2622 | 7626 | 0,004141 | 0,004141 |
| Campagne 03 | 06 | INVALIDATED | 2 | 2685 | 6523 | 0,003597 | 0,003597 |
| Campagne 03 | 07 | INVALIDATED | 5 | 6567 | 7061 | 0,004328 | 0,004328 |
| Campagne 03 | 08 | INVALIDATED | 4 | 5091 | 6004 | 0,003615 | 0,003615 |
| Campagne 03 | 09 | INVALIDATED | 3 | 4167 | 5841 | 0,003441 | 0,003441 |
| Campagne 03 | 10 | INVALIDATED | 3 | 4033 | 7890 | 0,004426 | 0,004426 |
| Campagne 03 | 11 | INVALIDATED | 3 | 3721 | 8315 | 0,004599 | 0,004599 |
| Campagne 03 | 12 | INVALIDATED | 3 | 3967 | 7578 | 0,004262 | 0,004262 |
| Campagne 03 | 13 | BLOCKED | 4 | 18373 | 15668 | 0,010130 | 0,010130 |
| Campagne 04 | 28 | BLOCKED | 2 | 15460 | 390 | 0,002104 | 0,002104 |
| Campagne 05 | 28 | BLOCKED | 3 | 58944 | 2946 | 0,008817 | 0,008817 |
| Campagne 06 | Contrôle de source | BLOCKED | 1 | 686 | 95 | 0,000116 | 0,000116 |
| Campagne 07 | Contrôle de source | BLOCKED | 7 | 17127 | 5171 | 0,004692 | 0,004692 |
| Campagne 08 | Contrôle de source | FAIL | 7 | 16036 | 3674 | 0,003806 | 0,003806 |
| Campagne 09 | 01 | INVALIDATED | 2 | 2808 | 5613 | 0,003157 | 0,003157 |
| Campagne 09 | 02 | FAIL | 1 | 1093 | 556 | 0,000415 | 0,000415 |
| Campagne 09 | 03 | FAIL | 2 | 2836 | 9029 | 0,004869 | 0,004869 |
| Campagne 09 | 04 | INVALIDATED | 2 | 2763 | 4910 | 0,002800 | 0,002800 |
| Campagne 09 | 05 | INVALIDATED | 2 | 2742 | 7654 | 0,004170 | 0,004170 |
| Campagne 09 | 06 | BLOCKED | 2 | 2793 | 8272 | 0,004485 | 0,004485 |
| Campagne 10 | 01 | INVALIDATED | 2 | 3079 | 6291 | 0,003530 | 0,003530 |
| Campagne 10 | 02 | INVALIDATED | 2 | 2993 | 6171 | 0,003459 | 0,003459 |
| Campagne 10 | 03 | INVALIDATED | 2 | 2970 | 15060 | 0,007901 | 0,007901 |
| Campagne 10 | 04 | INVALIDATED | 2 | 2996 | 12121 | 0,006435 | 0,006435 |
| Campagne 10 | 05 | INVALIDATED | 2 | 2936 | 4735 | 0,002734 | 0,002734 |
| Campagne 10 | 06 | INVALIDATED | 2 | 2978 | 7232 | 0,003988 | 0,003988 |
| Campagne 10 | 07 | INVALIDATED | 5 | 7180 | 7272 | 0,004533 | 0,004533 |
| Campagne 10 | 08 | INVALIDATED | 4 | 5735 | 7278 | 0,004356 | 0,004356 |
| Campagne 10 | 09 | INVALIDATED | 4 | 18114 | 10948 | 0,007738 | 0,007738 |
| Campagne 10 | 10 | INVALIDATED | 3 | 4492 | 8895 | 0,005009 | 0,005009 |
| Campagne 10 | 11 | INVALIDATED | 3 | 4136 | 7228 | 0,004131 | 0,004131 |
| Campagne 10 | 12 | INVALIDATED | 3 | 4481 | 8614 | 0,004867 | 0,004867 |
| Campagne 10 | 13 | INVALIDATED | 4 | 21371 | 18798 | 0,012070 | 0,012070 |
| Campagne 10 | 14 | INVALIDATED | 3 | 3514 | 508 | 0,000693 | 0,000693 |
| Campagne 10 | 15 | INVALIDATED | 3 | 3588 | 579 | 0,000738 | 0,000738 |
| Campagne 10 | 16 | INVALIDATED | 3 | 3527 | 449 | 0,000665 | 0,000665 |
| Campagne 10 | 17 | INVALIDATED | 2 | 2259 | 305 | 0,000435 | 0,000435 |
| Campagne 10 | 18 | INVALIDATED | 1 | 1065 | 313 | 0,000290 | 0,000290 |
| Campagne 10 | 19 | BLOCKED | 5 | 19883 | 6572 | 0,005771 | 0,005771 |
| Campagne 11 | 01 | BLOCKED | 2 | 3043 | 8568 | 0,004664 | 0,004664 |
| Campagne 12 | 01 | AUTOMATED_PASS | 2 | 3060 | 5643 | 0,003204 | 0,003204 |
| Campagne 12 | 02 | AUTOMATED_PASS | 2 | 3097 | 4839 | 0,002806 | 0,002806 |
| Campagne 12 | 03 | AUTOMATED_PASS | 2 | 3016 | 6937 | 0,003845 | 0,003845 |
| Campagne 12 | 04 | AUTOMATED_PASS | 2 | 2967 | 6976 | 0,003859 | 0,003859 |
| Campagne 12 | 05 | AUTOMATED_PASS | 2 | 2944 | 7074 | 0,003905 | 0,003905 |
| Campagne 12 | 06 | AUTOMATED_PASS | 3 | 16730 | 11457 | 0,007820 | 0,007820 |
| Campagne 12 | 07 | AUTOMATED_PASS | 6 | 15980 | 10063 | 0,007029 | 0,007029 |
| Campagne 12 | 08 | AUTOMATED_PASS | 4 | 5628 | 6164 | 0,003785 | 0,003785 |
| Campagne 12 | 09 | AUTOMATED_PASS | 3 | 4649 | 7019 | 0,004090 | 0,004090 |
| Campagne 12 | 10 | AUTOMATED_PASS | 3 | 4481 | 8355 | 0,004737 | 0,004737 |
| Campagne 12 | 11 | AUTOMATED_PASS | 3 | 4224 | 5934 | 0,003495 | 0,003495 |
| Campagne 12 | 12 | AUTOMATED_PASS | 3 | 4478 | 6828 | 0,003974 | 0,003974 |
| Campagne 12 | 13 | AUTOMATED_PASS | 4 | 20501 | 17042 | 0,011083 | 0,011083 |
| Campagne 12 | 14 | AUTOMATED_PASS | 3 | 3429 | 485 | 0,000671 | 0,000671 |
| Campagne 12 | 15 | AUTOMATED_PASS | 3 | 3619 | 641 | 0,000773 | 0,000773 |
| Campagne 12 | 16 | AUTOMATED_PASS | 3 | 3527 | 533 | 0,000707 | 0,000707 |
| Campagne 12 | 17 | AUTOMATED_PASS | 2 | 2254 | 322 | 0,000443 | 0,000443 |
| Campagne 12 | 18 | AUTOMATED_PASS | 2 | 2273 | 276 | 0,000422 | 0,000422 |
| Campagne 12 | 19 | AUTOMATED_PASS | 5 | 19941 | 9462 | 0,007223 | 0,007223 |
| Campagne 12 | 20 | AUTOMATED_PASS | 5 | 18871 | 3874 | 0,004296 | 0,004296 |
| Campagne 12 | 21 | AUTOMATED_PASS | 5 | 62084 | 7285 | 0,011403 | 0,011403 |
| Campagne 12 | 22 | AUTOMATED_PASS | 7 | 38139 | 6140 | 0,007837 | 0,007837 |
| Campagne 12 | 23 | FAIL | 1 | 1065 | 88 | 0,000177 | 0,000177 |
| Campagne 12 | 24 | FAIL | 1 | 1067 | 117 | 0,000192 | 0,000192 |
| Campagne 12 | 25 | FAIL | 1 | 1068 | 185 | 0,000226 | 0,000226 |
| Campagne 12 | 26 | FAIL | 1 | 1061 | 137 | 0,000201 | 0,000201 |
| Campagne 12 | 27 | AUTOMATED_PASS | 5 | 24800 | 5414 | 0,005807 | 0,005807 |
| Campagne 12 | 28 | BLOCKED | 16 | 3550622 | 30415 | 0,175695 | 0,156559 |
| Campagne 13 | 23 | INVALIDATED | 3 | 6272 | 6965 | 0,004266 | 0,004266 |
| Campagne 13 | 24 | INVALIDATED | 3 | 6127 | 6227 | 0,003879 | 0,003879 |
| Campagne 13 | 25 | FAIL | 3 | 4986 | 1467 | 0,001357 | 0,001357 |
| Campagne 13 | 26 | INVALIDATED | 5 | 61875 | 5843 | 0,010656 | 0,010656 |
| Campagne 13 | 28 | BLOCKED | 20 | 6036503 | 35779 | 0,462972 | 0,445316 |
| Campagne 14 | 25 | INVALIDATED | 4 | 7986 | 5663 | 0,003829 | 0,003829 |
| Campagne 14 | 23 | FAIL | 2 | 3571 | 671 | 0,000782 | 0,000782 |
| Campagne 14 | 24 | FAIL | 2 | 3480 | 345 | 0,000607 | 0,000607 |
| Campagne 14 | 26 | BLOCKED | 5 | 62429 | 6294 | 0,010950 | 0,010950 |
| Campagne 15 | 23 | AUTOMATED_PASS | 3 | 6854 | 7276 | 0,004495 | 0,004495 |
| Campagne 15 | 24 | AUTOMATED_PASS | 3 | 6726 | 8005 | 0,004843 | 0,004843 |
| Campagne 15 | 25 | AUTOMATED_PASS | 4 | 8554 | 7037 | 0,004587 | 0,004587 |
| Campagne 15 | 26 | AUTOMATED_PASS | 5 | 62687 | 5678 | 0,010674 | 0,010674 |
| Campagne 15 | 28 | BLOCKED | 2 | 15887 | 246 | 0,002109 | 0,002109 |
| Campagne 16 | 28 | BLOCKED | 8 | 773513 | 10226 | 0,128268 | 0,101802 |
| Campagne 17 | 28 | BLOCKED | 88 | 17857266 | 81868 | 4,101901 | 3,978291 |
| Campagne 18 | 28 | BLOCKED | 102 | 5755513 | 92002 | 0,947111 | 0,947111 |
| Campagne 19 | 28 | BLOCKED | 26 | 1018116 | 26634 | 0,140580 | 0,140580 |
| Campagne 20 | 28 | FAIL | 92 | 5377163 | 97637 | 0,905176 | 0,905176 |
| Campagne 21 | 28 | BLOCKED | 215 | 13993756 | 293870 | 2,547104 | 2,547104 |
| Campagne 22 | 01 | AUTOMATED_PASS | 2 | 3624 | 5875 | 0,033904 | 0,033904 |
| Campagne 22 | 02 | AUTOMATED_PASS | 2 | 3430 | 5335 | 0,030961 | 0,030961 |
| Campagne 22 | 03 | AUTOMATED_PASS | 2 | 3550 | 8191 | 0,045391 | 0,045391 |
| Campagne 22 | 04 | AUTOMATED_PASS | 2 | 3419 | 5783 | 0,033187 | 0,033187 |
| Campagne 22 | 05 | AUTOMATED_PASS | 2 | 3438 | 5855 | 0,033571 | 0,033571 |
| Campagne 22 | 06 | AUTOMATED_PASS | 2 | 3482 | 5608 | 0,032391 | 0,032391 |
| Campagne 22 | 07 | AUTOMATED_PASS | 6 | 21880 | 12853 | 0,091610 | 0,091610 |
| Campagne 22 | 08 | AUTOMATED_PASS | 5 | 17679 | 10169 | 0,072940 | 0,072940 |
| Campagne 22 | 09 | AUTOMATED_PASS | 3 | 5650 | 6989 | 0,042005 | 0,042005 |
| Campagne 22 | 10 | AUTOMATED_PASS | 3 | 5442 | 6324 | 0,038420 | 0,038420 |
| Campagne 22 | 11 | AUTOMATED_PASS | 3 | 5120 | 5538 | 0,034088 | 0,034088 |
| Campagne 22 | 12 | AUTOMATED_PASS | 3 | 5423 | 6632 | 0,039936 | 0,039936 |
| Campagne 22 | 13 | AUTOMATED_PASS | 4 | 19619 | 13339 | 0,091216 | 0,091216 |
| Campagne 22 | 14 | AUTOMATED_PASS | 3 | 4972 | 342 | 0,007923 | 0,007923 |
| Campagne 22 | 15 | AUTOMATED_PASS | 3 | 5035 | 494 | 0,008762 | 0,008762 |
| Campagne 22 | 16 | AUTOMATED_PASS | 3 | 4982 | 353 | 0,007990 | 0,007990 |
| Campagne 22 | 17 | AUTOMATED_PASS | 2 | 3247 | 303 | 0,005572 | 0,005572 |
| Campagne 22 | 18 | AUTOMATED_PASS | 2 | 3243 | 185 | 0,004977 | 0,004977 |
| Campagne 22 | 19 | AUTOMATED_PASS | 5 | 20895 | 5125 | 0,051740 | 0,051740 |
| Campagne 22 | 20 | AUTOMATED_PASS | 5 | 19792 | 3572 | 0,042596 | 0,042596 |
| Campagne 22 | 21 | AUTOMATED_PASS | 5 | 63277 | 7030 | 0,114242 | 0,114242 |
| Campagne 22 | 22 | AUTOMATED_PASS | 7 | 39194 | 6429 | 0,081132 | 0,081132 |
| Campagne 22 | 23 | AUTOMATED_PASS | 3 | 7254 | 5546 | 0,036795 | 0,036795 |
| Campagne 22 | 24 | AUTOMATED_PASS | 3 | 7105 | 6444 | 0,041099 | 0,041099 |
| Campagne 22 | 25 | AUTOMATED_PASS | 4 | 9166 | 5683 | 0,039870 | 0,039870 |
| Campagne 22 | 26 | AUTOMATED_PASS | 5 | 62935 | 6658 | 0,111955 | 0,111955 |
| Campagne 22 | 27 | AUTOMATED_PASS | 5 | 25676 | 3814 | 0,051161 | 0,051161 |
| Campagne 22 | 31 | AUTOMATED_PASS | 4 | 18993 | 12739 | 0,087433 | 0,087433 |
| Campagne 22 | 32 | AUTOMATED_PASS | 3 | 12269 | 6868 | 0,049674 | 0,049674 |
| Campagne 23 | 01 | AUTOMATED_PASS | 2 | 3604 | 6205 | 0,035528 | 0,035528 |

Export détaillé : [https://github.com/yanisAitlamine/repo-partage-humains/blob/couts-tests-20261028/documentation%20yanis/couts-campagnes-20261028.csv](https://github.com/yanisAitlamine/repo-partage-humains/blob/couts-tests-20261028/documentation%20yanis/couts-campagnes-20261028.csv). Il contient **156 lignes campagne/test**, avec les volumes de cache et de raisonnement. Séparateur point-virgule, virgule décimale.

## Couverture du montant

Sont inclus les essais incomplets, les résultats invalidés, les anciens cas retirés et les reprises identifiées sur leurs projets. Les données couvrent les campagnes historiques et le nouvel essai 01 ; les vérifications hors ligne ne sont pas ajoutées comme si elles avaient interrogé le modèle.

Une tentative de construction s’est terminée après dépassement de contexte, avec des compteurs et un coût enregistré nuls. Ce zéro est conservé comme donnée observée, sans inventer des jetons. Les autres réponses de cette campagne, dont les longues lectures, sont comptées. Les frais du lab, l’abonnement Codex et les frais annexes absents des compteurs OpenAI ne sont pas compris dans ce total de jetons.

## Délégation

La collecte historique, la déduplication, le recalcul et cette restitution ont été réalisés directement dans la conversation de Yanis, sans sous-agent. Une autre conversation travaillait déjà sur le suivi des consommations du nouveau lanceur ; son export du premier test a été lu et rapproché des compteurs. Le coût de ces conversations Codex est exclu. Les modèles des tests observés sont Luna et Terra ; le modèle exact du rédacteur n’est pas attesté par ces données.

## Collaboration

Les consignes et annonces partagées ont été consultées. L’intention a réservé la collecte technique et cette restitution, en préservant le suivi de consommation en cours dans l’autre conversation. Le staging historique a été lu sans lancer de traitement client. Le nouvel essai a été intégré depuis son export existant, sans connexion au contrôleur de lab. Les identifiants techniques de projet et de session restent dans les preuves d’origine. La fin de mission est annoncée après vérification du rapprochement et de la publication.
