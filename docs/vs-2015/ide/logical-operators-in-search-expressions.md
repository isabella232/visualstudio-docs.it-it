---
title: Operatori logici nelle espressioni di ricerca | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0cf55bbdc025b4aabd13f7ded72c2ea69386a61b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518886"
---
# <a name="logical-operators-in-search-expressions"></a>Operatori logici nelle espressioni di ricerca
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [gli operatori logici nelle espressioni di ricerca](https://docs.microsoft.com/visualstudio/ide/logical-operators-in-search-expressions).  
  
Con gli operatori logici è possibile limitare la ricerca di contenuto mediante la creazione di espressioni di ricerca più complesse partendo da quelle più semplici. Come illustrato nella tabella seguente, gli operatori logici specificano in che modo più termini di ricerca debbano essere combinati in una query di ricerca.  
  
> [!IMPORTANT]
>  Per essere riconosciuti dal motore di ricerca, gli operatori logici devono essere immessi interamente in lettere maiuscole.  
  
|Per cercare|Usa|Esempio|Risultato|  
|-------------------|---------|-------------|------------|  
|Entrambi i termini nello stesso argomento|AND|DIB AND tavolozza|Argomenti che contengono sia "DIB" che "tavolozza".|  
|Uno dei termini in un argomento|OR|raster OR vettore|Argomenti che contengono "raster" o "vettore".|  
|Primo termine senza il secondo nello stesso argomento|NOT|"sistema operativo" NOT DOS|Argomenti che contengono "sistema operativo" ma non "DOS".|  
|Entrambi i termini, vicini in un argomento|VICINO|utente NEAR kernel|Gli argomenti che contengono "utente" in prossimità di "kernel".|  
  
## <a name="see-also"></a>Vedere anche  
 [Full-Text Search Tips](../ide/full-text-search-tips.md)  (Suggerimenti per la ricerca full-text)  
 [Locate Information](../ide/locate-information.md) (Individuare informazioni)



