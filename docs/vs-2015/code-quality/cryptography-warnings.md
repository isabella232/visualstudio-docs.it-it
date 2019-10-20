---
title: Avvisi di crittografia | Microsoft Docs
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d9f5694ccf48615ebdf7157adc80543b0fbb71eb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667678"
---
# <a name="cryptography-warnings"></a>Avvisi di crittografia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli avvisi di crittografia supportano applicazioni e librerie più sicure attraverso l'uso corretto della crittografia. Questi avvisi contribuiscono ad evitare che il programma presenti difetti nella sicurezza. Se si disabilita uno qualsiasi di questi avvisi, è opportuno indicarne chiaramente il motivo nel codice e informare il responsabile della sicurezza designato per il progetto di sviluppo.

|Regola|Descrizione|
|----------|-----------------|
|[CA5350: non usare algoritmi di crittografia vulnerabili](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Oggi si usano algoritmi di crittografia e funzioni hash deboli per diversi motivi, ma non dovrebbero essere usati per garantire la riservatezza o l'integrità dei dati che proteggono.        Questa regola si attiva quando vengono rilevati algoritmi TripleDES, SHA1 o RIPEMD160 nel codice.|
|[CA5351: non usare algoritmi di crittografia interrotti](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Gli algoritmi di crittografia violati non sono considerati sicuri e il loro uso è fortemente sconsigliato. Questa regola si attiva quando nel codice vengono rilevati l'algoritmo hash MD5 oppure gli algoritmi di crittografia DES o RC2.|
