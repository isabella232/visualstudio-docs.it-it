---
title: Modifica e continuazione (C++) | Microsoft Docs
description: Modifica e continuazione è disponibile per i progetti C++. Informazioni sulle modifiche supportate e su come controllare se e quando vengono applicate le modifiche.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 1f4bae68781cec00a61cb67f08450cc978418099
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122065725"
---
# <a name="edit-and-continue-c"></a>Modifica e continuazione (C++)
È possibile usare Modifica e continuazione nei progetti C++. Per informazioni sulle limitazioni di Modifica e continuazione, vedere Modifiche al codice supportate [(C++).](../debugger/supported-code-changes-cpp.md)

Per altre informazioni sui miglioramenti Visual Studio 2015 Update 3, vedere Modifica e continuazione [C++ in Visual Studio 2015 Update 3](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

 L'opzione del compilatore [/Zo (Enhance Optimized Debugging)](/cpp/build/reference/zo-enhance-optimized-debugging) introdotta in Visual Studio 2013 Update 3 aggiunge altre informazioni ai file PDB (symbol) per i file binari compilati senza l'opzione [/Od (Disable (Debug))](/cpp/build/reference/od-disable-debug).

 **/Zo** disabilita Modifica e continuazione. Vedere [Procedura: Eseguire il debug di codice ottimizzato](../debugger/how-to-debug-optimized-code.md).

## <a name="enable-or-disable-edit-and-continue"></a><a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Abilitare o disabilitare Modifica e continuazione
 È consigliabile disabilitare la chiamata automatica di Modifica e continuazione se si apportano modifiche al codice che non si vuole applicare durante la sessione di debug corrente. È anche possibile riabilitare la chiamata automatica di Modifica e continuazione.

> [!IMPORTANT]
> Per le impostazioni di compilazione necessarie e altre informazioni sulla compatibilità delle funzionalità, vedere Modifica e continuazione [in C++ in Visual Studio 2015 Update 3.](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/)

1. Se si è in una sessione di debug, arrestare il debug (**MAIUSC + F5**).

2. Scegliere **Opzioni** dal menu **Strumenti**.

3. Nella finestra **di dialogo** Opzioni selezionare Debug **> Generale**.

4. Per abilitare , selezionare **Abilita Modifica e continuazione**. Per disabilitare, deselezionare la casella di controllo.

5. Nel gruppo **Modifica e continuazione** selezionare o deselezionare la casella di controllo **Abilita Modifica e continuazione nativo** .

   La modifica di questa impostazione influisce su tutti i progetti attivi. Non è necessario ricompilare l'applicazione dopo la modifica di questa impostazione. Se si compila l'applicazione dalla riga di comando o da un makefile, ma si esegue il debug nell'ambiente Visual Studio, è comunque possibile usare Modifica e continuazione se si imposta **l'opzione /ZI.**

## <a name="how-to-apply-code-changes-explicitly"></a><a name="BKMK_How_to_apply_code_changes_explicitly"></a> Come applicare modifiche al codice in modo esplicito
 In C++, Modifica e continuazione può applicare le modifiche al codice in due modi. in modo implicito, quando si sceglie un comando di esecuzione, o in modo esplicito, quando si usa il comando **Applica modifiche del codice** .

 Quando si applicano modifiche al codice in modo esplicito, il programma rimane in modalità di interruzione e non viene eseguito.

- Per applicare le modifiche al codice in modo esplicito, nel menu **Debug** scegliere **Applica modifiche del codice**.

## <a name="how-to-stop-code-changes"></a><a name="BKMK_How_to_stop_code_changes"></a> Come arrestare le modifiche al codice
 In Modifica e continuazione è possibile scegliere di interrompere l'applicazione delle modifiche al codice.

 Per interrompere l'applicazione delle modifiche al codice:

- Nel menu **Debug** scegliere **Interrompi applicazione modifiche del codice**.

  Questa voce di menu viene visualizzata solo durante l'applicazione delle modifiche al codice.

  Se si sceglie questa opzione, non verrà completata nessuna delle modifiche del codice.

## <a name="how-to-reset-the-point-of-execution"></a><a name="BKMK_How_to_reset_the_point_of_execution"></a> Come reimpostare il punto di esecuzione
 Alcune modifiche al codice applicate in modalità Modifica e continuazione possono causare uno spostamento automatico del punto di esecuzione in una nuova posizione. Nonostante il punto di esecuzione venga collocato nel modo più accurato possibile, in alcuni casi il risultato potrebbe non essere corretto.

 In C++, una finestra di dialogo indica quando cambia il punto di esecuzione. Si consiglia di verificare che la posizione sia corretta prima di continuare con il debug. In caso negativo, usare il comando **Imposta istruzione successiva** . Per altre informazioni, vedere [Impostare l'istruzione successiva da eseguire](./navigating-through-code-with-the-debugger.md#BKMK_Set_the_next_statement_to_execute).

## <a name="how-to-work-with-stale-code"></a><a name="BKMK_How_to_work_with_stale_code"></a> Come usare il codice non aggiornato
 In alcuni casi la funzionalità Modifica e continuazione non consente di applicare immediatamente modifiche all'eseguibile, ma può apportare automaticamente tali modifiche in un secondo momento se si continua il debug. Ciò si verifica quando si modifica una funzione che chiama la funzione corrente o si aggiungono più di 64 byte di nuove variabili ad una funzione presente nello stack di chiamate.

 In questi casi, il debugger continua a eseguire il codice originale, fino a quando non è possibile applicare le modifiche. Il codice non aggiornato è visualizzato in una finestra del file di origine temporanea di una finestra di origine distinta, caratterizzata da un titolo simile a `enc25.tmp`. L'origine modificata continua ad essere visualizzata nella finestra di origine originale. Se si tenta di modificare il codice non aggiornato, viene visualizzato un messaggio di avviso.

## <a name="see-also"></a>Vedi anche
- [Modifiche al codice supportate (C++)](../debugger/supported-code-changes-cpp.md)