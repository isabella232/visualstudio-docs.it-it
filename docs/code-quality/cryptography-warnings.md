---
title: Avvisi di crittografia
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: d96723ea-a293-488d-b9db-adb437e50cdd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d55d0d565db2287c51b6e1e96ac26aecad1be1fa
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31920284"
---
# <a name="cryptography-warnings"></a>Avvisi di crittografia
Gli avvisi di crittografia supportano applicazioni e librerie più sicure attraverso l'uso corretto della crittografia. Questi avvisi contribuiscono ad evitare che il programma presenti difetti nella sicurezza. Se si disabilita uno qualsiasi di questi avvisi, è opportuno indicarne chiaramente il motivo nel codice e informare il responsabile della sicurezza designato per il progetto di sviluppo.

|Regola|Descrizione|
|----------|-----------------|
|[CA5350: non usare algoritmi di crittografia vulnerabili](../code-quality/ca5350-do-not-use-weak-cryptographic-algorithms.md)|Oggi si usano algoritmi di crittografia e funzioni hash deboli per diversi motivi, ma non dovrebbero essere usati per garantire la riservatezza o l'integrità dei dati che proteggono.        Questa regola si attiva quando vengono rilevati algoritmi TripleDES, SHA1 o RIPEMD160 nel codice.|
|[CA5351: non usare algoritmi di crittografia interrotti](../code-quality/ca5351-do-not-use-broken-cryptographic-algorithms.md)|Gli algoritmi di crittografia violati non sono considerati sicuri e il loro uso è fortemente sconsigliato. Questa regola si attiva quando nel codice vengono rilevati l'algoritmo hash MD5 oppure gli algoritmi di crittografia DES o RC2.|