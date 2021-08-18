---
title: Modifica e continuazione non supportato per F# | Microsoft Docs
description: Modifica e continuazione non è supportato per il debug F#. Le modifiche al codice durante il debug non vengono applicate all'origine, quindi il codice in fase di debug non corrisponderà all'origine.
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c37954fcb334116a81de8a29937983719f6b31ed
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134103"
---
# <a name="edit-and-continue-not-supported-for-f"></a>Modifica e continuazione non supportate per F# #
La modifica e la continuazione non sono supportate quando si esegue il debug del codice F #. Le modifiche al codice F# durante una sessione di debug sono possibili ma devono essere evitate. Le modifiche di codice non vengono applicate durante la sessione di debug. Pertanto, qualsiasi modifica apportata al codice F# durante il debug comporterà una non corrispondenza del codice sorgente con il codice in fase di debug.
