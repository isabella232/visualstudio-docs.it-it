---
title: Inviare messaggi alla finestra di output | Microsoft Docs
ms.date: 11/08/2018
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 85d3c146775ac06b3118186738ee74932a4c452a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350472"
---
# <a name="send-messages-to-the-output-window"></a>Inviare messaggi alla finestra di output

È possibile scrivere messaggi di runtime nella finestra di **output** usando la <xref:System.Diagnostics.Debug> classe o la <xref:System.Diagnostics.Trace> classe, che fa parte della libreria di <xref:System.Diagnostics> classi. Utilizzare la <xref:System.Diagnostics.Debug> classe se si desidera solo l'output nella versione di *debug* del programma. Utilizzare la <xref:System.Diagnostics.Trace> classe se si desidera l'output in entrambe le versioni di *debug* e di *rilascio* .

## <a name="output-methods"></a>Metodi di output
 Le classi <xref:System.Diagnostics.Trace> e <xref:System.Diagnostics.Debug> forniscono i seguenti metodi di output:

- Diversi metodi `Write`, che generano informazioni senza interrompere l'esecuzione. Questi metodi sostituiscono il metodo `Debug.Print` utilizzato nelle versioni precedenti di Visual Basic.

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName><xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>metodi e, che interrompono l'esecuzione e le informazioni di output se una condizione specificata ha esito negativo. Per impostazione predefinita, il metodo `Assert` visualizza le informazioni in una finestra di dialogo. Per altre informazioni, vedere [Asserzioni nel metodo gestito](../debugger/assertions-in-managed-code.md).

- I <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> metodi e, che interrompono sempre le informazioni di esecuzione e di output. Per impostazione predefinita, i metodi `Fail` visualizzano le informazioni in una finestra di dialogo.

La finestra **output** consente inoltre di visualizzare informazioni su:

- I moduli caricati o scaricati dal debugger.

- Le eccezioni generate.

- I processi chiusi.

- I thread chiusi.

## <a name="see-also"></a>Vedere anche
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Output (finestra)](../ide/reference/output-window.md)
- [Traccia e strumentazione di applicazioni](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Tipi di progetto C#, F # e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Debug del codice gestito](../debugger/debugging-managed-code.md)
