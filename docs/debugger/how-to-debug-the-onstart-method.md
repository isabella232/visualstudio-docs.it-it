---
title: Eseguire il debug del metodo OnStart | Microsoft Docs
description: Informazioni su come eseguire il debug del metodo OnStart di un servizio Windows in Visual Studio, avviando il debugger dall'interno del metodo .
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 995470a5156850bf789a233b2629a41859585440
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627995"
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

    ![Screenshot di una Visual Studio finestra di dialogo Debugger JUST-In-Time che mostra un'eccezione di .NET Framework non gestita che si è verificata WindowsService-Asis.exe.](../debugger/media/onstartdebug.png)

3. Selezionare **Sì, esegui il \<service name> debug.**

4. Nella finestra Debugger JIT di Visual Studio selezionare la versione di Visual Studio da usare per il debug.

    ![Screenshot di una finestra Visual Studio debugger JUST-In-Time con l'opzione "Nuova istanza di Microsoft Visual Studio 2015" selezionata nell'elenco dei possibili debugger.](../debugger/media/justintimedebugger.png)

5. Viene avviata una nuova istanza di Visual Studio e l'esecuzione viene arrestata in corrispondenza del metodo `Debugger.Launch()` .

## <a name="see-also"></a>Vedi anche
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
