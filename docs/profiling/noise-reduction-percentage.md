---
title: Percentuale di riduzione del rumore | Microsoft Docs
description: Informazioni sull'impostazione Percentuale di riduzione del rumore e su come è possibile controllare il numero di voci visualizzate nell'albero delle chiamate.
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.cv.threads.filter
helpviewer_keywords:
- Concurrency Visualizer, Noise Reduction Percentage
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 23715bd06b37c016a48ad1a173eae3b6d5d31f7a50528c4bad8c3448b19256e3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121316085"
---
# <a name="noise-reduction-percentage"></a>Percentuale di riduzione del rumore
Per impostazione predefinita, il valore dell'impostazione Percentuale di riduzione del rumore è 2. Solo le voci con una percentuale di tempo inclusivo maggiore o uguale a questa impostazione vengono visualizzate nell'albero delle chiamate. Modificando l'impostazione, è possibile controllare il numero di voci visualizzate nell'albero delle chiamate. Ad esempio, se si imposta il valore su 10 verranno visualizzate solo le voci dell'albero delle con un tempo inclusivo maggiore o uguale al 10%. Se si aumenta il valore dell'impostazione, è possibile concentrarsi sulle voci con maggiore impatto sulle prestazioni del processo.