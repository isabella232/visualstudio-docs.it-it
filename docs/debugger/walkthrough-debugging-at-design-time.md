---
title: Eseguire il debug in fase di progettazione | Microsoft Docs
description: Usare la finestra Controllo immediato per eseguire il debug del codice in fase di progettazione, senza eseguire l'app. È possibile eseguire una funzione ed esaminare lo stato quando viene raggiunto un punto di interruzione.
ms.custom: SEO-VS-2020
ms.date: 01/10/2019
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- debugging [Visual Studio], design-time
- breakpoints, design-time debugging
- Immediate window, design-time debugging
- design-time debugging
ms.assetid: 35bfdd2c-6f60-4be1-ba9d-55fce70ee4d8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 360bdb1ac3d3dfce56a60f1e1c33e97d76885c6a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122090200"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Debug in fase di progettazione in Visual Studio (C#, C++/CLI, Visual Basic, F#)

Per eseguire il debug del codice in fase di progettazione anziché durante l'esecuzione di un'app, è possibile usare la finestra **Controllo** immediato.

Per eseguire il debug di codice XAML dietro un'app dalla finestra di progettazione XAML, ad esempio scenari di data binding dichiarativi, è possibile usare **Debug**  >  **Attach to Process**.

## <a name="use-the-immediate-window"></a>Usare la finestra Controllo immediato

È possibile usare la finestra Visual Studio **controllo** immediato per eseguire una funzione o una subroutine senza eseguire l'app. Se la funzione o la subroutine contiene un punto di interruzione, Visual Studio si interromperà in corrispondenza del punto di interruzione. È quindi possibile usare le finestre del debugger per esaminare lo stato del programma. Questa funzionalità è denominata *debug in fase di progettazione.*

L'esempio seguente è in Visual Basic. È anche possibile usare la finestra **Controllo** immediato in fase di progettazione nelle app C#, F# e C++/CLI.

1. Incollare il codice seguente in un'app console Visual Basic vuota:

   ```vb
   Module Module1

       Sub Main()
           MySub()
       End Sub

       Function MyFunction() As Decimal
           Static i As Integer
           i = i + 1
           Return i
       End Function

       Sub MySub()
           MyFunction()

       End Sub
   End Module
   ```

1. Impostare un punto di interruzione nella riga **End Function**.

1. Aprire la **finestra Controllo** immediato selezionando **Debug Windows**  >    >  **Controllo immediato.** Digitare `?MyFunction` nella finestra e quindi premere **INVIO.**

   Viene raggiunto il punto di interruzione e il valore di **MyFunction** nella **finestra Variabili** locali è **1**. È possibile esaminare lo stack di chiamate e altre finestre di debug mentre l'app è in modalità di interruzione.

1. Selezionare **Continua** sulla barra Visual Studio strumenti. L'app termina e viene restituito **1** nella finestra **di controllo immediato.** Assicurarsi di essere ancora in modalità progettazione.

1. Digitare `?MyFunction` di nuovo **nella** finestra di controllo immediato e premere **INVIO.** Viene raggiunto il punto di interruzione e il valore di **MyFunction** nella **finestra** Variabili locali è **2**.

1. Senza selezionare **Continua**, `?MySub()` digitare nella finestra **di** controllo immediato e quindi premere **INVIO.** Viene raggiunto il punto di interruzione e il valore di **MyFunction** nella **finestra** Variabili locali è **3**. È possibile esaminare lo stato dell'app mentre l'app è in modalità di interruzione.

1. Selezionare **Continua**. Il punto di interruzione viene raggiunto nuovamente e il valore di **MyFunction** nella **finestra** Variabili locali è ora **2**. La **finestra Di** controllo immediato restituisce Che espressione è stata **valutata e non ha valore**.

1. Selezionare **di nuovo Continua.** L'app termina e viene restituito **2** nella finestra **di controllo immediato.** Assicurarsi di essere ancora in modalità progettazione.

1. Per cancellare il contenuto della finestra Controllo **immediato,** fare clic con il pulsante destro del mouse nella finestra e **scegliere Cancella tutto.**

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>Eseguire il debug di un controllo XAML personalizzato in fase di progettazione collegando alla finestra di progettazione XAML

1. Aprire la soluzione o il progetto in Visual Studio.

1. Compilare la soluzione o il progetto.

1. Aprire la pagina XAML contenente il controllo personalizzato di cui si vuole eseguire il debug.

   Per i progetti UWP Windows la build 16299 o successiva, questo passaggio avvia il *UwpSurface.exe* processo. Per i progetti WPF Windows la build 16299 o successiva, questo passaggio avvia il *WpfSurface.exe* progetto. Per le versioni wpf o UWP precedenti Windows build 16299, questo passaggio avvia il *XDesProc.exe* processo. 

1. Aprire una seconda istanza di Visual Studio. Non aprire una soluzione o un progetto nella seconda istanza.

1. Nella seconda istanza di Visual Studio aprire il menu **Debug** e scegliere **Associa a processo.**

1. A seconda del tipo di progetto (vedere i passaggi precedenti), selezionare ilUwpSurface.exe *,* *WpfSurface.exe* o il processo *XDesProc.exe* dall'elenco dei processi disponibili.

1. Nel campo **Associa a** della finestra di dialogo **Associa a** processo scegliere il tipo di codice corretto per il controllo personalizzato di cui si vuole eseguire il debug.

   Se il controllo personalizzato è stato scritto in un linguaggio .NET, scegliere il tipo di codice .NET appropriato, ad esempio **Managed (CoreCLR).** Se il controllo personalizzato è stato scritto in C++, scegliere **Nativo.**

1. Collegare la seconda istanza di Visual Studio clic sul **pulsante Associa.**

1. Nella seconda istanza di Visual Studio aprire i file di codice associati al controllo personalizzato di cui si vuole eseguire il debug. Assicurarsi di aprire solo i file, non l'intera soluzione o progetto.

1. Inserire i punti di interruzione necessari nei file aperti in precedenza.

1. Nella prima istanza di Visual Studio chiudere la pagina XAML contenente il controllo personalizzato di cui si vuole eseguire il debug (la stessa pagina aperta nei passaggi precedenti).

1. Nella prima istanza di Visual Studio aprire la pagina XAML chiusa nel passaggio precedente. In questo modo il debugger si arresterà in corrispondenza del primo punto di interruzione impostato nella seconda istanza di Visual Studio.

1. Eseguire il debug del codice nella seconda istanza di Visual Studio.

## <a name="see-also"></a>Vedi anche
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)