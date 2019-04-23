---
title: Modifica e continuazione (Visual C++) | Microsoft Docs
ms.date: 05/31/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9ff67be52c36050f513fc3ef6530a6bd81d8988d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60046670"
---
# <a name="edit-and-continue-visual-c"></a>Modifica e continuazione (Visual C++)
È possibile usare Modifica e continuazione nei progetti Visual C++. Visualizzare [modifiche di codice supportato (C++)](../debugger/supported-code-changes-cpp.md) per informazioni sulle limitazioni di modifica e continuazione.

Per altre informazioni sui miglioramenti apportati a Visual Studio 2015 Update 3, vedere [C++ Modifica e continuazione in Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

 L'opzione del compilatore [/Zo (Enhance Optimized Debugging)](/cpp/build/reference/zo-enhance-optimized-debugging) introdotta in Visual Studio 2013 Update 3 aggiunge altre informazioni ai file PDB (symbol) per i file binari compilati senza l'opzione [/Od (Disable (Debug))](https://msdn.microsoft.com/library/aafb762y.aspx).

 **/Zo** Disabilita modifica e continuazione. Vedere [How to: Eseguire il debug di codice ottimizzato](../debugger/how-to-debug-optimized-code.md).

## <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Abilitare o disabilitare Modifica e continuazione
 È consigliabile disabilitare la chiamata automatica di Modifica e continuazione se si apportano modifiche al codice che non si vuole applicare durante la sessione di debug corrente. È anche possibile riabilitare la chiamata automatica di Modifica e continuazione.

> [!IMPORTANT]
> Per altre informazioni sulla compatibilità tra funzionalità e le impostazioni di compilazione necessari, vedere [ C++ modifica e continuazione in Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

1. Se trovano in una sessione di debug, arrestare il debug (**MAIUSC+F5**).

2. Scegliere **Opzioni** dal menu **Strumenti**.

3. Nella finestra di dialogo **Opzioni** selezionare la cartella **Debug > Generale**.

4. Per abilitare, selezionare **Abilita modifica e continuazione**. Per disabilitare, deselezionare la casella di controllo.

5. Nel gruppo **Modifica e continuazione** selezionare o deselezionare la casella di controllo **Abilita Modifica e continuazione nativo** .

   La modifica di questa impostazione influisce su tutti i progetti attivi. Non è necessario ricompilare l'applicazione dopo la modifica di questa impostazione. Quando si compila l'applicazione dalla riga di comando o da un makefile, ma si esegue il debug nell'ambiente Visual Studio, è comunque possibile usare Modifica e continuazione se si imposta l'opzione **/ZI**.

## <a name="BKMK_How_to_apply_code_changes_explicitly"></a> Come applicare modifiche al codice in modo esplicito
 In Visual C++, Modifica e continuazione consente di applicare modifiche al codice in due modi: in modo implicito, quando si sceglie un comando di esecuzione, o in modo esplicito, quando si usa il comando **Applica modifiche del codice** .

 Quando si applicano modifiche al codice in modo esplicito, il programma rimane in modalità di interruzione e non viene eseguito.

- Per applicare le modifiche al codice in modo esplicito, nel menu **Debug** scegliere **Applica modifiche del codice**.

## <a name="BKMK_How_to_stop_code_changes"></a> Come interrompere l'applicazione delle modifiche al codice
 In Modifica e continuazione è possibile scegliere di interrompere l'applicazione delle modifiche al codice.

 Per interrompere l'applicazione delle modifiche al codice:

- Nel menu **Debug** scegliere **Interrompi applicazione modifiche del codice**.

  Questa voce di menu viene visualizzata solo durante l'applicazione delle modifiche al codice.

  Se si sceglie questa opzione, non verrà completata nessuna delle modifiche del codice.

## <a name="BKMK_How_to_reset_the_point_of_execution"></a> Come reimpostare il punto di esecuzione
 Alcune modifiche al codice applicate in modalità Modifica e continuazione possono causare uno spostamento automatico del punto di esecuzione in una nuova posizione. Nonostante il punto di esecuzione venga collocato nel modo più accurato possibile, in alcuni casi il risultato potrebbe non essere corretto.

 In Visual C++ la modifica del punto di esecuzione viene segnalata tramite una finestra di dialogo. Si consiglia di verificare che la posizione sia corretta prima di continuare con il debug. In caso negativo, usare il comando **Imposta istruzione successiva** . Per altre informazioni, vedere [Impostare l'istruzione successiva da eseguire](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).

## <a name="BKMK_How_to_work_with_stale_code"></a> Come usare il codice non aggiornato
 In alcuni casi la funzionalità Modifica e continuazione non consente di applicare immediatamente modifiche all'eseguibile, ma può apportare automaticamente tali modifiche in un secondo momento se si continua il debug. Ciò si verifica quando si modifica una funzione che chiama la funzione corrente o si aggiungono più di 64 byte di nuove variabili ad una funzione presente nello stack di chiamate.

 In questi casi, il debugger continua a eseguire il codice originale, fino a quando non è possibile applicare le modifiche. Il codice non aggiornato è visualizzato in una finestra del file di origine temporanea di una finestra di origine distinta, caratterizzata da un titolo simile a `enc25.tmp`. L'origine modificata continua ad essere visualizzata nella finestra di origine originale. Se si tenta di modificare il codice non aggiornato, viene visualizzato un messaggio di avviso.

## <a name="see-also"></a>Vedere anche
- [Modifiche al codice supportate (C++)](../debugger/supported-code-changes-cpp.md)