---
title: 'Modifica e continuazione non supportate per F # | Microsoft Docs'
description: "La funzionalità modifica e continuazione non è supportata per il debug F #. Le modifiche al codice durante il debug non vengono applicate all'origine, quindi il codice di cui è in corso il debug non corrisponderà all'origine."
ms.custom: SEO-VS-2020
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 33d1e8379e71c41e42cbf761ccdfe740342ee642
ms.sourcegitcommit: 47da50a74fcd3db66d97cb20accac983bc41912f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96863088"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Modifica e continuazione non supportate per F# #
La modifica e la continuazione non sono supportate quando si esegue il debug del codice F #. Le modifiche al codice F# durante una sessione di debug sono possibili ma devono essere evitate. Le modifiche di codice non vengono applicate durante la sessione di debug. Pertanto, qualsiasi modifica apportata al codice F# durante il debug comporterà una non corrispondenza del codice sorgente con il codice in fase di debug.
