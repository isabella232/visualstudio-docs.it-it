---
title: Applicazioni Server SDI | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba975d21e1fbef2d32b45dd4ebdc758e8b6cf575
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199069"
---
# <a name="sdi-server-applications"></a>Applicazioni server SDI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si esegue il debug un'applicazione server SDI, è necessario specificare `/Embedding` o `/Automation` nel **argomenti della riga di comando** proprietà nel *progetto* la finestra di dialogo Pagine delle proprietà per C/C++, c#, o Progetti Visual Basic.  
  
 Grazie a questi argomenti della riga di comando, il debugger è in grado di avviare l'applicazione server come se tale avvio venisse eseguito da un contenitore. In seguito all'avvio del contenitore da Program Manager o File Manager, il contenitore utilizzerà l'istanza del server già avviata dal debugger.  
  
## <a name="finding-the-command-line-arguments-property"></a>Ricerca della proprietà Argomenti della riga di comando  
 Per l'accesso di *progetto* finestra di dialogo Pagine delle proprietà, pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere Proprietà dal menu di scelta rapida. Per individuare la proprietà Argomenti della riga di comando, espandere la categoria Proprietà di configurazione e fare clic sulla pagina Debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Procedura: Eseguire il debug di server COM](../debugger/how-to-debug-com-servers.md)



