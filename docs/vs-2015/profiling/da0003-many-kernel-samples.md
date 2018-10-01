---
title: 'DA0003: Numero elevato di campioni del kernel | Microsoft Docs'
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
- vs.performance.rules.DA0003
- vs.performance.DA0003
- vs.performance.3
- vs.performance.rules.DAManyKernelSamples
ms.assetid: c1f46f77-eb95-42e5-b340-d86bc9de41b4
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fd4412fc120eb0a0fa039ac91bec4da4ba4a6f44
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531507"
---
# <a name="da0003-many-kernel-samples"></a>DA0003: Numero elevato di campioni del kernel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [DA0003: numero di campioni del kernel](https://docs.microsoft.com/visualstudio/profiling/da0003-many-kernel-samples).  
  
Id regola | DA0003 |  
| Categoria | Utilizzo degli strumenti di profilatura |  
| Metodi di profilatura | Campionamento |  
| Messaggio | Presente un numero elevato di campioni in modalità Kernel. Questa circostanza potrebbe indicare un volume elevato di attività I/O oppure un rapporto elevato di cambi di contesto. Si consiglia di profilare nuovamente l'applicazione utilizzando la modalità strumentazione. |  
| Tipo di regola | Informazioni |  
  
## <a name="cause"></a>Causa  
 Una parte significativa degli esempi di stack di chiamate raccolti per l'applicazione era in esecuzione in modalità kernel. Si consiglia di profilare l'applicazione usando un altro metodo di profilatura.  
  
## <a name="rule-description"></a>Descrizione della regola  
 In Windows è possibile eseguire il codice in modalità kernel oppure in modalità utente. La modalità kernel è chiamata anche modalità privilegiata. Solo il codice di sistema di basso livello, ad esempio i driver di dispositivo, viene eseguito in modalità kernel. Un'applicazione in modalità utente può passare alla modalità kernel per eseguire operazioni di I/O, per attendere primitive di sincronizzazione di thread o processi o per eseguire chiamate di sistema.  
  
 Il campionamento è più efficace quando si profilano applicazioni che per la maggior parte del tempo eseguono operazioni in modalità utente. Il numero di campioni raccolti durante l'esecuzione dell'applicazione in modalità kernel può indicare operazioni di I/O frequenti o può indicare che si stanno verificando cambi di contesto. Nessuna di queste operazioni può essere analizzata usando il metodo di campionamento. Se è stato acquisito un numero eccessivo di campioni in modalità kernel, è possibile che i dati di campionamento non contengano un numero sufficiente di campioni in modalità utente per essere statisticamente significativi.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Si consiglia di profilare nuovamente l'applicazione usando una delle opzioni seguenti:  
  
-   Profilare usando il metodo di strumentazione.  
  
-   Aumentare la frequenza di campionamento per tentare di raccogliere più campioni in modalità utente.



