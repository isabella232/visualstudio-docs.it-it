---
title: Libreria di controlli (codice gestito) Web | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- debugging DLLs
- debugging [Visual Studio], Web control libraries
ms.assetid: 2413883f-9e88-406d-b874-0ed743b75d40
caps.latest.revision: 29
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6bdc9c62699e905a2c7aaee106dcb9cba14ac312
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529554"
---
# <a name="web-control-library-managed-code"></a>Libreria di controlli Web (Codice gestito)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [libreria di controlli Web (codice gestito)](https://docs.microsoft.com/visualstudio/debugger/web-control-library-managed-code).  
  
Il modello di progetto Libreria di controlli Web consente di creare una DLL. Poiché la libreria di classi è una DLL, non è possibile eseguirla direttamente. È necessario creare una pagina di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] in cui sia incorporato il controllo. Per altre informazioni, vedere [modello libreria di controlli Web](http://msdn.microsoft.com/en-us/00666b07-71d2-4ace-a13c-cc130a3ce372).  
  
### <a name="to-debug-a-web-control-library-method-1"></a>Per eseguire il debug di una libreria di controlli Web (procedura 1)  
  
1.  Aprire un progetto Libreria di controlli Web esistente o crearne uno nuovo.  
  
2.  Creare una pagina di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] in cui sia incorporato il controllo.  
  
3.  Nel sito Web che ospita il test harness di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] creare una sottodirectory denominata `/Code`.  
  
4.  Copiare il codice sorgente del controllo nella sottodirectory `/Code`.  
  
5.  Aprire il codice sorgente nella sottodirectory `/Code` e impostare i punti di interruzione.  
  
6.  Aprire una finestra del browser con un URL che punta al test harness. Quando verrà raggiunto un punto di interruzione nel controllo sarà possibile iniziare il debug.  
  
### <a name="to-debug-a-web-control-library-method-2"></a>Eseguire il debug di una libreria di controlli Web (il metodo 2)  
  
1.  Creare il progetto dell'applicazione host e il progetto del controllo Web nella stessa soluzione.  
  
2.  Nelle **Esplora soluzioni**, fare doppio clic su applicazione host e scegliere **Aggiungi riferimento**.  
  
3.  Aggiungere un riferimento al progetto del controllo Web.  
  
## <a name="see-also"></a>Vedere anche  
 [Applicazioni Web ASP.NET](../debugger/debugging-preparation-aspnet-web-applications.md)



