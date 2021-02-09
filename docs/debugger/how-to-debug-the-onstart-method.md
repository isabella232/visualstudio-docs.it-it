---
title: Eseguire il debug del metodo OnStart | Microsoft Docs
description: Informazioni su come eseguire il debug del metodo OnStart di un servizio Windows in Visual Studio, avviando il debugger dall'interno del metodo.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 51096d7a47de80be7434659936165ba0a29f7c67
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899294"
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

    ![Screenshot della finestra di dialogo debugger JIT di Visual Studio in cui viene visualizzata un'eccezione .NET Framework non gestita nel WindowsService-Asis.exe.](../debugger/media/onstartdebug.png)

3. Selezionare **Sì, debug \<service name> .**

4. Nella finestra Debugger JIT di Visual Studio selezionare la versione di Visual Studio da usare per il debug.

    ![Screenshot di una finestra del debugger JIT di Visual Studio con ' nuova istanza di Microsoft Visual Studio 2015' selezionata nell'elenco dei debugger possibili.](../debugger/media/justintimedebugger.png)

5. Viene avviata una nuova istanza di Visual Studio e l'esecuzione viene arrestata in corrispondenza del metodo `Debugger.Launch()` .

## <a name="see-also"></a>Vedi anche
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
