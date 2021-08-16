---
title: Eseguire il debug di progetti DLL | Microsoft Docs
description: Eseguire il debug di file dll (dynamic-link library) in Visual Studio. Usare Visual Studio per creare, compilare, configurare ed eseguire il debug di DLL.
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
ms.openlocfilehash: 7fbeca9fbe809e157190aab60a8ecdd33b000b7a65ac35986f12aa3a767b1140
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121264085"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Eseguire il debug di DLL Visual Studio (C#, C++, Visual Basic, F#)

Una DLL (libreria a collegamento dinamico) è una libreria che contiene codice e dati che possono essere usati da più app. È possibile usare Visual Studio per creare, compilare, configurare ed eseguire il debug di DLL.

## <a name="create-a-dll"></a>Creare una DLL

I seguenti Visual Studio di progetto possono creare DLL:

- Libreria di classi C#, Visual Basic o F#
- Libreria di controlli Form Visual Basic Windows C# o Visual Basic Windows (WCF)
- Libreria di Dynamic-Link C++ (DLL)

Per altre informazioni, vedere [Tecniche di debug MFC.](../debugger/mfc-debugging-techniques.md)

Il debug di una libreria WCF è simile al debug di una libreria di classi. Per informazioni dettagliate, [vedere Windows Form.](/dotnet/framework/winforms/controls/index)

In genere si chiama una DLL da un altro progetto. Quando si esegue il debug del progetto chiamante, a seconda della configurazione della DLL, è possibile eseguire istruzioni ed eseguire il debug del codice dll.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Configurazione di debug dll

Quando si usa un modello Visual Studio di progetto per creare un'app, crea automaticamente le impostazioni necessarie per le configurazioni [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] delle build di debug e di rilascio. Se necessario, è possibile modificare queste impostazioni. Per altre informazioni, vedere gli articoli seguenti:

- [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Project per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Procedura: Impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Impostare DebuggableAttribute di C++

Perché il debugger si allegare a una DLL C++, il codice C++ deve generare `DebuggableAttribute` .

**Per impostare `DebuggableAttribute` :**

1. Selezionare il progetto DLL C++ in  **Esplora soluzioni** e selezionare l'icona Proprietà oppure fare clic con il pulsante destro del mouse sul progetto e **scegliere Proprietà.**

1. Nel riquadro **Proprietà** in **Debug del linker** selezionare Sì  >   **(/ASSEMBLYDEBUG) per** Assembly di cui è possibile eseguire il **debug.**

Per altre informazioni, vedere [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a> Impostare i percorsi dei file DLL C/C++

Per eseguire il debug di una DLL esterna, un progetto chiamante deve essere in grado di trovare la DLL, il relativo file con estensione [pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)e qualsiasi altro file richiesto dalla DLL. È possibile creare un'attività di compilazione personalizzata per copiare questi file nella cartella di output *\<project folder> \Debug* oppure copiare i file in questa cartella manualmente.

Per i progetti C/C++, è possibile impostare percorsi di file di intestazione e LIB nelle pagine delle proprietà del progetto, anziché copiarli nella cartella di output.

**Per impostare l'intestazione C/C++ e i percorsi dei file LIB:**

1. Selezionare il progetto DLL C/C++ in **Esplora soluzioni** e selezionare l'icona Proprietà oppure fare clic con il pulsante destro del mouse sul progetto e **scegliere Proprietà.** 

1. Nella parte superiore del riquadro **Proprietà** in **Configurazione selezionare** Tutte **le configurazioni.**

1. In **Directory di inclusione aggiuntive generali C/C++** specificare la cartella che contiene i file di  >    >  intestazione.

1. In **Directory librerie** aggiuntive generali del linker  >    >  specificare la cartella che contiene i file LIB.

1. In **Linker**  >  **Input**  >  **Additional Dependencies (Dipendenze** aggiuntive di input del linker) specificare il percorso completo e il nome file per i file LIB.

1. Selezionare **OK**.

Per altre informazioni sulle impostazioni del progetto C++, Windows riferimento alla pagina delle proprietà [C++.](/cpp/build/reference/property-pages-visual-cpp)

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Compilare una versione di debug

Assicurarsi di compilare una versione di debug della DLL prima di avviare il debug. Per eseguire il debug di una DLL, un'app chiamante deve essere in grado di trovare il relativo file con estensione [pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) e qualsiasi altro file richiesto dalla DLL.

È possibile creare un'attività di compilazione personalizzata per copiare i file DLL nella cartella di output *\<calling project folder> \Debug* oppure copiare i file in questa cartella manualmente.

Assicurarsi di chiamare la DLL nel percorso corretto. Può sembrare ovvio, ma se un'app chiamante trova e carica una copia diversa della DLL, il debugger non avrà mai raggiunto i punti di interruzione impostati.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Eseguire il debug di una DLL

Non è possibile eseguire direttamente una DLL. Deve essere chiamato da un'app, in genere un file *.exe.* Per altre informazioni, vedere [Visual Studio progetti - C++.](/cpp/ide/creating-and-managing-visual-cpp-projects)

Per eseguire il debug di una DLL, è possibile avviare il [debug dall'app chiamante](#vxtskdebuggingdllprojectsthecallingapplication)oppure eseguire [il debug](how-to-debug-from-a-dll-project.md) dal progetto DLL specificando l'app chiamante. È anche possibile usare la finestra [di controllo immediato del](#vxtskdebuggingdllprojectstheimmediatewindow) debugger per valutare funzioni o metodi DLL in fase di progettazione, senza usare un'app chiamante.

Per altre informazioni, vedere [Prima di tutto il debugger.](../debugger/debugger-feature-tour.md)

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Avviare il debug dall'app chiamante

L'app che chiama una DLL può essere:

- Un'app da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] un progetto nella stessa soluzione o in una soluzione diversa dalla DLL.
- Un'app esistente già distribuita e in esecuzione in un computer di test o di produzione.
- Trovarsi sul Web ed essere accessibile tramite un URL.
- Un'app Web con una pagina Web che incorpora la DLL.

Per eseguire il debug di una DLL da un'app chiamante, è possibile:

- Aprire il progetto per l'app chiamante e avviare il debug selezionando **Debug**  >  **Avvia** debug o premendo **F5.**

  oppure

- Connettersi a un'app già distribuita e in esecuzione in un computer di test o di produzione. Usare questo metodo per le DLL nei siti Web o nelle app Web. Per altre informazioni, vedere [Procedura: Connettersi a un processo in esecuzione.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

Prima di avviare il debug dell'app chiamante, impostare un punto di interruzione nella DLL. Vedere [Uso dei punti di interruzione.](../debugger/using-breakpoints.md) Quando viene raggiunto il punto di interruzione della DLL, è possibile eseguire il codice un'istruzione alla volta, osservando l'azione in ogni riga. Per altre informazioni, vedere [Esplorare il codice nel debugger.](../debugger/navigating-through-code-with-the-debugger.md)

Durante il debug, è possibile usare la **finestra** Moduli per verificare le DLL e i.exe *caricati* dall'app. Per aprire la **finestra Moduli** durante il debug, selezionare **Debug**  >  **Windows**  >  **Moduli**. Per altre informazioni, [vedere Procedura: Usare la finestra Moduli](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Usare la finestra Controllo immediato

È possibile usare la finestra **Controllo immediato** per valutare funzioni o metodi DLL in fase di progettazione. La **finestra Controllo** immediato svolge il ruolo di app chiamante.

>[!NOTE]
>È possibile usare la finestra **Controllo immediato** in fase di progettazione con la maggior parte dei tipi di progetto. Non è supportata per l'SQL, i progetti Web o lo script.

Ad esempio, per testare un metodo denominato `Test` nella classe `Class1` :

1. Con il progetto DLL aperto, aprire **la** finestra Controllo immediato selezionando **Debug**  >  **Windows**  >  **controllo immediato** o premendo **CTRL** + **ALT** + **I.**

1. Creare un'istanza di un `Class1` oggetto di  tipo digitando il codice C# seguente nella finestra controllo immediato e premendo **INVIO.** Questo codice gestito funziona per C# e Visual Basic, con modifiche appropriate alla sintassi:

   ```csharp
   Class1 obj = new Class1();
   ```

   In C# tutti i nomi devono essere completi. Tutti i metodi o le variabili devono essere nell'ambito e nel contesto correnti quando il servizio di linguaggio tenta di valutare l'espressione.

1. Se `Test` accetta un parametro `int` , valutare `Test` usando la finestra **Controllo immediato** :

   ```csharp
   ?obj.Test(10);
   ```

   Il risultato viene stampato nella finestra **di controllo immediato.**

1. Per continuare a eseguire il debug di `Test`, inserire un punto di interruzione nel metodo e valutare di nuovo la funzione.

   Verrà raggiunto il punto di interruzione ed è possibile eseguire . `Test` Al termine dell'esecuzione di `Test`, nel debugger verrà ripristinata la modalità di progettazione.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Debug in modalità mista

È possibile scrivere un'app chiamante per una DLL in codice gestito o nativo. Se l'app nativa chiama una DLL gestita e si vuole eseguire il debug di entrambi, è possibile abilitare sia il debugger gestito che quello nativo nelle proprietà del progetto. Il processo esatto dipende dal fatto che si voglia avviare il debug dal progetto DLL o dal progetto di app chiamante. Per altre informazioni, vedere [Procedura: Eseguire il debug in modalità mista.](../debugger/how-to-debug-in-mixed-mode.md)

È anche possibile eseguire il debug di una DLL nativa da un progetto chiamante gestito. Per altre informazioni, vedere [Come eseguire il debug di codice gestito e nativo.](how-to-debug-managed-and-native-code.md)

## <a name="see-also"></a>Vedi anche
- [Eseguire il debug del codice gestito](../debugger/debugging-managed-code.md)
- [Preparare il debug di progetti C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Project per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Project per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Project per una configurazione Visual Basic debug](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
