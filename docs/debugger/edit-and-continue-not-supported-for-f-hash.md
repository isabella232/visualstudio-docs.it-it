---
title: Modifica e continuazione non supportate per F# | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [F#]
- Debugging [F#], Edit and Continue
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 856940231e65932b208c83bf4ff1231395b04382
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838073"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Modifica e continuazione non supportate per F# #
La modifica e la continuazione non sono supportate quando si esegue il debug del codice F #. Le modifiche al codice F# durante una sessione di debug sono possibili ma devono essere evitate. Le modifiche di codice non vengono applicate durante la sessione di debug. Pertanto, qualsiasi modifica apportata al codice F# durante il debug comporterà una non corrispondenza del codice sorgente con il codice in fase di debug.
