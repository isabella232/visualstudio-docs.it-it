---
title: L'ordinamento, filtro e raggruppamento (XML Schema Explorer) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a914de0-9ffc-4526-9603-92e460e52513
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9cb8086e894130fa20f8c270c9dafe6b302c989c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530240"
---
# <a name="sorting-filtering-and-grouping-xml-schema-explorer"></a>Ordinamento, filtro e raggruppamento (XML Schema Explorer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [ordinamento, filtro e raggruppamento (XML Schema Explorer)](https://docs.microsoft.com/visualstudio/xml-tools/sorting-filtering-and-grouping-xml-schema-explorer).  
  
  
In questo argomento vengono descritte le opzioni disponibili tramite il **opzioni di raggruppamento, filtro e ordinamento** menu sulla barra degli strumenti XML Schema Explorer.  
  
## <a name="filter-options"></a>Opzioni di filtro  
 Sono disponibili le seguenti opzioni del filtro. Per impostazione predefinita, il **Mostra spazi dei nomi** e **Mostra file di Schema** sono selezionate le opzioni.  
  
-   **Mostra spazi dei nomi**.  
  
-   **Mostra file di Schema**.  
  
-   **Mostra Compositor (sequence/choice/all)**.  
  
## <a name="sorting-options"></a>Opzioni di ordinamento  
 Sono disponibili le seguenti opzioni di ordinamento. Il valore predefinito è **Ordina per tipo**. Le opzioni Ordina per non si applicano ai file e agli spazi dei nomi.  
  
-   **Ordina per tipo**.  
  
-   **Ordina per nome**.  
  
-   **Ordine dei documenti**.  
  
### <a name="sort-by-type"></a>Ordina per tipo  
 Quando la **Ordina per tipo** opzione è selezionata, i nodi globali vengono ordinati nell'ordine seguente. All'interno di ciascun gruppo i nodi vengono ordinati alfabeticamente.  
  
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
 Quando la **Ordina per nome** opzione è selezionata, i nodi globali vengono ordinati nell'ordine seguente:  
  
1.  Nodi `import` (in ordine alfabetico degli spazi dei nomi).  
  
2.  Nodi `include` (in ordine alfabetico degli attributi `schemaLocation`).  
  
3.  Nodi `redefine` (in ordine alfabetico degli attributi `schemaLocation`).  
  
4.  Altri nodi globali in ordine alfabetico.  
  
### <a name="document-order"></a>Ordine documenti  
 Il **ordine del documento** opzione è disponibile quando il **Mostra file di Schema** opzione è selezionata. Quando **ordine del documento** è selezionata, i nodi globali vengono visualizzati nell'ordine in cui vengono visualizzati nel file di schema.  
  
## <a name="persisting-sortfilter-options"></a>Persistenza delle opzioni di ordinamento e filtro  
 Le opzioni di ordinamento, filtro e raggruppamento vengono salvate nel Registro di sistema per ogni utente, indipendentemente dalla soluzione o dai file aperti quando sono state modificate le impostazioni.





