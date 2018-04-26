---
title: L'ordinamento, filtro e raggruppamento in XML Schema Explorer
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f4354e58e8de2d877e726b4615bac3832bfc37d2
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Ordinamento, filtro e raggruppamento (XML Schema Explorer)

In questo argomento vengono descritte le opzioni sono disponibili tramite il **opzioni di raggruppamento, filtro e ordinamento** menu sulla barra degli strumenti di XML Schema Explorer.

## <a name="filter-options"></a>Opzioni di filtro

 Sono disponibili le seguenti opzioni del filtro. Per impostazione predefinita, il **Mostra spazi dei nomi** e **Mostra file di Schema** le opzioni sono selezionate.

-   **Mostra spazi dei nomi**.

-   **Mostra file di Schema**.

-   **Mostra Compositor (sequence/choice/all)**.

## <a name="sorting-options"></a>Opzioni di ordinamento

 Sono disponibili le seguenti opzioni di ordinamento. Il valore predefinito è **Ordina per tipo**. Le opzioni Ordina per non si applicano ai file e agli spazi dei nomi.

-   **Ordina per tipo**.

-   **Ordina per nome**.

-   **Ordine documenti**.

### <a name="sort-by-type"></a>Ordina per tipo

 Quando il **Ordina per tipo** opzione è selezionata, i nodi globali vengono ordinati nell'ordine seguente. All'interno di ciascun gruppo i nodi vengono ordinati alfabeticamente.

1.  Nodi `import`.

2.  Nodi `include`.

3.  Nodi `redefine`.

4.  Nodi `attribute`.

5.  Nodi `attributeGroup`.

6.  Nodi `complexType`.

7.  Nodi `simpleType`.

8.  Nodi `element`.

9. Nodi `group`.

### <a name="sort-by-name"></a>Ordina per nome

 Quando il **Ordina per nome** opzione è selezionata, i nodi globali vengono ordinati nell'ordine seguente:

1.  Nodi `import` (in ordine alfabetico degli spazi dei nomi).

2.  Nodi `include` (in ordine alfabetico degli attributi `schemaLocation`).

3.  Nodi `redefine` (in ordine alfabetico degli attributi `schemaLocation`).

4.  Altri nodi globali in ordine alfabetico.

### <a name="document-order"></a>Ordine documenti

 Il **ordine del documento** opzione è disponibile quando il **Mostra file di Schema** opzione è selezionata. Quando **ordine del documento** è selezionata, i nodi globali vengono visualizzati nell'ordine in cui appaiono nel file di schema.

## <a name="persisting-sortfilter-options"></a>Persistenza delle opzioni di ordinamento e filtro

 Le opzioni di ordinamento, filtro e raggruppamento vengono salvate nel Registro di sistema per ogni utente, indipendentemente dalla soluzione o dai file aperti quando sono state modificate le impostazioni.