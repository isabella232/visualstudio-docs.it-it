---
title: 'Procedura: eseguire il debug di eccezioni ASP.NET | Microsoft Docs'
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
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ccd8c399bd92bd98307d44aff913c30390033c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205434"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Procedura: debug di eccezioni ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debug delle eccezioni è una parte importante dello sviluppo di una potente applicazione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Per informazioni generali sul debug delle eccezioni, è possibile [gestire le eccezioni con il debugger](../debugger/managing-exceptions-with-the-debugger.md).  
  
 Per eseguire il debug di eccezioni [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] non gestite, è necessario assicurarsi che il debugger si interrompa ogni volta che ne raggiunge una. Il runtime di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] dispone di un gestore eccezioni di livello superiore. Di conseguenza, per impostazione predefinita il debugger non si interrompe mai in corrispondenza di eccezioni non gestite. Per interrompere il debugger quando viene generata un'eccezione, è necessario selezionare l'impostazione **Interrompi quando un'eccezione è: Generata** per tale eccezione nella finestra di dialogo **Eccezioni**.  
  
 Se Just My Code è attivato, la selezione dell'opzione **Interrompi quando un'eccezione è: Generata** non comporta l'interruzione immediata del debugger quando un'eccezione viene generata in un metodo .NET Framework o in un altro codice di sistema. Invece l'esecuzione continua sino al raggiungimento di codice non di sistema, quindi si interrompe. Non è pertanto necessario eseguire il codice di sistema quando si verifica un'eccezione.  
  
 Just My Code offre un'altra opzione che può rivelarsi molto utile: **Interrompi quando un'eccezione è: Non gestita dall'utente**. Se si sceglie questa impostazione per un'eccezione, il debugger interromperà l'esecuzione nel codice utente, ma solo se l'eccezione non viene intercettata e gestita dal codice utente. Questa impostazione annulla l'effetto del gestore eccezioni di primo livello di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], perché quest'ultimo si trova nel codice non utente.  
  
### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Per attivare il debug delle eccezioni ASP.NET con Just My Code  
  
1. Scegliere **Eccezioni** dal menu **Debug**.  
  
     Verrà visualizzata la finestra di dialogo **Eccezioni**.  
  
2. Nella riga **Eccezioni Common Language Runtime** selezionare **Generata** o **Non gestita dall'utente**.  
  
     Per utilizzare l'impostazione **Non gestita dall'utente**, è necessario attivare **Just My Code**.  
  
### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Procedure ottimali per la gestione delle eccezioni ASP.NET  
  
- Collocare blocchi `try … catch` attorno al codice che può generare eccezioni anticipabili e gestibili. Se, ad esempio, l'applicazione effettua chiamate a un servizio Web XML o direttamente a una SQL Server, il codice deve essere in **try... blocchi catch** poiché possono verificarsi numerose eccezioni.
