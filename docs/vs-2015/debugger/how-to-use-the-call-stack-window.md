---
title: 'Procedura: utilizzare la finestra stack di chiamate | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.callstack
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- aspx
helpviewer_keywords:
- threading [Visual Studio], displaying calls to or from
- functions [debugger], viewing code on call stack
- disassembly code
- breakpoints, Call Stack window
- debugging [Visual Studio], switching to another stack frame
- debugging [Visual Studio], Call Stack window
- Call Stack window, viewing source code for functions on the call stack
- stack, switching stack frames
- Call Stack window, viewing disassembly code for functions on the call stack
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 84c0bfead1633da13b4284cad04ace674045b057
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697480"
---
# <a name="how-to-use-the-call-stack-window"></a>Procedura: utilizzare la finestra Stack di chiamate
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tramite la finestra **Stack di chiamate** è possibile visualizzare le chiamate di funzione o di routine attualmente presenti nello stack.  
  
 Nella finestra **stack di chiamate** vengono visualizzati il nome di ogni funzione e il linguaggio di programmazione in cui è scritto. Il nome della funzione o della procedura può essere seguito da informazioni facoltative quali il nome del modulo, il numero di riga, oltre a nomi, tipi e valori di parametri. La visualizzazione di queste informazioni opzionali può essere attivata o disattivata.  
  
 Lo stack frame in cui è attualmente posizionato il puntatore di esecuzione è contraddistinto da una freccia gialla. Per impostazione predefinita, si tratta del frame le cui informazioni vengono visualizzate nelle finestre di origine, **Disassembly**, **variabili locali**, **espressioni di controllo**e **auto** . Se si desidera modificare il contesto in un altro frame dello stack, è possibile eseguire questa operazione nella finestra **stack di chiamate** .  
  
 Quando i simboli di debug non sono disponibili per una parte di uno stack di chiamate, la finestra **stack di chiamate** potrebbe non essere in grado di visualizzare le informazioni corrette per tale parte dello stack di chiamate. Verrà visualizzata la notazione seguente:  
  
 [I frame indicati di seguito possono essere errati e/o mancanti, non sono stati caricati simboli per nome.dll]  
  
 Nel codice gestito, per impostazione predefinita. la finestra **stack di chiamate** nasconde le informazioni per il codice non utente. Di seguito è riportata la notazione visualizzata in sostituzione delle informazioni nascoste:  
  
 **[\<External Code>]**  
  
 Per codice non utente si intende qualsiasi codice diverso da "My Code". Per visualizzare le informazioni sullo stack di chiamate per il codice non utente, utilizzare il menu di scelta rapida.  
  
 Utilizzando il menu di scelta rapida, è possibile scegliere se visualizzare o meno le chiamate tra thread.  
  
> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti**. Per altre informazioni, vedere [personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-call-stack-window-in-break-mode-or-in-run-mode"></a>Per visualizzare la finestra Stack di chiamate in modalità di interruzione o di esecuzione  
  
- Scegliere **finestre** dal menu **debug** , quindi fare clic su **stack di chiamate**.  
  
### <a name="to-change-the-optional-information-displayed"></a>Per scegliere quali informazioni opzionali visualizzare  
  
- Fare clic con il pulsante destro del mouse sulla finestra **stack di chiamate** e impostare o deselezionare **Mostra \<**_the information that you want_**> **.  
  
### <a name="to-display-non-user-code-frames-in-the-call-stack-window"></a>Per visualizzare i frame del codice non utente nella finestra Stack di chiamate  
  
- Fare clic con il pulsante destro del mouse sulla finestra **Stack di chiamate** e selezionare **Mostra codice esterno**.  
  
### <a name="to-switch-to-another-stack-frame"></a>Per passare a un altro stack frame  
  
1. Nella finestra **stack di chiamate** fare clic con il pulsante destro del mouse sul frame di cui si desidera visualizzare il codice e i dati.  
  
2. Selezionare **Passa al frame**.  
  
     Accanto al frame selezionato verrà visualizzata una freccia verde ricurva. Il puntatore di esecuzione rimarrà nel frame originale, sempre contrassegnato dalla freccia gialla. Se si sceglie **Esegui** o **Continua** dal menu **Debug**, l'esecuzione continuerà nel frame originale, non nel frame selezionato.  
  
### <a name="to-display-calls-to-or-from-another-thread"></a>Per visualizzare le chiamate da o verso altri thread  
  
- Fare clic con il pulsante destro del mouse sulla finestra **Stack di chiamate** e selezionare **Includi chiamate da e verso altri thread**.  
  
### <a name="to-view-the-source-code-for-a-function-on-the-call-stack"></a>Per visualizzare il codice sorgente di una funzione dello stack di chiamate  
  
- Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse sulla funzione della quale si vuole esaminare il codice sorgente e selezionare **Vai a codice sorgente**.  
  
### <a name="to-visually-trace-the-call-stack"></a>Per rilevare visivamente lo stack di chiamate  
  
1. Nella finestra **Stack di chiamate** aprire il menu di scelta rapida. Scegliere **Mostra stack di chiamate nella mappa codici**. (Tastiera: **CTRL**  +  **Sposta**  +  **`**  
  
     Vedere [eseguire il mapping dei metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### <a name="to-view-the-disassembly-code-for-a-function-on-the-call-stack"></a>Per visualizzare il codice disassembly di una funzione dello stack di chiamate  
  
- Nella finestra **Stack di chiamate** fare clic con il pulsante destro del mouse sulla funzione della quale si desidera esaminare il codice del disassembly e selezionare **Vai a disassembly**.  
  
### <a name="to-run-to-a-specific-function-from-the-call-stack-window"></a>Per eseguire una funzione specifica dalla finestra Stack di chiamate  
  
- Nella finestra **stack di chiamate** selezionare la funzione, fare clic con il pulsante destro del mouse e scegliere **Esegui fino al cursore**.  
  
### <a name="to-set-a-breakpoint-on-the-exit-point-of-a-function-call"></a>Per impostare un punto di interruzione in corrispondenza del punto di uscita di una chiamata di funzione  
  
- Vedere [impostare un punto di interruzione in una funzione dello stack di chiamate](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_in_the_call_stack_window).  
  
### <a name="to-load-symbols-for-a-module"></a>Per caricare i simboli per un modulo  
  
- Nella finestra **stack di chiamate** fare clic con il pulsante destro del mouse sul frame che mostra il modulo di cui si desidera ricaricare i simboli e selezionare **Carica simboli**.  
  
## <a name="loading-symbols"></a>Caricamento dei simboli  
 Nella finestra **Stack di chiamate** è possibile caricare i simboli di debug per un codice che non ne dispone. Questi simboli possono essere simboli di sistema o .NET Framework scaricati dai server dei simboli pubblici Microsoft o simboli contenuti in un percorso nel computer del quale si esegue il debug.  
  
 Vedere [Specificare file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols"></a>Per caricare i simboli  
  
1. Nella finestra **stack di chiamate** fare clic con il pulsante destro del mouse sul frame per il quale non sono caricati i simboli. Il frame verrà disattivato (rappresentato in grigio).  
  
2. Scegliere **Carica simboli da** , quindi fare clic su server dei simboli **Microsoft** o **percorso simboli**.  
  
#### <a name="to-set-the-symbol-path"></a>Per impostare il percorso dei simboli  
  
1. Nella finestra **Stack di chiamate** scegliere **Impostazioni simboli** nel menu di scelta rapida.  
  
     Viene visualizzata la finestra di dialogo **Opzioni** con la pagina **Simboli**.  
  
2. Fare clic su **Impostazioni simboli**.  
  
3. Nella finestra di dialogo **Opzioni** fare clic sull'icona della cartella.  
  
     Viene visualizzato un cursore nella casella **Percorsi dei file di simboli (pdb)**.  
  
4. Digitare il percorso di directory del simbolo sul computer del quale si esegue il debug. Per il debug locale, è il computer locale. Per il debug remoto, è il computer remoto.  
  
5. Fare clic su **OK** per chiudere la finestra di dialogo **Opzioni** .  
  
## <a name="see-also"></a>Vedere anche  
 [Codice misto e informazioni mancanti nella finestra stack di chiamate](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Procedura: modificare il formato numerico delle finestre del debugger](https://msdn.microsoft.com/library/cd593847-a625-411d-a430-b798346ef18f)   
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Uso di punti di interruzione](../debugger/using-breakpoints.md)
