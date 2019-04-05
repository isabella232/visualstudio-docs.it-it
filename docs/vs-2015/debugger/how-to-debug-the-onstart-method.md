---
title: 'Procedura: Eseguire il debug del metodo OnStart | Microsoft Docs'
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
- OnStart method
- debugging [Visual Studio], Windows services
- debugging managed code, OnStart method
- debugging Windows Services applications, OnStart method
- Windows Service applications, debugging
ms.assetid: b06b5d65-424b-490f-bf58-97583cd7006a
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d77d06e720ebe9146f907d8868c46c94addd5d99
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966477"
---
# <a name="how-to-debug-the-onstart-method"></a>Procedura: Eseguire il debug del metodo OnStart
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile eseguire il debug di un servizio Windows stesso avviando il servizio e connettendo il debugger al processo del servizio. Per altre informazioni, vedere [Procedura: Eseguire il debug di applicazioni di servizio di Windows](http://msdn.microsoft.com/library/63ab0800-0f05-4f1e-88e6-94c73fd920a2). Per eseguire il debug del metodo <xref:System.ServiceProcess.ServiceBase.OnStart%2A?displayProperty=fullName> di un servizio Windows, è tuttavia necessario avviare il debugger all'interno del metodo.  
  
1.  Aggiungere una chiamata a <xref:System.Diagnostics.Debugger.Launch%2A> all'inizio del metodo `OnStart()`.  
  
    ```csharp  
    protected override void OnStart(string[] args)  
    {  
        System.Diagnostics.Debugger.Launch();  
     }  
    ```  
  
2.  Avviare il servizio. È possibile usare `net start`o avviarlo nella finestra **Servizi** .  
  
     Verrà visualizzata una finestra di dialogo analoga alla seguente:  
  
     ![OnStartDebug](../debugger/media/onstartdebug.png "OnStartDebug")  
  
3.  Selezionare **Sì, esegui il debug di \<nome servizio>.**  
  
4.  Nella finestra Debugger JIT di Visual Studio selezionare la versione di Visual Studio da usare per il debug.  
  
     ![JustInTimeDebugger](../debugger/media/justintimedebugger.png "JustInTimeDebugger")  
  
5.  Viene avviata una nuova istanza di Visual Studio e l'esecuzione viene arrestata in corrispondenza del metodo `Debugger.Launch()` .  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Debug di codice gestito](../debugger/debugging-managed-code.md)
