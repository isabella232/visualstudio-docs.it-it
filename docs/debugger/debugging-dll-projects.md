---
title: Eseguire il debug di progetti DLL | Microsoft Docs
description: Eseguire il debug di file di libreria a collegamento dinamico (DLL) in Visual Studio. Usare Visual Studio per creare, compilare, configurare ed eseguire il debug di DLL.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ba25ff92131f9f044e0b81d25cf49e865563161b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122134116"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Eseguire il debug di DLL in Visual Studio (C#, C++, Visual Basic, F#)

Una DLL (libreria a collegamento dinamico) è una libreria che contiene codice e dati che possono essere usati da più app. È possibile usare Visual Studio per creare, compilare, configurare ed eseguire il debug di DLL.

## <a name="create-a-dll"></a>Creare una DLL

I modelli di Visual Studio seguenti possono creare DLL:

- Libreria di classi C#, Visual Basic o F#
- Libreria di controlli Form Visual Basic Windows C# o Visual Basic Windows (WCF)
- Libreria Dynamic-Link C++ (DLL)

Per altre informazioni, vedere [Tecniche di debug MFC](../debugger/mfc-debugging-techniques.md).

Il debug di una libreria WCF è simile al debug di una libreria di classi. Per informazioni dettagliate, [vedere Windows Forms Controls](/dotnet/framework/winforms/controls/index).

In genere si chiama una DLL da un altro progetto. Quando si esegue il debug del progetto chiamante, a seconda della configurazione della DLL, è possibile eseguire un'istruzione alla volta ed eseguire il debug del codice DLL.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Configurazione del debug DLL

Quando si usa un modello Visual Studio di progetto per creare un'app, vengono create automaticamente le impostazioni necessarie per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] le configurazioni di build di debug e versione. Se necessario, è possibile modificare queste impostazioni. Per altre informazioni, vedere gli articoli seguenti:

- [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Project per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Procedura: Impostare le configurazioni di debug e versione](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Impostare DebuggableAttribute C++

Per collegare il debugger a una DLL C++, il codice C++ deve generare `DebuggableAttribute` .

**Per impostare `DebuggableAttribute` :**

1. Selezionare il progetto DLL C++ in  **Esplora soluzioni** selezionare l'icona Proprietà oppure fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.

1. Nel riquadro **Proprietà** in **Debug del linker** selezionare Sì  >   **(/ASSEMBLYDEBUG) per** Assembly di cui è possibile eseguire il **debug.**

Per altre informazioni, vedere [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a> Impostare i percorsi dei file DLL C/C++

Per eseguire il debug di una DLL esterna, un progetto chiamante deve essere in grado di trovare la DLL, il [relativo file con estensione pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)e qualsiasi altro file richiesto dalla DLL. È possibile creare un'attività di compilazione personalizzata per copiare questi file nella cartella di output *\<project folder> \Debug* oppure copiare i file manualmente.

Per i progetti C/C++, è possibile impostare i percorsi di intestazione e file LIB nelle pagine delle proprietà del progetto, anziché copiarli nella cartella di output.

**Per impostare l'intestazione C/C++ e i percorsi dei file LIB:**

1. Selezionare il progetto DLL C/C++ in  **Esplora soluzioni** e selezionare l'icona Proprietà oppure fare clic con il pulsante destro del mouse sul progetto e scegliere **Proprietà**.

1. Nella parte superiore del riquadro **Proprietà** selezionare Tutte **le** configurazioni in **Configurazione**.

1. In **Directory di inclusione aggiuntive generali C/C++** specificare la cartella contenente i file di  >    >  intestazione.

1. In **Directory librerie** aggiuntive generali del linker  >    >  specificare la cartella contenente i file LIB.

1. In **Dipendenze aggiuntive** di input del  >  **linker** specificare il percorso completo e il nome  >  file per i file LIB.

1. Selezionare **OK**.

Per altre informazioni sulle impostazioni del progetto C++, Windows riferimento alla pagina delle proprietà [C++.](/cpp/build/reference/property-pages-visual-cpp)

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Compilare una versione di debug

Assicurarsi di compilare una versione di debug della DLL prima di avviare il debug. Per eseguire il debug di una DLL, un'app chiamante deve essere in grado di trovare il [relativo file con estensione pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) e qualsiasi altro file richiesto dalla DLL.

È possibile creare un'attività di compilazione personalizzata per copiare i file DLL nella cartella di output *\<calling project folder> \Debug* oppure copiare i file manualmente.

Assicurarsi di chiamare la DLL nel percorso corretto. Questo può sembrare ovvio, ma se un'app chiamante trova e carica una copia diversa della DLL, il debugger non avrà mai raggiunto i punti di interruzione impostati.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Eseguire il debug di una DLL

Non è possibile eseguire direttamente una DLL. Deve essere chiamato da un'app, in genere *un*.exefile. Per altre informazioni, vedere [progetti Visual Studio - C++.](/cpp/ide/creating-and-managing-visual-cpp-projects)

Per eseguire il debug di una DLL, è possibile avviare il [debug dall'app](#vxtskdebuggingdllprojectsthecallingapplication)chiamante o eseguire [il debug](how-to-debug-from-a-dll-project.md) dal progetto DLL specificando l'app chiamante. È anche possibile usare la finestra Di controllo [immediato del](#vxtskdebuggingdllprojectstheimmediatewindow) debugger per valutare funzioni o metodi DLL in fase di progettazione, senza usare un'app chiamante.

Per altre informazioni, vedere [Prima di tutto il debugger.](../debugger/debugger-feature-tour.md)

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Avviare il debug dall'app chiamante

L'app che chiama una DLL può essere:

- Un'app [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da un progetto nella stessa soluzione o in una soluzione diversa dalla DLL.
- Un'app esistente già distribuita e in esecuzione in un computer di test o di produzione.
- Trovarsi sul Web ed essere accessibile tramite un URL.
- Un'app Web con una pagina Web che incorpora la DLL.

Per eseguire il debug di una DLL da un'app chiamante, è possibile:

- Aprire il progetto per l'app chiamante e avviare il debug selezionando **Debug**  >  **Avvia** debug o premendo **F5.**

  oppure

- Connettersi a un'app già distribuita e in esecuzione in un computer di test o di produzione. Usare questo metodo per le DLL nei siti Web o nelle app Web. Per altre informazioni, vedere [Procedura: Connettersi a un processo in esecuzione.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

Prima di avviare il debug dell'app chiamante, impostare un punto di interruzione nella DLL. Vedere [Uso di punti di interruzione](../debugger/using-breakpoints.md). Quando viene raggiunto il punto di interruzione dll, è possibile eseguire il codice un'istruzione alla volta, osservando l'azione in ogni riga. Per altre informazioni, vedere [Esplorare il codice nel debugger](../debugger/navigating-through-code-with-the-debugger.md).

Durante il debug, è possibile usare la **finestra Moduli** per verificare le DLL e.exe *file* caricati dall'app. Per aprire la **finestra Moduli,** durante il debug, **selezionare**  >  **Debug Windows**  >  **moduli**. Per altre informazioni, [vedere Procedura: Usare la finestra Moduli](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Usare la finestra Controllo immediato

È possibile usare la finestra **Controllo immediato** per valutare funzioni o metodi DLL in fase di progettazione. La **finestra Controllo** immediato svolge il ruolo di un'app chiamante.

>[!NOTE]
>È possibile usare la finestra **Controllo immediato** in fase di progettazione con la maggior parte dei tipi di progetto. Non è supportato per l'SQL, i progetti Web o lo script.

Ad esempio, per testare un metodo denominato `Test` nella classe `Class1` :

1. Con il progetto DLL aperto, aprire la **finestra Controllo** immediato selezionando Debug Windows controllo immediato  >    >   o premendo **CTRL** + **ALT+I.** + 

1. Creare un'istanza di un oggetto di tipo digitando il codice `Class1` C# seguente nella finestra **Controllo** immediato e premendo **INVIO.** Questo codice gestito funziona per C# e Visual Basic, con le modifiche appropriate alla sintassi:

   ```csharp
   Class1 obj = new Class1();
   ```

   In C# tutti i nomi devono essere completi. Tutti i metodi o le variabili devono essere nell'ambito e nel contesto correnti quando il servizio di linguaggio tenta di valutare l'espressione.

1. Se `Test` accetta un parametro `int` , valutare `Test` usando la finestra **Controllo immediato** :

   ```csharp
   ?obj.Test(10);
   ```

   Il risultato viene stampato nella **finestra Controllo** immediato.

1. Per continuare a eseguire il debug di `Test`, inserire un punto di interruzione nel metodo e valutare di nuovo la funzione.

   Verrà raggiunto il punto di interruzione ed è possibile eseguire un'istruzione alla `Test` volta. Al termine dell'esecuzione di `Test`, nel debugger verrà ripristinata la modalità di progettazione.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Debug in modalità mista

È possibile scrivere un'app chiamante per una DLL in codice gestito o nativo. Se l'app nativa chiama una DLL gestita e si vuole eseguire il debug di entrambi, è possibile abilitare sia il debugger gestito che quello nativo nelle proprietà del progetto. Il processo esatto dipende dal fatto che si voglia avviare il debug dal progetto DLL o dal progetto di app chiamante. Per altre informazioni, vedere [Procedura: Eseguire il debug in modalità mista.](../debugger/how-to-debug-in-mixed-mode.md)

È anche possibile eseguire il debug di una DLL nativa da un progetto chiamante gestito. Per altre informazioni, vedere [Come eseguire il debug di codice gestito e nativo.](how-to-debug-managed-and-native-code.md)

## <a name="see-also"></a>Vedi anche
- [Eseguire il debug del codice gestito](../debugger/debugging-managed-code.md)
- [Preparare il debug di progetti C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Tipi di progetto C#, F# e Visual Basic progetto](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Project per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Project per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Project per una configurazione Visual Basic debug](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
