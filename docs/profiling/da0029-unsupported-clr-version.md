---
title: 'DA0029: Versione CLR non supportata | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a3855b8975684b088b2838a866db36e6ec19e665
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62936291"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Versione CLR non supportata

|||
|-|-|
|ID regola|DA0029|
|Category|Uso degli strumenti di profilatura|
|Metodo di profilatura|Profilatura dalla riga di comando|
|Messaggio|È stata rilevata una versione CLR non supportata durante la raccolta. È possibile che i simboli gestiti non vengano risolti correttamente.|
|Tipo regola|Informazioni.|

## <a name="cause"></a>Causa
 Si sta tentando di profilare un'applicazione che usa [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)] non supportato dagli strumenti di profilatura.

## <a name="rule-description"></a>Descrizione della regola
 Questo avviso si verifica perché gli strumenti di profilatura non sono in grado di risolvere i simboli per il codice gestito in esecuzione nell'applicazione. Gli strumenti di profilatura non sono in grado di risolvere i simboli di codice gestito per le applicazioni che eseguono [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Nessuno.