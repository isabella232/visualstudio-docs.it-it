---
title: Inviare i messaggi diagnostici nella finestra di Output | Microsoft Docs
ms.custom: ''
ms.date: 04/25/2017
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- diagnostic messages [C#]
- System.Diagnostics.Debug class, Output window
- messages, diagnostic
- Debug.Print replacements
- diagnosis
- Output window, diagnostic messages
- System.Diagnostics.Trace class, Output window
- Trace class, diagnostic messages
- diagnostics
- debugger, Output window
- debugging [Visual Studio], diagnostic messages in Output window
- Debug class
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 27cec31b775ba5f8d201c81cbd65f5b161353986
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252297"
---
# <a name="send-diagnostic-messages-to-the-output-window"></a>Inviare i messaggi diagnostici nella finestra di Output
È possibile scrivere messaggi in fase di esecuzione per il **Output** finestra utilizzando il <xref:System.Diagnostics.Debug> classe o il <xref:System.Diagnostics.Trace> classe, che fanno parte del <xref:System.Diagnostics> libreria di classi. Usare la <xref:System.Diagnostics.Debug> se è l'output solo nella classe la *Debug* versione del programma. Usare la <xref:System.Diagnostics.Trace> classe se si desidera che l'output in entrambi il *eseguire il Debug* e *versione* versioni.  
  
## <a name="output-methods"></a>Metodi di output  
 Le classi <xref:System.Diagnostics.Trace> e <xref:System.Diagnostics.Debug> forniscono i seguenti metodi di output:  
  
-   Diversi metodi `Write`, che generano informazioni senza interrompere l'esecuzione. Questi metodi sostituiscono il metodo `Debug.Print` utilizzato nelle versioni precedenti di Visual Basic.  
  
-   I metodi <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> and <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, che interrompono l'esecuzione e generano informazioni se si verifica un errore relativo a una condizione specificata. Per impostazione predefinita, il metodo `Assert` visualizza le informazioni in una finestra di dialogo. Per altre informazioni, vedere [asserzioni nel codice gestito](../debugger/assertions-in-managed-code.md).  
  
-   I metodi <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, che interrompono sempre l'esecuzione e generano informazioni. Per impostazione predefinita, i metodi `Fail` visualizzano le informazioni in una finestra di dialogo.  
  
 Oltre a programma out dall'applicazione, il **Output** finestra possono essere visualizzate le informazioni riguardanti:  
  
-   I moduli caricati o scaricati dal debugger.  
  
-   Le eccezioni generate.  
  
-   I processi chiusi.  
  
-   I thread chiusi.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Finestra di output](../ide/reference/output-window.md)   
 [Traccia e strumentazione di applicazioni](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)  
 [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debug di codice gestito](../debugger/debugging-managed-code.md)
