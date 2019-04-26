---
title: Operatori logici nelle espressioni di ricerca | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, logical operators in search
- logical operators in search [Help Viewer 2.0]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 30a33a434540fded8daab0628d0bd6dd7fb0ff38
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63412263"
---
# <a name="logical-operators-in-search-expressions"></a>Operatori logici nelle espressioni di ricerca
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con gli operatori logici è possibile limitare la ricerca di contenuto mediante la creazione di espressioni di ricerca più complesse partendo da quelle più semplici. Come illustrato nella tabella seguente, gli operatori logici specificano in che modo più termini di ricerca debbano essere combinati in una query di ricerca.  
  
> [!IMPORTANT]
> Per essere riconosciuti dal motore di ricerca, gli operatori logici devono essere immessi interamente in lettere maiuscole.  
  
|Per cercare|Usa|Esempio|Risultato|  
|-------------------|---------|-------------|------------|  
|Entrambi i termini nello stesso argomento|AND|DIB AND tavolozza|Argomenti che contengono sia "DIB" che "tavolozza".|  
|Uno dei termini in un argomento|OR|raster OR vettore|Argomenti che contengono "raster" o "vettore".|  
|Primo termine senza il secondo nello stesso argomento|NOT|"sistema operativo" NOT DOS|Argomenti che contengono "sistema operativo" ma non "DOS".|  
|Entrambi i termini, vicini in un argomento|VICINO|utente NEAR kernel|Gli argomenti che contengono "utente" in prossimità di "kernel".|  
  
## <a name="see-also"></a>Vedere anche  
 [Full-Text Search Tips](../ide/full-text-search-tips.md)  (Suggerimenti per la ricerca full-text)  
 [Locate Information](../ide/locate-information.md) (Individuare informazioni)
