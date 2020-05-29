---
title: Esegui il debug in fase di progettazione | Microsoft Docs
ms.custom: ''
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8bc5d08e8b0ae71acb846e1e863e24e8b8def0ee
ms.sourcegitcommit: d20ce855461c240ac5eee0fcfe373f166b4a04a9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2020
ms.locfileid: "84183561"
---
# <a name="debug-at-design-time-in-visual-studio-c-ccli-visual-basic-f"></a>Eseguire il debug in fase di progettazione in Visual Studio (C#, C++/CLI, Visual Basic, F #)

Per eseguire il debug del codice in fase di progettazione anziché durante l'esecuzione di un'app, è possibile usare la finestra **controllo immediato** .

Per eseguire il debug del codice XAML dietro un'app dalla finestra di progettazione XAML, ad esempio scenari dichiarativi Data Binding, è possibile usare **debug**  >  **Connetti a processo**.

## <a name="use-the-immediate-window"></a>Utilizzare la finestra controllo immediato

È possibile usare la finestra **controllo immediato** di Visual Studio per eseguire una funzione o una subroutine senza eseguire l'app. Se la funzione o subroutine contiene un punto di interruzione, Visual Studio si interrompe in corrispondenza del punto di interruzione. È quindi possibile usare le finestre del debugger per esaminare lo stato del programma. Questa funzionalità è denominata *debug in fase di progettazione*.

Nell'esempio seguente viene Visual Basic. È anche possibile usare la finestra **controllo immediato** in fase di progettazione nelle app C#, F # e C++/CLI.

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

1. Impostare un punto di interruzione nella **funzione di fine**riga.

1. Aprire la finestra di **controllo immediato** selezionando **debug**  >  **Windows**  >  **immediate**. Digitare `?MyFunction` nella finestra, quindi premere **invio**.

   Il punto di interruzione viene raggiunto e il valore di **funzione** nella finestra **variabili locali** è **1**. È possibile esaminare lo stack di chiamate e altre finestre di debug mentre l'app è in modalità di interruzioni.

1. Selezionare **continua** sulla barra degli strumenti di Visual Studio. L'app termina e viene restituito **1** nella finestra di **controllo immediato** . Assicurarsi di essere ancora in modalità progettazione.

1. Digitare `?MyFunction` di nuovo nella finestra di **controllo immediato** e premere **invio**. Il punto di interruzione viene raggiunto e il valore di **funzione** nella finestra **variabili locali** è **2**.

1. Senza selezionare **continua**, digitare `?MySub()` nella finestra di **controllo immediato** , quindi premere **invio**. Il punto di interruzione viene raggiunto e il valore di **funzione** nella finestra **variabili locali** è **3**. È possibile esaminare lo stato dell'app mentre l'app è in modalità di interruzioni.

1. Seleziona **Continua**. Il punto di interruzione viene nuovamente raggiunto e il valore di **funzione** nella finestra **variabili locali** è ora **2**. La finestra **controllo immediato** restituisce l' **espressione è stata valutata e non ha alcun valore**.

1. Selezionare di nuovo **continua** . L'app termina e **2** viene restituita nella finestra di **controllo immediato** . Assicurarsi di essere ancora in modalità progettazione.

1. Per cancellare il contenuto della finestra di **controllo immediato** , fare clic con il pulsante destro del mouse nella finestra e scegliere **Cancella tutto**.

## <a name="debug-a-custom-xaml-control-at-design-time-by-attaching-to-xaml-designer"></a>Eseguire il debug di un controllo XAML personalizzato in fase di progettazione tramite la connessione alla finestra di progettazione XAML

1. Aprire la soluzione o il progetto in Visual Studio.

1. Compilare la soluzione o il progetto.

1. Aprire la pagina XAML contenente il controllo personalizzato di cui si desidera eseguire il debug.

   Per i progetti UWP destinati a Windows Build 16299 o versione successiva, questo passaggio avvierà il processo *UwpSurface. exe* . Per i progetti WPF destinati a Windows Build 16299 o versione successiva, questo passaggio avvierà il processo *WpfSurface. exe* . Per le versioni WPF o UWP precedenti a Windows Build 16299, questo passaggio avvierà il processo *XDesProc. exe* . 

1. Aprire una seconda istanza di Visual Studio. Non aprire una soluzione o un progetto nella seconda istanza.

1. Nella seconda istanza di Visual Studio aprire il menu **debug** e scegliere **Connetti a processo...**.

1. A seconda del tipo di progetto (vedere passaggi precedenti), selezionare il processo *UwpSurface. exe*, *WpfSurface. exe*o *XDesProc. exe* dall'elenco dei processi disponibili.

1. Nel campo **Connetti a** della finestra di dialogo **Connetti a processo** scegliere il tipo di codice corretto per il controllo personalizzato di cui si vuole eseguire il debug.

   Se il controllo personalizzato è stato scritto in un linguaggio .NET, scegliere il tipo di codice .NET appropriato, ad esempio **Managed (CoreCLR)**. Se il controllo personalizzato è stato scritto in C++, scegliere **nativo**.

1. Per aggiungere la seconda istanza di Visual Studio, fare clic sul pulsante **Connetti** .

1. Nella seconda istanza di Visual Studio aprire i file di codice associati al controllo personalizzato di cui si vuole eseguire il debug. Assicurarsi di aprire solo i file, non l'intera soluzione o progetto.

1. Inserire i punti di interruzione necessari nei file aperti in precedenza.

1. Nella prima istanza di Visual Studio, chiudere la pagina XAML contenente il controllo personalizzato di cui si vuole eseguire il debug (la stessa pagina aperta nei passaggi precedenti).

1. Nella prima istanza di Visual Studio aprire la pagina XAML chiusa nel passaggio precedente. Il debugger verrà arrestato in corrispondenza del primo punto di interruzione impostato nella seconda istanza di Visual Studio.

1. Eseguire il debug del codice nella seconda istanza di Visual Studio.

## <a name="see-also"></a>Vedere anche
- [Presentazione del debugger](../debugger/debugger-feature-tour.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)