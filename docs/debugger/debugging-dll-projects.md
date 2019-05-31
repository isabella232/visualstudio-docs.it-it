---
title: Eseguire il debug di progetti di DLL | Microsoft Docs
ms.date: 11/06/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- templates, debugging DLLs
- DLLs, debugging
- debugging [Visual Studio], DLLs
ms.assetid: 433cab30-d191-460b-96f7-90d2530ca243
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c22da2a31be1389ca0b60df6cc64ac6c9155ad69
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62852485"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Eseguire il debug di DLL in Visual Studio (C#, C++, Visual Basic, F#)

Una DLL (libreria a collegamento dinamico) è una libreria che contiene codice e i dati che possono essere usati da più app. È possibile usare Visual Studio per creare, compilare, configurare e DLL di debug.

## <a name="create-a-dll"></a>Creare una DLL

I seguenti modelli di progetto di Visual Studio possono creare DLL:

- C#, Visual Basic, o F# libreria di classi
- C#o Visual Basic Windows Form libreria di controlli (WCF)
- Libreria di C++ collegamento dinamico (DLL)

Per altre informazioni, vedere [Tecniche di debug MFC](../debugger/mfc-debugging-techniques.md).

Il debug di una libreria di WCF è simile al debug di una libreria di classi. Per informazioni dettagliate, vedere [Windows Forms Controls](/dotnet/framework/winforms/controls/index).

In genere si chiama una DLL di un altro progetto. Quando si esegue il debug del progetto chiamante, a seconda della configurazione di DLL, è possibile eseguire l'istruzione e il debug del codice DLL.

## <a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Configurazione di debug DLL

Quando si usa un modello di progetto di Visual Studio per creare un'app, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea automaticamente le impostazioni necessarie per le configurazioni della build di Debug e rilascio. Se necessario, è possibile modificare queste impostazioni. Per altre informazioni, vedere i seguenti articoli:

- [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Impostazioni di progetto per configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Impostazioni di progetto per una configurazione di debug di Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Procedura: Impostare configurazioni di debug e di rilascio](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Impostare DebuggableAttribute C++

Affinché il debugger possa connettersi a una DLL C++, è necessario che il codice C++ `DebuggableAttribute`.

**Per impostare `DebuggableAttribute`:**

1. Selezionare il progetto di DLL C++ in **Esplora soluzioni** e selezionare il **delle proprietà** icona, o il progetto e scegliere **proprietà**.

1. Nel **delle proprietà** riquadro, di sotto **Linker** > **debug**, selezionare **Sì (/ /ASSEMBLYDEBUG)** per  **Assembly Debuggable**.

Per altre informazioni, vedere [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="vxtskdebuggingdllprojectsexternal"></a> Impostare i percorsi dei file DLL di C/C++

Per eseguire il debug di una DLL esterna, un progetto chiamante deve essere in grado di trovare la DLL, relativi [file con estensione PDB](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)e qualsiasi altro file DLL necessario. È possibile creare un'attività di compilazione personalizzata per copiare questi file per il  *\<cartella di progetto > \Debug* cartella di output, oppure è possibile copiare i file presenti manualmente.

Per i progetti C/C++, è possibile impostare intestazione e LIB percorsi dei file nelle pagine delle proprietà di progetto, anziché copiarli nella cartella di output.

**Per C/C++ impostare intestazione e LIB percorsi dei file:**

1. Selezionare il progetto di DLL di C/C++ in **Esplora soluzioni** e selezionare il **delle proprietà** icona, o il progetto e scegliere **proprietà**.

1. Nella parte superiore del **delle proprietà** riquadro, in **Configuration**, selezionare **tutte le configurazioni**.

1. Sotto **C/C++**  > **generali** > **directory di inclusione aggiuntive**, specificare la cartella che contiene i file di intestazione.

1. Sotto **Linker** > **generali** > **Directory librerie aggiuntive**, specificare la cartella che contiene i file LIB.

1. Sotto **Linker** > **Input** > **dipendenze aggiuntive**, specificare il percorso completo e nome file per i file LIB.

1. Scegliere **OK**.

Per altre informazioni sulle impostazioni di progetto C++, vedere [pagine delle proprietà (Visual C++)](/cpp/ide/property-pages-visual-cpp).

## <a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Compilare una versione di Debug

Assicurarsi di compilare una versione di Debug della DLL prima di avviare il debug. Per eseguire il debug di una DLL, un'app chiamante deve essere in grado di trovare relativi [file con estensione PDB](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) e qualsiasi altro file DLL necessario.

È possibile creare un'attività di compilazione personalizzata per copiare i file DLL per il  *\<chiamata cartella del progetto > \Debug* cartella di output, oppure è possibile copiare i file presenti manualmente.

Assicurarsi di chiamare la DLL nella posizione corretta. Ciò potrebbe sembrare ovvio, ma se un'app chiamante Trova e carica una copia diversa della DLL, il debugger non raggiungerà mai i punti di interruzione che è impostato.

## <a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Eseguire il debug di una DLL

È possibile eseguire direttamente una DLL. Deve essere chiamato da un'app, in genere un *.exe* file. Per altre informazioni, vedere [creare e gestire i progetti Visual C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Per eseguire il debug di una DLL, è possibile [avviare il debug dell'App chiamante](#vxtskdebuggingdllprojectsthecallingapplication), o [eseguire il debug dal progetto di DLL](how-to-debug-from-a-dll-project.md) specificando le app chiamante. È anche possibile usare il debugger [finestra controllo immediato](#vxtskdebuggingdllprojectstheimmediatewindow) per valutare i metodi o funzioni di DLL in fase di progettazione senza usare un'app chiamante.

Per altre informazioni, vedere [innanzitutto osservare il debugger](../debugger/debugger-feature-tour.md).

### <a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Avviare il debug dell'App chiamante

L'app che chiama una DLL può essere:

- Un'app da un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto nello stesso o in una soluzione diversa dalla DLL.
- Un'app esistente già distribuito e in esecuzione in un computer di test o produzione.
- Trovarsi sul Web ed essere accessibile tramite un URL.
- Un'app web con una pagina web che incorpora la DLL.

Per eseguire il debug di una DLL di un'app chiamante, è possibile:

- Aprire il progetto per app chiamante e avviare il debug scegliendo **Debug** > **Avvia debug** oppure premendo **F5**.

  oppure

- Connettersi a un'app è già distribuito e in esecuzione in un computer di test o produzione. Utilizzare questo metodo per le DLL nei siti Web o nelle App web. Per altre informazioni, vedere [Procedura: Connettersi a un processo in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Prima di avviare il debug di app chiamante, impostare un punto di interruzione nella DLL. Visualizzare [usando i punti di interruzione](../debugger/using-breakpoints.md). Quando viene raggiunto il punto di interruzione DLL, è possibile eseguire il codice, osservandone l'esecuzione in ogni riga. Per altre informazioni, vedere [esplorare il codice nel debugger](../debugger/navigating-through-code-with-the-debugger.md).

Durante il debug, è possibile usare la **moduli** per verificare le DLL e *.exe* i file del caricamento dell'app. Per aprire la **moduli** finestra durante il debug, selezionare **Debug** > **Windows** > **moduli**. Per altre informazioni, vedere [Procedura: Usare la finestra Moduli](../debugger/how-to-use-the-modules-window.md).

### <a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Utilizzare la finestra controllo immediata

È possibile usare la **Immediate** finestra per la valutazione di metodi o funzioni di DLL in fase di progettazione. Il **Immediate** finestra svolge il ruolo di un'app chiamante.

>[!NOTE]
>È possibile usare la **Immediate** finestra in fase di progettazione con la maggior parte dei tipi di progetto. Non è supportata per SQL, i progetti web o uno script.

Ad esempio, per testare un metodo denominato `Test` nella classe `Class1`:

1. Con il progetto DLL aperto, aprire il **controllo immediato** finestra selezionando **Debug** > **Windows** > **immediato**o premendo **Ctrl**+**Alt**+**ho**.

1. Creare un'istanza di un oggetto di tipo `Class1` digitando quanto segue C# Scrivi codice nel **controllo immediato** finestra e quindi premendo **invio**. Questo codice gestito funziona per C# e Visual Basic, con opportune modifiche alla sintassi:

   ```csharp
   Class1 obj = new Class1();
   ```

   In C# tutti i nomi devono essere completi. I metodi o le variabili devono essere l'ambito corrente e il contesto quando il servizio di linguaggio tenta di valutare l'espressione.

1. Se `Test` accetta un parametro `int` , valutare `Test` usando la finestra **Controllo immediato** :

   ```csharp
   ?obj.Test(10);
   ```

   Il risultato viene stampato nella **Immediate** finestra.

1. Per continuare a eseguire il debug di `Test`, inserire un punto di interruzione nel metodo e valutare di nuovo la funzione.

   Il punto di interruzione verrà raggiunto ed è possibile avanzare `Test`. Al termine dell'esecuzione di `Test`, nel debugger verrà ripristinata la modalità di progettazione.

## <a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Debug in modalità mista

È possibile scrivere un'app chiamante per una DLL nel codice gestito o nativo. Se l'app nativa chiama una DLL gestita e si vuole eseguire il debug di entrambi, è possibile abilitare entrambi i debugger nativi e gestiti nelle proprietà del progetto. Il processo esatto dipende dal fatto che si desidera avviare il debug dal progetto della DLL o del progetto di app chiamante. Per altre informazioni, vedere [Procedura: Eseguire il debug in modalità mista](../debugger/how-to-debug-in-mixed-mode.md).

È anche possibile eseguire il debug di una DLL nativa da un progetto chiama gestito. Per altre informazioni, vedere [come eseguire il debug di codice gestito e nativo](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Vedere anche
- [Eseguire il debug del codice gestito](../debugger/debugging-managed-code.md)
- [Tipi di progetto Visual C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
