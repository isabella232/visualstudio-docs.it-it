---
title: 'Procedura: eseguire il debug del metodo OnStart | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7392b4185def34f38f0e183f2626bd648bb4b4ea
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350017"
---
# <a name="how-to-debug-the-onstart-method"></a>Procedura: eseguire il debug del metodo OnStart
È possibile eseguire il debug di un servizio Windows stesso avviando il servizio e connettendo il debugger al processo del servizio. Per altre informazioni, vedere [Procedura: Eseguire il debug di applicazioni di servizio per Windows](/dotnet/framework/windows-services/how-to-debug-windows-service-applications). Per eseguire il debug del metodo <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> di un servizio Windows, è tuttavia necessario avviare il debugger all'interno del metodo.

1. Aggiungere una chiamata a <xref:System.Diagnostics.Debugger.Launch%2A> all'inizio del metodo `OnStart()`.

    ```csharp
    protected override void OnStart(string[] args)
    {
        System.Diagnostics.Debugger.Launch();
    }
    ```

2. Avviare il servizio. È possibile usare `net start`o avviarlo nella finestra **Servizi** .

    Verrà visualizzata una finestra di dialogo analoga alla seguente:

    ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")

3. Selezionare **Sì, debug \<service name> .**

4. Nella finestra Debugger JIT di Visual Studio selezionare la versione di Visual Studio da usare per il debug.

    ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")

5. Viene avviata una nuova istanza di Visual Studio e l'esecuzione viene arrestata in corrispondenza del metodo `Debugger.Launch()` .

## <a name="see-also"></a>Vedi anche
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
