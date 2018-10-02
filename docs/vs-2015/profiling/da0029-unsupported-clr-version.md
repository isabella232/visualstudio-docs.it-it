---
title: 'DA0029: Versione CLR non supportata | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.29
- vs.performance.rules.DA0029
helpviewer_keywords:
- vs.performance.29
- vs.performance.DA0029
- vs.performance.rules.DA0029
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: df5deda533c21033d26af4b8dc08d98a5dafc583
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517108"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Versione CLR non supportata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [DA0029: versione CLR non supportata](https://docs.microsoft.com/visualstudio/profiling/da0029-unsupported-clr-version).  
  
Id regola | DA0029 |  
| Categoria | Utilizzo degli strumenti di profilatura |  
| Metodo di profilatura | Profilatura dalla riga di comando |  
| Messaggio | Durante la raccolta è stata rilevata una versione CLR non supportata. Simboli gestiti non vengano risolti correttamente. |  
| Tipo di regola | Le informazioni. |  
  
## <a name="cause"></a>Causa  
 Si sta tentando di profilare un'applicazione che usa [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)] non supportato dagli strumenti di profilatura.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questo avviso si verifica perché gli strumenti di profilatura non sono in grado di risolvere i simboli per il codice gestito in esecuzione nell'applicazione. Gli strumenti di profilatura non sono in grado di risolvere i simboli di codice gestito per le applicazioni che eseguono [!INCLUDE[net_v11_long](../includes/net-v11-long-md.md)].  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Nessuno.



