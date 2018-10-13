---
title: 'Procedura: specificare una versione di .NET Framework per il debug | Microsoft Docs'
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
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 914c4bfb58485bd1d423e58bbe8fc8ab7f1a898a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49272961"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Procedura: specificare una versione di .NET Framework per il debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debugger di [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] supporta il debug delle versioni precedenti di Microsoft [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], oltre che della versione corrente. Se si avvia un'applicazione da Visual Studio, il debugger può identificare sempre la versione corretta del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] per l'applicazione si esegue il debug. Se l'applicazione è già in esecuzione e si utilizza **collegarsi**, il debugger potrebbe non essere sempre in grado di identificare una versione precedente del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. In questo caso, verrà visualizzato un messaggio di errore simile al seguente:  
  
 Il debugger ha interpretato erroneamente la versione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] che verrà utilizzata dall'applicazione.  
  
 In questi rari casi, è possibile impostare una chiave del Registro di sistema per indicare al debugger quale versione utilizzare.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Per specificare una versione di .NET Framework per il debug  
  
1.  Cercare nella directory Windows\Microsoft.NET\Framework le versioni di .NET Framework installate nel computer. I numeri di versione saranno simili al seguente:  
  
     `V1.1.4322`  
  
     Identificare il numero di versione corretto e annotarlo.  
  
2.  Avviare il **dell'Editor del Registro di sistema** (regedit).  
  
3.  Nel **dell'Editor del Registro di sistema**, aprire la cartella HKEY_LOCAL_MACHINE.  
  
4.  Passare a: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Se la chiave non esiste, fare doppio clic su HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine e scegliere **nuova chiave**. Denominare la nuova chiave `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5.  Dopo l'accesso a {449EC4CC-30D2-4032-9256-EE18EB41B62B}, esaminare i **nome** colonna e chiave CLRVersionForDebugging.  
  
    1.  Se la chiave non esiste, fare doppio clic su {449EC4CC-30D2-4032-9256-EE18EB41B62B} e fare clic su **nuovo valore stringa**. Quindi fare clic su nuovo valore stringa, fare clic su **rinominare**e il tipo `CLRVersionForDebugging`.  
  
6.  Fare doppio clic su **CLRVersionForDebugging**.  
  
7.  Nel **Modifica stringa** , digitare il numero di versione di .NET Framework le **valore** casella. Ad esempio: V1.1.4322  
  
8.  Fare clic su **OK**.  
  
9. Chiudi il **dell'Editor del Registro di sistema**.  
  
     Se all'avvio del debug viene di nuovo visualizzato un messaggio di errore, verificare di avere immesso il numero di versione corretto nel Registro di sistema. Verificare inoltre che la versione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] in uso sia supportata da Visual Studio. Il debugger è compatibile con la versione di .NET Framework corrente e le versioni precedenti, ma potrebbe non essere compatibile con le versioni future.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)



