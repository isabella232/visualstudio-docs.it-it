---
title: Debug di progetti DLL | Microsoft Docs
description: Eseguire il debug di file DLL (Dynamic Link Library) in Visual Studio. Utilizzare Visual Studio per creare, compilare, configurare ed eseguire il debug di dll.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ec78e9a04062699ea699f45671e1210fc2306631
ms.sourcegitcommit: fcfd0fc7702a47c81832ea97cf721cca5173e930
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2020
ms.locfileid: "97728499"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Eseguire il debug di dll in Visual Studio (C#, C++, Visual Basic, F #)

Una DLL (libreria a collegamento dinamico) è una libreria che contiene il codice e i dati che possono essere usati da più di un'app. È possibile usare Visual Studio per creare, compilare, configurare ed eseguire il debug di dll.

## <a name="create-a-dll"></a>Creare una DLL

I modelli di progetto di Visual Studio seguenti possono creare dll:

- Libreria di classi C#, Visual Basic o F #
- Libreria di controllo Windows Forms (WCF) C# o Visual Basic
- Libreria di Dynamic-Link C++ (DLL)

Per ulteriori informazioni, vedere [tecniche di debug MFC](../debugger/mfc-debugging-techniques.md).

Il debug di una libreria WCF è simile al debug di una libreria di classi. Per informazioni dettagliate, vedere [controlli Windows Forms](/dotnet/framework/winforms/controls/index).

In genere si chiama una DLL da un altro progetto. Quando si esegue il debug del progetto chiamante, a seconda della configurazione della DLL, è possibile eseguire istruzioni ed eseguire il debug del codice DLL.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a> Configurazione debug DLL

Quando si usa un modello di progetto di Visual Studio per creare un'app, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] crea automaticamente le impostazioni necessarie per le configurazioni di debug e di rilascio della build. Se necessario, è possibile modificare queste impostazioni. Per altre informazioni, vedere gli articoli seguenti:

- [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Procedura: impostare le configurazioni di debug e di rilascio](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Imposta DebuggableAttribute C++

Per la connessione del debugger a una DLL di C++, è necessario che il codice C++ emetta `DebuggableAttribute` .

**Per impostare `DebuggableAttribute` :**

1. Selezionare il progetto DLL C++ in **Esplora soluzioni** e selezionare l'icona **Proprietà** oppure fare clic con il pulsante destro del mouse sul progetto e scegliere **proprietà**.

1. Nel riquadro **Proprietà** , in debug del **linker**  >  , selezionare **Sì (/ASSEMBLYDEBUG)** per l'assembly di cui è stato eseguito il **debug**.

Per ulteriori informazioni, vedere [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a> Imposta percorsi file DLL C/C++

Per eseguire il debug di una DLL esterna, un progetto chiamante deve essere in grado di trovare la DLL, il [file con estensione PDB](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)e tutti gli altri file necessari per la dll. È possibile creare un'attività di compilazione personalizzata per copiare questi file nella cartella di output di *\<project folder> \Debug* . in alternativa, è possibile copiare i file manualmente.

Per i progetti C/C++, è possibile impostare i percorsi dei file di intestazione e LIB nelle pagine delle proprietà del progetto, anziché copiarli nella cartella di output.

**Per impostare i percorsi del file LIB e dell'intestazione C/C++:**

1. Selezionare il progetto DLL C/C++ in **Esplora soluzioni** e selezionare l'icona **Proprietà** oppure fare clic con il pulsante destro del mouse sul progetto e scegliere **proprietà**.

1. Nella parte superiore del riquadro **Proprietà** , in **configurazione**, selezionare **tutte le configurazioni**.

1. In **C/C++**  >  **General**  >  **Additional include directory** specificare la cartella contenente i file di intestazione.

1. In   >    >  **directory aggiuntive librerie** generali del linker specificare la cartella che contiene file lib.

1. In **linker**  >  **immettere**  >  **altre dipendenze**, specificare il percorso completo e il nome file per i file lib.

1. Selezionare **OK**.

Per ulteriori informazioni sulle impostazioni del progetto C++, vedere [riferimenti alla pagina delle proprietà di Windows c++](/cpp/build/reference/property-pages-visual-cpp).

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a> Compilare una versione di debug

Assicurarsi di compilare una versione di debug della DLL prima di avviare il debug. Per eseguire il debug di una DLL, un'app chiamante deve essere in grado di trovare il file con estensione [PDB](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) e tutti gli altri file necessari per la dll.

È possibile creare un'attività di compilazione personalizzata per copiare i file DLL nella cartella di output di *\<calling project folder> \Debug* . in alternativa, è possibile copiare i file manualmente.

Assicurarsi di chiamare la DLL nella posizione corretta. Questo può sembrare ovvio, ma se un'app chiamante trova e carica una copia diversa della DLL, il debugger non raggiungerà mai i punti di interruzione impostati.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a> Eseguire il debug di una DLL

Non è possibile eseguire direttamente una DLL. Deve essere chiamato da un'app, in genere un file con estensione *exe* . Per altre informazioni, vedere [progetti di Visual Studio-C++](/cpp/ide/creating-and-managing-visual-cpp-projects).

Per eseguire il debug di una DLL, è possibile [avviare il debug dall'app chiamante](#vxtskdebuggingdllprojectsthecallingapplication)oppure [eseguire il debug dal progetto di dll](how-to-debug-from-a-dll-project.md) specificando l'app chiamante. È anche possibile usare la [finestra controllo immediato](#vxtskdebuggingdllprojectstheimmediatewindow) del debugger per valutare le funzioni o i metodi dll in fase di progettazione, senza usare un'app chiamante.

Per ulteriori informazioni, vedere [la prima occhiata al debugger](../debugger/debugger-feature-tour.md).

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a> Avviare il debug dall'app chiamante

L'app che chiama una DLL può essere:

- Un'app da un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto nella stessa soluzione o in una soluzione diversa dalla dll.
- Un'app esistente già distribuita ed eseguita in un computer di test o di produzione.
- Trovarsi sul Web ed essere accessibile tramite un URL.
- Un'app Web con una pagina Web che incorpora la DLL.

Per eseguire il debug di una DLL da un'app chiamante, è possibile:

- Aprire il progetto per l'app chiamante e avviare il debug selezionando **debug**  >  **Avvia debug** o premendo **F5**.

  oppure

- Connettersi a un'app che è già stata distribuita ed eseguita in un computer di test o di produzione. Usare questo metodo per le dll nei siti Web o nelle app Web. Per altre informazioni, vedere [procedura: connettersi a un processo in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Prima di iniziare a eseguire il debug dell'app chiamante, impostare un punto di interruzione nella DLL. Vedere [utilizzo](../debugger/using-breakpoints.md)di punti di interruzione. Quando viene raggiunto il punto di interruzione della DLL, è possibile eseguire il codice un'istruzione alla volta, osservando l'azione a ogni riga. Per ulteriori informazioni, vedere [spostarsi nel codice del debugger](../debugger/navigating-through-code-with-the-debugger.md).

Durante il debug, è possibile usare la finestra **moduli** per verificare i file dll e *exe* caricati dall'app. Per aprire la finestra **moduli** , durante il debug selezionare **debug**  >    >  **moduli** di Windows. Per altre informazioni, vedere [procedura: usare la finestra moduli](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a> Utilizzare la finestra controllo immediato

È possibile utilizzare la finestra **controllo immediato** per valutare le funzioni o i metodi dll in fase di progettazione. La finestra di **controllo immediato** svolge il ruolo di un'app chiamante.

>[!NOTE]
>È possibile utilizzare la finestra **controllo immediato** in fase di progettazione con la maggior parte dei tipi di progetto. Non è supportata per SQL, progetti Web o script.

Ad esempio, per testare un metodo denominato `Test` nella classe `Class1` :

1. Con il progetto di dll aperto, aprire la finestra di **controllo immediato** selezionando **debug**  >  **Windows**  >  **immediate** o premendo **CTRL** + **ALT** + **I**.

1. Creare un'istanza di un oggetto di tipo `Class1` digitando il codice C# seguente nella finestra di **controllo immediato** e premendo **invio**. Questo codice gestito funziona per C# e Visual Basic, con modifiche di sintassi appropriate:

   ```csharp
   Class1 obj = new Class1();
   ```

   In C# tutti i nomi devono essere completi. Tutti i metodi o le variabili devono trovarsi nell'ambito e nel contesto correnti quando il servizio di linguaggio tenta di valutare l'espressione.

1. Se `Test` accetta un parametro `int` , valutare `Test` usando la finestra **Controllo immediato** :

   ```csharp
   ?obj.Test(10);
   ```

   Il risultato viene stampato nella finestra di **controllo immediato** .

1. Per continuare a eseguire il debug di `Test`, inserire un punto di interruzione nel metodo e valutare di nuovo la funzione.

   Il punto di interruzione verrà raggiunto ed è possibile eseguire un'istruzione alla volta `Test` . Al termine dell'esecuzione di `Test`, nel debugger verrà ripristinata la modalità di progettazione.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a> Debug in modalità mista

È possibile scrivere un'app chiamante per una DLL in codice gestito o nativo. Se l'app nativa chiama una DLL gestita e si desidera eseguire il debug di entrambi, è possibile abilitare sia i debugger gestiti sia quelli nativi nelle proprietà del progetto. Il processo esatto dipende dal fatto che si voglia avviare il debug dal progetto di DLL o dal progetto di applicazione chiamante. Per altre informazioni, vedere [procedura: eseguire il debug in modalità mista](../debugger/how-to-debug-in-mixed-mode.md).

È anche possibile eseguire il debug di una DLL nativa da un progetto chiamante gestito. Per ulteriori informazioni, vedere [come eseguire il debug di codice gestito e nativo](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Vedi anche
- [Eseguire il debug del codice gestito](../debugger/debugging-managed-code.md)
- [Preparare il debug di progetti C++](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Tipi di progetto C#, F # e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Impostazioni di progetto per una configurazione di debug C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Impostazioni di progetto per le configurazioni di debug C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
