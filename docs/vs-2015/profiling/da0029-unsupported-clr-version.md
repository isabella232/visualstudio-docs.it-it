---
title: 'DA0029: Versione CLR non supportata | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 532427618f476e1e187d8a1c88749810f9d157c9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68152655"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Versione CLR non supportata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id regola | DA0029 |  
| Categoria | Utilizzo degli strumenti di profilatura |  
| Metodo di profilatura | Profilatura dalla riga di comando |  
| Messaggio | Durante la raccolta è stata rilevata una versione CLR non supportata. È possibile che i simboli gestiti non vengano risolti correttamente.|  
| Tipo di regola | Le informazioni. |  
  
## <a name="cause"></a>Causa  
 Si sta tentando di profilare un'applicazione che usa [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)] non supportato dagli strumenti di profilatura.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questo avviso si verifica perché gli strumenti di profilatura non sono in grado di risolvere i simboli per il codice gestito in esecuzione nell'applicazione. Gli strumenti di profilatura non sono in grado di risolvere i simboli di codice gestito per le applicazioni che eseguono [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)].  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 No.
