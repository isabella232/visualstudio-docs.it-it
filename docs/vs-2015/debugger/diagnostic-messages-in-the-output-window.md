---
title: Messaggi diagnostici nella finestra di Output | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.output
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 60f8da2430e1c84af3c26be31c6de561291c8c6e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65695292"
---
# <a name="diagnostic-messages-in-the-output-window"></a>Messaggi diagnostici nella finestra di output
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile scrivere messaggi di runtime nella finestra di output utilizzando la classe Debug o la classe Trace, che fanno entrambe parte della libreria di classi <xref:System.Diagnostics>. Utilizzare la classe Debug se si desidera generare l'output solo nella versione di debug del programma e la classe Trace se si desidera generare l'output sia nella versione di debug che in quella di rilascio del programma.  
  
## <a name="output-methods"></a>Metodi di output  
 Le classi <xref:System.Diagnostics.Trace> e <xref:System.Diagnostics.Debug> forniscono i seguenti metodi di output:  
  
- Diversi metodi `Write`, che generano informazioni senza interrompere l'esecuzione. Questi metodi sostituiscono il metodo `Debug.Print` utilizzato nelle versioni precedenti di Visual Basic.  
  
- I metodi <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> and <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, che interrompono l'esecuzione e generano informazioni se si verifica un errore relativo a una condizione specificata. Per impostazione predefinita, il metodo `Assert` visualizza le informazioni in una finestra di dialogo. Per ulteriori informazioni, vedere [Asserzioni nel metodo gestito](../debugger/assertions-in-managed-code.md).  
  
- I metodi <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, che interrompono sempre l'esecuzione e generano informazioni. Per impostazione predefinita, i metodi `Fail` visualizzano le informazioni in una finestra di dialogo.  
  
  Oltre a programma out dall'applicazione, il **Output** finestra possono essere visualizzate le informazioni riguardanti:  
  
- I moduli caricati o scaricati dal debugger.  
  
- Le eccezioni generate.  
  
- I processi chiusi.  
  
- I thread chiusi.  
  
## <a name="see-also"></a>Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Finestra di output](../ide/reference/output-window.md)   
 [Traccia e strumentazione di applicazioni](https://msdn.microsoft.com/library/773b6fc4-9013-4322-b728-5dec7a72e743)   
 [Introduzione alla strumentazione e alla traccia](https://msdn.microsoft.com/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debug di codice gestito](../debugger/debugging-managed-code.md)
