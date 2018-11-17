---
title: 'DA0029: Versione CLR non supportata | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51195b14be7bffe682f4ac8588e38c6f5bd56e58
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51762535"
---
# <a name="da0029-unsupported-clr-version"></a>DA0029: Versione CLR non supportata
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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



