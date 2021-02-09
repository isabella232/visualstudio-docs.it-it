---
title: Eccezioni di debug ASP.NET | Microsoft Docs
Description: Informazioni su come configurare in modo che il debugger si arresti per le eccezioni non gestite nell'applicazione ASP.NET. È possibile assicurarsi che l'interruzioni avvenga nel codice non di sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- aspnet
ms.openlocfilehash: 00823fd1a5029cb45b91a6beb4168f8a9cbd999a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99913254"
---
# <a name="how-to-debug-aspnet-exceptions"></a>Procedura: debug di eccezioni ASP.NET
Il debug delle eccezioni è una parte importante dello sviluppo di una potente applicazione [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Per informazioni generali sul debug delle eccezioni, è possibile [gestire le eccezioni con il debugger](../debugger/managing-exceptions-with-the-debugger.md).

 Per eseguire il debug di eccezioni [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] non gestite, è necessario assicurarsi che il debugger si interrompa ogni volta che ne raggiunge una. Il runtime di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] dispone di un gestore eccezioni di livello superiore. Di conseguenza, per impostazione predefinita il debugger non si interrompe mai in corrispondenza di eccezioni non gestite. Per interrompere il debugger quando viene generata un'eccezione, è necessario selezionare l'impostazione **Interrompi quando un'eccezione è: Generata** per tale eccezione nella finestra di dialogo **Eccezioni**.

 Se è stato abilitato Just My Code, **Interrompi quando un'eccezione è: generata** non comporta l'interruzione immediata del debugger se viene generata un'eccezione in un metodo .NET o in un altro codice di sistema. Invece l'esecuzione continua sino al raggiungimento di codice non di sistema, quindi si interrompe. Non è pertanto necessario eseguire il codice di sistema quando si verifica un'eccezione.

 Just My Code offre un'altra opzione che può rivelarsi molto utile: **Interrompi quando un'eccezione è: Non gestita dall'utente**. Se si sceglie questa impostazione per un'eccezione, il debugger interromperà l'esecuzione nel codice utente, ma solo se l'eccezione non viene intercettata e gestita dal codice utente. Questa impostazione annulla l'effetto del gestore eccezioni di primo livello di [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], perché quest'ultimo si trova nel codice non utente.

### <a name="to-enable-debugging-of-aspnet-exceptions-with-just-my-code"></a>Per attivare il debug delle eccezioni ASP.NET con Just My Code

1. Scegliere **Eccezioni** dal menu **Debug**.

     Verrà visualizzata la finestra di dialogo **Eccezioni**.

2. Nella riga **Eccezioni Common Language Runtime** selezionare **Generata** o **Non gestita dall'utente**.

     Per utilizzare l'impostazione **Non gestita dall'utente**, è necessario attivare **Just My Code**.

### <a name="to-use-best-practices-for-aspnet-exception-handling"></a>Procedure ottimali per la gestione delle eccezioni ASP.NET

- Collocare blocchi `try ... catch` attorno al codice che può generare eccezioni anticipabili e gestibili. Se, ad esempio, l'applicazione effettua chiamate a un Servizio Web XML o direttamente a SQL Server, il codice dovrebbe trovarsi in blocchi **try ... catch** perché è possibile che si verifichino numerose eccezioni.

## <a name="see-also"></a>Vedi anche
- [Eseguire il debug di applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)