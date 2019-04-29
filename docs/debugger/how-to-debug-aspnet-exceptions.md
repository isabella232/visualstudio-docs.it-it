---
title: 'Procedura: Debug di eccezioni ASP.NET | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], ASP.NET exceptions
- ASP.NET, exceptions
- exceptions, ASP.NET
ms.assetid: 1810096e-de8c-435e-be3d-f365d0cd0a6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- aspnet
ms.openlocfilehash: 6a9c6d2c2159ca21f227beb2f8bd1a98b9420328
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62894339"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Procedura: Eseguire il debug di eccezioni ASP.NET
Il debug delle eccezioni è una parte importante dello sviluppo di una potente applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Informazioni generali su come eseguire il debug di eccezioni, vedere [la gestione delle eccezioni con il Debugger](../debugger/managing-exceptions-with-the-debugger.md).

 Per eseguire il debug di eccezioni [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non gestite, è necessario assicurarsi che il debugger si interrompa ogni volta che ne raggiunge una. Il runtime di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dispone di un gestore eccezioni di livello superiore. Di conseguenza, per impostazione predefinita il debugger non si interrompe mai in corrispondenza di eccezioni non gestite. Per interrompere il debugger quando viene generata un'eccezione, è necessario selezionare **Interrompi quando un'eccezione è: Generata** impostazione per tale eccezione nella **eccezioni** nella finestra di dialogo.

 Se è stato abilitato Just My Code, **Interrompi quando un'eccezione è: Generata** non causa il debugger per interrompere immediatamente se viene generata un'eccezione in un metodo .NET Framework o altro codice di sistema. Invece l'esecuzione continua sino al raggiungimento di codice non di sistema, quindi si interrompe. Non è pertanto necessario eseguire il codice di sistema quando si verifica un'eccezione.

 Just My Code fornisce un'altra opzione che può rivelarsi molto utile: **Interrompi quando un'eccezione è: User-unhandled**. Se si sceglie questa impostazione per un'eccezione, il debugger interromperà l'esecuzione nel codice utente, ma solo se l'eccezione non viene intercettata e gestita dal codice utente. Questa impostazione annulla l'effetto del gestore eccezioni di primo livello di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], perché quest'ultimo si trova nel codice non utente.

### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Per attivare il debug delle eccezioni ASP.NET con Just My Code

1. Scegliere **Eccezioni** dal menu **Debug**.

     Verrà visualizzata la finestra di dialogo **Eccezioni**.

2. Nella riga **Eccezioni Common Language Runtime** selezionare **Generata** o **Non gestita dall'utente**.

     Per utilizzare l'impostazione **Non gestita dall'utente**, è necessario attivare **Just My Code**.

### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Procedure ottimali per la gestione delle eccezioni ASP.NET

- Collocare blocchi `try ... catch` attorno al codice che può generare eccezioni anticipabili e gestibili. Se, ad esempio, l'applicazione effettua chiamate a un Servizio Web XML o direttamente a SQL Server, il codice dovrebbe trovarsi in blocchi **try ... catch** perché è possibile che si verifichino numerose eccezioni.

## <a name="see-also"></a>Vedere anche
- [Eseguire il debug di applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)