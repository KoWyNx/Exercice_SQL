## 10 Listez pour chaque ticket la quantité totale d’articles vendus. (Classer par quantité décroissante)

```mysql
SELECT NUMERO_TICKET, SUM(QUANTITE) AS QuantiteTotale
FROM ventes
GROUP BY NUMERO_TICKET
ORDER BY QuantiteTotale DESC;

```

## 11 Listez chaque ticket pour lequel la quantité totale d’articles vendus est supérieure à 500. (Classer par quantité décroissante)

```mysql
SELECT NUMERO_TICKET, SUM(QUANTITE) AS QuantiteTotale
FROM ventes
GROUP BY NUMERO_TICKET
HAVING QuantiteTotale > 500
ORDER BY QuantiteTotale DESC;

```

## 12 Listez chaque ticket pour lequel la quantité totale d’articles vendus est supérieure à 500. On exclura du total, les ventes ayant une quantité supérieure à 50 (classer par quantité décroissante)

```mysql
SELECT NUMERO_TICKET, SUM(QUANTITE) AS QuantiteTotale
FROM ventes
WHERE QUANTITE <= 50
GROUP BY NUMERO_TICKET
HAVING QuantiteTotale > 500
ORDER BY QuantiteTotale DESC;

```

## 13 Listez les bières de type ‘Trappiste’. (id, nom de la bière, volume et titrage)

```mysql
SELECT ID_ARTICLE, NOM_ARTICLE, volume, titrage
FROM article
WHERE NOM_ARTICLE LIKE '%Trappiste%';
```

## 14 Listez les marques de bières du continent ‘Afrique’

```mysql
SELECT DISTINCT m.ID_MARQUE, m.NOM_MARQUE
FROM marque m
JOIN pays b ON m.ID_PAYS = b.ID_PAYS
JOIN continent p ON b.ID_CONTINENT = p.ID_CONTINENT
WHERE p.NOM_CONTINENT = 'Afrique';
```

## 15 Lister les bières du continent ‘Afrique’

```mysql
SELECT b.ID_ARTICLE, b.NOM_ARTICLE, p.NOM_PAYS, c.NOM_CONTINENT
FROM article b
join marque m on b.ID_MARQUE = m.ID_MARQUE
JOIN pays p ON m.ID_PAYS = p.ID_PAYS
JOIN continent c ON p.ID_CONTINENT = c.ID_CONTINENT
WHERE c.NOM_CONTINENT = 'Afrique';
```

## 16. Lister les tickets (année, numéro de ticket, montant total payé). En sachant que le prix de vente est égal au prix d’achat augmenté de 15%.

```mysql
SELECT YEAR(DATE_VENTE) AS ANNEE, NUMERO_TICKET, SUM(round(PRIX_ACHAT * 1.15, 2)) AS MontantTotalPaye
FROM ticket
JOIN article ON ticket.NUMERO_TICKET = article.ID_ARTICLE
GROUP BY YEAR(DATE_VENTE), NUMERO_TICKET;

```

## 17  Donner le C.A. par année.

```mysql
```

## 18. Lister les quantités vendues de chaque article pour l’année 2016.

```mysql

```

## 19. Lister les quantités vendues de chaque article pour les années 2014, 2015, 2016.

```mysql

```

