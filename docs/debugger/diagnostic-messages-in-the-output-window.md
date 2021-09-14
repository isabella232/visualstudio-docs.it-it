---
title: Inviare messaggi alla finestra Output | Microsoft Docs
description: Scrivere messaggi di runtime nella finestra Output Visual Studio usando la classe Debug o la classe Trace, che fanno parte della libreria di classi System.Diagnostics.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: c7ec9cfa05be11cb17e5a6ed6d768e1335cf5860
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709923"
---
# <a name="send-messages-to-the-output-window"></a>Inviare messaggi alla finestra di output

È possibile scrivere messaggi di runtime nella **finestra Output** usando la classe o la classe , che fanno parte della libreria <xref:System.Diagnostics.Debug> di <xref:System.Diagnostics.Trace> <xref:System.Diagnostics> classi. Usare la <xref:System.Diagnostics.Debug> classe se si vuole solo l'output nella versione *di* debug del programma. Usare la <xref:System.Diagnostics.Trace> classe se si desidera che l'output sia nelle versioni di *debug* *che di* versione.

## <a name="output-methods"></a>Metodi di output
 Le classi <xref:System.Diagnostics.Trace> e <xref:System.Diagnostics.Debug> forniscono i seguenti metodi di output:

- Diversi metodi `Write`, che generano informazioni senza interrompere l'esecuzione. Questi metodi sostituiscono il metodo `Debug.Print` utilizzato nelle versioni precedenti di Visual Basic.

- <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> metodi <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName> e , che interrompno l'esecuzione e le informazioni di output se una condizione specificata ha esito negativo. Per impostazione predefinita, il metodo `Assert` visualizza le informazioni in una finestra di dialogo. Per altre informazioni, vedere [Asserzioni nel metodo gestito](../debugger/assertions-in-managed-code.md).

- I <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> metodi e , che <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName> interrompno sempre l'esecuzione e le informazioni di output. Per impostazione predefinita, i metodi `Fail` visualizzano le informazioni in una finestra di dialogo.

La **finestra Output** può anche visualizzare informazioni su:

- I moduli caricati o scaricati dal debugger.

- Le eccezioni generate.

- I processi chiusi.

- I thread chiusi.

## <a name="see-also"></a>Vedi anche
- [Sicurezza del debugger](../debugger/debugger-security.md)
- [Output (finestra)](../ide/reference/output-window.md)
- [Traccia e strumentazione di applicazioni](/dotnet/framework/debug-trace-profile/tracing-and-instrumenting-applications)
- [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Debug di codice gestito](../debugger/debugging-managed-code.md)
