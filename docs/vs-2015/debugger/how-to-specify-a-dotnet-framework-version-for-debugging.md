---
title: 'Procedura: Specificare una versione di .NET Framework per il debug | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4c785c419ead31ad90e2b20ae7f48af778598bb6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68176566"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging"></a>Procedura: Specificare una versione di .NET Framework per il debug
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debugger di [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] supporta il debug delle versioni precedenti di Microsoft [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], oltre che della versione corrente. Se un'applicazione viene avviata da Visual Studio, il debugger è sempre in grado di identificare la versione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] corretta per l'applicazione di cui è in corso il debug. Se l'applicazione è già in esecuzione e si utilizza **collegarsi**, il debugger potrebbe non essere sempre in grado di identificare una versione precedente del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. In questo caso, verrà visualizzato un messaggio di errore simile al seguente:  
  
 Il debugger ha interpretato erroneamente la versione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] che verrà utilizzata dall'applicazione.  
  
 In questi rari casi, è possibile impostare una chiave del Registro di sistema per indicare al debugger quale versione utilizzare.  
  
### <a name="to-specify-a-net-framework-version-for-debugging"></a>Per specificare una versione di .NET Framework per il debug  
  
1. Cercare nella directory Windows\Microsoft.NET\Framework le versioni di .NET Framework installate nel computer. I numeri di versione saranno simili al seguente:  
  
     `V1.1.4322`  
  
     Identificare il numero di versione corretto e annotarlo.  
  
2. Avviare l'**editor del Registro di sistema** (regedit).  
  
3. Nell'**editor del Registro di sistema** aprire la cartella HKEY_LOCAL_MACHINE.  
  
4. Passare a: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine\\{449EC4CC-30D2-4032-9256-EE18EB41B62B}  
  
     Se la chiave non esiste, fare clic con il pulsante destro del mouse su HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine e scegliere **Nuova chiave**. Denominare la nuova chiave `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.  
  
5. Dalla chiave {449EC4CC-30D2-4032-9256-EE18EB41B62B}, cercare la chiave CLRVersionForDebugging nella colonna **Nome**.  
  
    1. Se la chiave non esiste, fare clic con il pulsante destro del mouse su {449EC4CC-30D2-4032-9256-EE18EB41B62B} e scegliere **Nuovo Valore stringa**. Quindi fare clic su nuovo valore stringa, fare clic su **rinominare**e il tipo `CLRVersionForDebugging`.  
  
6. Fare doppio clic su **CLRVersionForDebugging**.  
  
7. Digitare il numero di versione di .NET Framework nella casella **Valore** della casella **Modifica stringa**. Ad esempio: V1.1.4322  
  
8. Fare clic su **OK**.  
  
9. Chiudere l'**editor del Registro di sistema**.  
  
     Se all'avvio del debug viene di nuovo visualizzato un messaggio di errore, verificare di avere immesso il numero di versione corretto nel Registro di sistema. Verificare inoltre che la versione di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] in uso sia supportata da Visual Studio. Il debugger è compatibile con la versione di .NET Framework corrente e le versioni precedenti, ma potrebbe non essere compatibile con le versioni future.  
  
## <a name="see-also"></a>Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)
