---
title: Ordinamento, filtro e raggruppamento in XML Schema Explorer
description: Informazioni sulle opzioni disponibili tramite il menu opzioni di ordinamento, filtro e raggruppamento sulla barra degli strumenti di XML Schema Explorer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 172226334622b830db79b79f7eaae2c5fe7efc79
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351492"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Ordinamento, filtro e raggruppamento (XML Schema Explorer)

In questo argomento vengono descritte le opzioni disponibili tramite il menu **Opzioni di ordinamento, filtro e raggruppamento** sulla barra degli strumenti di **XML Schema Explorer** .

## <a name="filter-options"></a>Opzioni di filtro

Sono disponibili le seguenti opzioni del filtro. Per impostazione predefinita, sono selezionate le opzioni **Mostra spazi dei nomi** e **Mostra file di schema** .

- **Mostra spazi dei nomi**.

- **Mostra file di schema**.

- **Mostra compositor (sequence/choice/all)**.

## <a name="sorting-options"></a>Opzioni di ordinamento

Sono disponibili le seguenti opzioni di ordinamento. Il valore predefinito è **Ordina per tipo**. Le opzioni **Ordina per** non si applicano ai file e agli spazi dei nomi.

- **Ordina per tipo**.

- **Ordina per nome**.

- **Ordine del documento**.

### <a name="sort-by-type"></a>Ordina per tipo

Quando si seleziona l'opzione **Ordina per tipo** , i nodi globali vengono ordinati nell'ordine seguente. All'interno di ciascun gruppo i nodi vengono ordinati alfabeticamente.

1. Nodi `import`.

2. Nodi `include`.

3. Nodi `redefine`.

4. Nodi `attribute`.

5. Nodi `attributeGroup`.

6. Nodi `complexType`.

7. Nodi `simpleType`.

8. Nodi `element`.

9. Nodi `group`.

### <a name="sort-by-name"></a>Ordina per nome

Quando si seleziona l'opzione **Ordina per nome** , i nodi globali vengono ordinati nell'ordine seguente:

1. `import` nodi (in ordine alfabetico degli spazi dei nomi).

2. Nodi `include` (in ordine alfabetico degli attributi `schemaLocation`).

3. Nodi `redefine` (in ordine alfabetico degli attributi `schemaLocation`).

4. Altri nodi globali in ordine alfabetico.

### <a name="document-order"></a>Ordine documenti

L'opzione relativa all' **ordine dei documenti** è disponibile quando è selezionata l'opzione **Mostra file di schema** . Quando l' **ordine dei documenti** è selezionato, i nodi globali vengono visualizzati nell'ordine in cui vengono visualizzati nel file di schema.

## <a name="persisting-sortfilter-options"></a>Salvataggio permanente delle opzioni di ordinamento/filtro

Le opzioni di ordinamento, filtro e raggruppamento vengono salvate nel Registro di sistema per ogni utente, indipendentemente dalla soluzione o dai file aperti quando sono state modificate le impostazioni.
