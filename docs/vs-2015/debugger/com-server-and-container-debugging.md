---
title: Server COM e il debug di contenitori | Microsoft Docs
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
- vs.debug.com
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 531c485f50a4a775ca2933c40f5ff74ca9c43717
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528310"
---
# <a name="com-server-and-container-debugging"></a>Debug dei server e dei contenitori COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Server COM e il contenitore debug](https://docs.microsoft.com/visualstudio/debugger/com-server-and-container-debugging).  
  
Le applicazioni COM eseguono alcune attività che non sono sotto il controllo diretto del programmatore. Le comunicazioni tra le DLL, il conteggio di utilizzo degli oggetti e le operazioni relative agli Appunti rappresentano solo alcune delle aree nelle quali potrebbero verificarsi comportamenti non prevedibili. In questi casi il primo passo consiste nel tracciare il codice sorgente.  
  
 Il debugger di Visual Studio supporta l'esecuzione delle istruzioni attraverso i contenitori e i server e all'interno di essi. Tale supporto include la capacità di eseguire le istruzioni RPC (Remote Procedure Call, chiamata a procedura remota).  
  
##  <a name="BKMK_COMServerandContainerintheSameSolution"></a> Debug di un Server COM e i contenitori nella stessa soluzione  
 È possibile eseguire il debug di un server e di un contenitore COM utilizzando due progetti all'interno della stessa soluzione. Impostare i punti di interruzione appropriati in ogni progetto e procedere al debug. Quando il contenitore effettua una chiamata nel codice del server in cui è stato impostato un punto di interruzione, il contenitore resta in attesa della fine dell'esecuzione del codice del server ovvero il termine del relativo debug.  
  
 Il debug di un contenitore COM è simile a quello di un programma standard. Presenta invece delle differenze quando si riferisce a un evento che genera un callback, ad esempio il trascinamento di dati in un'applicazione contenitore. In questo caso, è necessario impostare un punto di interruzione nella funzione di callback.  
  
##  <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Debug di un'applicazione Server senza informazioni sul contenitore  
 Quando le informazioni di debug relative all'applicazione contenitore non vengono utilizzate o non sono disponibili, l'avvio del debug di un'applicazione server si suddivide in tre passaggi:  
  
1.  Avviare il debug del server come applicazione normale.  
  
2.  Impostare i punti di interruzione nel modo desiderato.  
  
3.  Avviare l'applicazione contenitore.  
  
##  <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Debug di un'applicazione Server e dominio (SDI) di isolamento  
 Se si esegue il debug un'applicazione server SDI, è necessario specificare `/Embedding` o `/Automation` nel **argomenti della riga di comando** proprietà nel *progetto* la finestra di dialogo Pagine delle proprietà per C/C++, c#, o Progetti Visual Basic.  
  
 Grazie a questi argomenti della riga di comando, il debugger è in grado di avviare l'applicazione server come se tale avvio venisse eseguito da un contenitore. In seguito all'avvio del contenitore da Program Manager o File Manager, il contenitore utilizzerà l'istanza del server già avviata dal debugger.  
  
 Per l'accesso di *progetto* finestra di dialogo Pagine delle proprietà, pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere Proprietà dal menu di scelta rapida. Per individuare la proprietà Argomenti della riga di comando, espandere la categoria Proprietà di configurazione e fare clic sulla pagina Debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md)


