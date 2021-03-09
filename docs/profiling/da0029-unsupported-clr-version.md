---
title: DA0029-versione CLR non supportata | Microsoft Docs
description: Si sta tentando di profilare un'applicazione che usa la .NET Framework 1,1 che non è supportata dal Strumenti di profilatura.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: b3f5e5129bed479273e141af70121d5a344972e2
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2021
ms.locfileid: "102465842"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Versione CLR non supportata

|Elemento|valore|
|-|-|
|ID regola|DA0029|
|Category|Uso degli strumenti di profilatura|
|Metodo di profilatura|Profilatura dalla riga di comando|
|Message|È stata rilevata una versione CLR non supportata durante la raccolta. È possibile che i simboli gestiti non vengano risolti correttamente.|
|Tipo regola|Informazioni.|

## <a name="cause"></a>Causa
 Si sta tentando di profilare un'applicazione che usa [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] non supportato dagli strumenti di profilatura.

## <a name="rule-description"></a>Descrizione della regola
 Questo avviso si verifica perché gli strumenti di profilatura non sono in grado di risolvere i simboli per il codice gestito in esecuzione nell'applicazione. Gli strumenti di profilatura non sono in grado di risolvere i simboli di codice gestito per le applicazioni che eseguono [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Nessuno.
