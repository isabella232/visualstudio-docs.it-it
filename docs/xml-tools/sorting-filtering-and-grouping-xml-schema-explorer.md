---
title: Ordinamento, filtro e raggruppamento
description: Informazioni sulle opzioni disponibili tramite il menu Opzioni di ordinamento, filtro e raggruppamento sulla barra degli strumenti di ESPLORA XML Schema.
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
ms.openlocfilehash: f317ea59fd7f3318669a71d4480c5b53a182b327
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122098684"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Ordinamento, filtro e raggruppamento (ESPLORA XML Schema)

In questo argomento vengono descritte le opzioni disponibili tramite il menu Opzioni di **ordinamento, filtro** e raggruppamento sulla barra degli strumenti di ESPLORA **XML Schema.**

## <a name="filter-options"></a>Opzioni di filtro

Sono disponibili le seguenti opzioni del filtro. Per impostazione predefinita, le **opzioni Mostra spazi dei** nomi e Mostra file di **schema** sono selezionate.

- **Mostra spazi dei nomi**.

- **Mostra file di schema**.

- **Mostra Compositors (sequence/choice/all)**.

## <a name="sorting-options"></a>Opzioni di ordinamento

Sono disponibili le seguenti opzioni di ordinamento. Il valore predefinito è **Ordina per tipo**. **Le opzioni Ordina** per non si applicano a file e spazi dei nomi.

- **Ordina per tipo**.

- **Ordina per nome**.

- **Ordine dei documenti**.

### <a name="sort-by-type"></a>Ordina per tipo

Quando **l'opzione Ordina** per tipo è selezionata, i nodi globali vengono ordinati nell'ordine seguente. All'interno di ciascun gruppo i nodi vengono ordinati alfabeticamente.

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

Quando **l'opzione Ordina** per nome è selezionata, i nodi globali vengono ordinati nell'ordine seguente:

1. `import` nodi (in ordine alfabetico degli spazi dei nomi).

2. Nodi `include` (in ordine alfabetico degli attributi `schemaLocation`).

3. Nodi `redefine` (in ordine alfabetico degli attributi `schemaLocation`).

4. Altri nodi globali in ordine alfabetico.

### <a name="document-order"></a>Ordine documenti

**L'opzione Ordine** documenti è disponibile quando è **selezionata l'opzione** Mostra file di schema. Quando **l'opzione Ordine** documento è selezionata, i nodi globali vengono visualizzati nell'ordine in cui vengono visualizzati nel file di schema.

## <a name="persisting-sortfilter-options"></a>Persistenza delle opzioni di ordinamento/filtro

Le opzioni di ordinamento, filtro e raggruppamento vengono salvate nel Registro di sistema per ogni utente, indipendentemente dalla soluzione o dai file aperti quando sono state modificate le impostazioni.
