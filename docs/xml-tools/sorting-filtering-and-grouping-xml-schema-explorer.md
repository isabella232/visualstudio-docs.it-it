---
title: Ordinamento, filtro e raggruppamento
description: Informazioni sulle opzioni disponibili tramite il menu Opzioni di ordinamento, filtro e raggruppamento sulla barra degli strumenti di XML Schema Explorer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: ba4e53916df5a1434daee75fd2ba04f3f9348d7fecc13219c93c283d006924c9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121423572"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Ordinamento, filtro e raggruppamento (XML Schema Explorer)

In questo argomento vengono descritte le opzioni disponibili tramite il menu Opzioni di **ordinamento, filtro** e raggruppamento sulla barra degli strumenti di XML **Schema Explorer.**

## <a name="filter-options"></a>Opzioni di filtro

Sono disponibili le seguenti opzioni del filtro. Per impostazione predefinita, le **opzioni Mostra spazi dei nomi** e Mostra file **di** schema sono selezionate.

- **Mostra spazi dei nomi**.

- **Mostra file di schema**.

- **Mostra Compositors (sequence/choice/all)**.

## <a name="sorting-options"></a>Opzioni di ordinamento

Sono disponibili le seguenti opzioni di ordinamento. Il valore predefinito è **Sort By Type.** **Le opzioni Ordina** per non si applicano a file e spazi dei nomi.

- **Ordina per tipo**.

- **Ordina per nome**.

- **Ordine dei documenti.**

### <a name="sort-by-type"></a>Ordina per tipo

Quando **l'opzione Ordina per tipo** è selezionata, i nodi globali vengono ordinati nell'ordine seguente. All'interno di ciascun gruppo i nodi vengono ordinati alfabeticamente.

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

Quando **l'opzione Ordina** per nome è selezionata, i nodi globali vengono ordinati nel seguente ordine:

1. `import` nodi (in ordine alfabetico degli spazi dei nomi).

2. Nodi `include` (in ordine alfabetico degli attributi `schemaLocation`).

3. Nodi `redefine` (in ordine alfabetico degli attributi `schemaLocation`).

4. Altri nodi globali in ordine alfabetico.

### <a name="document-order"></a>Ordine documenti

**L'opzione Ordine** documento è disponibile quando è **selezionata l'opzione** Mostra file di schema . Quando **l'opzione Ordine** documento è selezionata, i nodi globali vengono visualizzati nell'ordine in cui vengono visualizzati nel file di schema.

## <a name="persisting-sortfilter-options"></a>Persistenza delle opzioni di ordinamento/filtro

Le opzioni di ordinamento, filtro e raggruppamento vengono salvate nel Registro di sistema per ogni utente, indipendentemente dalla soluzione o dai file aperti quando sono state modificate le impostazioni.
