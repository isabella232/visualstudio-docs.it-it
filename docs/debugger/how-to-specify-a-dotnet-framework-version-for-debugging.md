---
title: Specificare una versione di .NET Framework per eseguire il debug | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: bfe17100fcdcb0d475a7467233caa51ba7895225
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747479"
---
# <a name="how-to-specify-a-net-framework-version-for-debugging-c-visual-basic-f"></a>Procedura: Specificare una versione di .NET Framework per il debug (C#, Visual Basic, F#)

Il debugger di Visual Studio supporta il debug di versioni precedenti di Microsoft .NET Framework, nonché la versione corrente. Se si avvia un'applicazione da Visual Studio, il debugger può identificare sempre la versione corretta di .NET Framework per l'applicazione che si esegue il debug. Tuttavia, se l'applicazione è già in esecuzione e si avvia il debug usando **Collega a**, il debugger potrebbe non essere sempre in grado di identificare una versione precedente di .NET Framework. In questo caso, verrà visualizzato un messaggio di errore simile al seguente:

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

In rari casi in cui viene visualizzato questo errore, è possibile impostare una chiave del Registro di sistema per indicare al debugger quale versione usare.

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

     Se all'avvio del debug viene di nuovo visualizzato un messaggio di errore, verificare di avere immesso il numero di versione corretto nel Registro di sistema. Verificare inoltre che si usa una versione di .NET Framework supportata da Visual Studio. Il debugger è compatibile con la versione di .NET Framework corrente e le versioni precedenti, ma potrebbe non essere compatibile con le versioni future.

## <a name="see-also"></a>Vedere anche
- [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)