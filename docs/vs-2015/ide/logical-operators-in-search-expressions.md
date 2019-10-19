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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d56f2dfc2924008a6be293fe1498f0ffe32abaf
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651432"
---
# <a name="logical-operators-in-search-expressions"></a>Operatori logici nelle espressioni di ricerca
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con gli operatori logici è possibile limitare la ricerca di contenuto mediante la creazione di espressioni di ricerca più complesse partendo da quelle più semplici. Come illustrato nella tabella seguente, gli operatori logici specificano in che modo più termini di ricerca debbano essere combinati in una query di ricerca.

> [!IMPORTANT]
> Per essere riconosciuti dal motore di ricerca, gli operatori logici devono essere immessi interamente in lettere maiuscole.

|Per cercare|Uso|Esempio|Risultato|
|-------------------|---------|-------------|------------|
|Entrambi i termini nello stesso argomento|AND|DIB AND tavolozza|Argomenti che contengono sia "DIB" che "tavolozza".|
|Uno dei termini in un argomento|Oppure|raster OR vettore|Argomenti che contengono "raster" o "vettore".|
|Primo termine senza il secondo nello stesso argomento|NOT|"sistema operativo" NOT DOS|Argomenti che contengono "sistema operativo" ma non "DOS".|
|Entrambi i termini, vicini in un argomento|VICINO|utente NEAR kernel|Gli argomenti che contengono "utente" in prossimità di "kernel".|

## <a name="see-also"></a>Vedere anche
 [Suggerimenti per la ricerca full-text](../ide/full-text-search-tips.md) [individuare le informazioni](../ide/locate-information.md)
