---
title: Progetti DLL di debug - Documenti Microsoft
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
ms.openlocfilehash: 898eb0eb1489d83e97ec9f0a5b38b475bda0199d
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302203"
---
# <a name="debug-dlls-in-visual-studio-c-c-visual-basic-f"></a>Eseguire il debug delle DLL in Visual Studio (C'è, C ', Visual Basic, F ')

Una DLL (libreria a collegamento dinamico) è una libreria che contiene codice e dati che possono essere usati da più app. È possibile utilizzare Visual Studio per creare, compilare, configurare ed eseguire il debug delle DLL.

## <a name="create-a-dll"></a>Creare una DLLCreate a DLL

I modelli di progetto di Visual Studio seguenti possono creare DLL:The following Visual Studio project templates can create DLLs:

- Libreria di classi Di C, Visual Basic o F
- Libreria di controlli Windows Form (WCF) di Visual Basic o Visual Basic
- Libreria a collegamento dinamico (DLL)

Per ulteriori informazioni, vedere [Tecniche di debug MFC](../debugger/mfc-debugging-techniques.md).

Il debug di una libreria WCF è simile al debug di una libreria di classi. Per informazioni dettagliate, vedere [Controlli Windows Form](/dotnet/framework/winforms/controls/index).

In genere si chiama una DLL da un altro progetto. Quando si esegue il debug del progetto chiamante, a seconda della configurazione della DLL, è possibile eseguire un'istruzione ed eseguire il debug del codice DLL.

## <a name="dll-debug-configuration"></a><a name="vxtskdebuggingdllprojectschangingdefaultconfigurations"></a>Configurazione di debug DLL

Quando si usa un modello di progetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di Visual Studio per creare un'app, vengono create automaticamente le impostazioni necessarie per le configurazioni di compilazione Debug e Rilascia. Se necessario, è possibile modificare queste impostazioni. Per altre informazioni, vedere gli articoli seguenti:

- [Impostazioni di progetto per una configurazione di debug di C](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Impostazioni di progetto per le configurazioni di debug di C](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Impostazioni di progetto per una configurazione di debug di Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Procedura: impostare le configurazioni di debug e rilascioHow to: Set Debug and Release configurations](../debugger/how-to-set-debug-and-release-configurations.md)

### <a name="set-c-debuggableattribute"></a>Impostare DebuggableAttribute di C

Affinché il debugger si acheda a una DLL `DebuggableAttribute`di C, è necessario che il codice di C.

**Per `DebuggableAttribute`impostare :**

1. In **Esplora soluzioni,** selezionare l'icona **Proprietà,** selezionare l'icona Proprietà oppure fare clic con il pulsante destro del mouse sul progetto e **scegliere Proprietà**.

1. Nel riquadro **Proprietà** , in**Debug** **linker** > , selezionare **Sì (/ASSEMBLYDEBUG)** per **Assembly di debug**.

Per ulteriori informazioni, vedere [/ASSEMBLYDEBUG](/cpp/build/reference/assemblydebug-add-debuggableattribute).

### <a name="set-cc-dll-file-locations"></a><a name="vxtskdebuggingdllprojectsexternal"></a>Impostare i percorsi dei file DLL C/C

Per eseguire il debug di una DLL esterna, un progetto chiamante deve essere in grado di trovare la DLL, il relativo [file pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)e qualsiasi altro file richiesto dalla DLL. È possibile creare un'attività di compilazione personalizzata per copiare questi file nella cartella del * \<progetto>* cartella di output Debug oppure è possibile copiare manualmente i file.

Per i progetti C/C, è possibile impostare i percorsi dei file di intestazione e LIB nelle pagine delle proprietà del progetto, anziché copiarli nella cartella di output.

**Per impostare i percorsi dei file C/C, ovvero l'intestazione e lib:**

1. In **Esplora soluzioni,** selezionare l'icona **Proprietà,** selezionare l'icona Proprietà oppure fare clic con il pulsante destro del mouse sul progetto e **scegliere Proprietà**.

1. Nella parte superiore del riquadro **Proprietà,** in **Configurazione,** selezionare **Tutte le configurazioni.**

1. In Directory di**General** > **inclusione aggiuntive**generali **di C/C** > , specificare la cartella che contiene i file di intestazione.

1. In **Linker** > **General** > **Additional Libraries Directories**, specificare la cartella contenente file LIB.

1. In**Dipendenze aggiuntive****input** >  **del linker** > specificare il percorso completo e il nome file per i file LIB.

1. Selezionare **OK**.

Per ulteriori informazioni sulle impostazioni del progetto di C, consultate Informazioni di riferimento sulla pagina delle proprietà di [Windows C.](/cpp/build/reference/property-pages-visual-cpp)

## <a name="build-a-debug-version"></a><a name="vxtskdebuggingdllprojectsbuildingadebugversion"></a>Compilare una versione di debugBuild a Debug version

Assicurarsi di compilare una versione di debug della DLL prima di avviare il debug. Per eseguire il debug di una DLL, un'app chiamante deve essere in grado di trovare il [relativo file pdb](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) e tutti gli altri file necessari per la DLL.

È possibile creare un'attività di compilazione personalizzata per copiare i file DLL nella cartella del * \<progetto chiamante>* cartella di output Debug oppure è possibile copiare i file manualmente.

Assicurarsi di chiamare la DLL nella posizione corretta. Questo può sembrare ovvio, ma se un'app chiamante trova e carica una copia diversa della DLL, il debugger non raggiungerà mai i punti di interruzione impostati.

## <a name="debug-a-dll"></a><a name="vxtskdebuggingdllprojectswaystodebugthedll"></a>Debug a DLL

Non è possibile eseguire direttamente una DLL. Deve essere chiamato da un'app, in genere un file *.exe.* Per ulteriori informazioni, vedere Progetti di [Visual Studio - C .](/cpp/ide/creating-and-managing-visual-cpp-projects)

Per eseguire il debug di una DLL, è possibile [avviare il debug dall'app chiamante](#vxtskdebuggingdllprojectsthecallingapplication)oppure [eseguire il debug dal progetto DLL](how-to-debug-from-a-dll-project.md) specificandone l'app chiamante. È anche possibile usare la [finestra Di colore di](#vxtskdebuggingdllprojectstheimmediatewindow) controllo immediato del debugger per valutare le funzioni o i metodi DLL in fase di progettazione, senza usare un'app chiamante.

Per ulteriori informazioni, vedere [Prima occhiata al debugger](../debugger/debugger-feature-tour.md).

### <a name="start-debugging-from-the-calling-app"></a><a name="vxtskdebuggingdllprojectsthecallingapplication"></a>Avviare il debug dall'app chiamante

L'app che chiama una DLL può essere:

- Un'app [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da un progetto nella stessa soluzione o in una soluzione diversa dalla DLL.
- Un'app esistente già distribuita e in esecuzione in un computer di test o di produzione.
- Trovarsi sul Web ed essere accessibile tramite un URL.
- Un'app Web con una pagina Web che incorpora la DLL.

Per eseguire il debug di una DLL da un'app chiamante, è possibile:To debug a DLL from a calling app, you can:

- Aprire il progetto per l'app chiamante e avviare il debug selezionando Debug di**avvio** **in eseguito** > o premendo **F5**.

  o

- Connettersi a un'app già distribuita e in esecuzione in un computer di test o di produzione. Utilizzare questo metodo per le DLL nei siti Web o nelle app Web. Per ulteriori informazioni, vedere [Procedura: connettersi a un processo in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

Prima di avviare il debug dell'app chiamante, impostare un punto di interruzione nella DLL. Consultate [Utilizzo dei punti di interruzione.](../debugger/using-breakpoints.md) Quando viene raggiunto il punto di interruzione DLL, è possibile eseguire il codice un'istruzione alla volta, osservando l'azione in ogni riga. Per ulteriori informazioni, vedere [Esplorare il codice nel debugger](../debugger/navigating-through-code-with-the-debugger.md).

Durante il debug, è possibile utilizzare la finestra **Moduli** per verificare le DLL e i file *con estensione exe* caricati dall'app. Per aprire la finestra **Moduli,** durante il debug, selezionare **Debug** > **moduli****Windows** > . Per ulteriori informazioni, vedere [Procedura: utilizzare la finestra Moduli](../debugger/how-to-use-the-modules-window.md).

### <a name="use-the-immediate-window"></a><a name="vxtskdebuggingdllprojectstheimmediatewindow"></a>Utilizzare la finestra Immediata

È possibile utilizzare la finestra **Immediata** per valutare le funzioni o i metodi DLL in fase di progettazione. La finestra **Immediata** svolge il ruolo di un'app chiamante.

>[!NOTE]
>È possibile utilizzare la finestra **Immediata** in fase di progettazione con la maggior parte dei tipi di progetto. Non è supportato per SQL, progetti Web o script.

Ad esempio, per testare un metodo denominato `Test` nella classe `Class1`:

1. Con il progetto DLL aperto, aprire la finestra **Immediata** selezionando **Debug** > **di Controllo immediato** di**Windows** > o premendo **CTRL**+**Alt**+**I**.

1. Creare un'istanza `Class1` di un oggetto di tipo digitando il seguente codice in C, nella finestra **Immediata** e premendo **INVIO**. Questo codice gestito funziona per C .

   ```csharp
   Class1 obj = new Class1();
   ```

   In C# tutti i nomi devono essere completi. Qualsiasi metodo o variabile deve trovarsi nell'ambito e nel contesto correnti quando il servizio di linguaggio tenta di valutare l'espressione.

1. Se `Test` accetta un parametro `int` , valutare `Test` usando la finestra **Controllo immediato** :

   ```csharp
   ?obj.Test(10);
   ```

   Il risultato viene stampato nella finestra **Immediata.**

1. Per continuare a eseguire il debug di `Test`, inserire un punto di interruzione nel metodo e valutare di nuovo la funzione.

   Il punto di interruzione verrà raggiunto ed è possibile eseguire un'istruzione alla volta. `Test` Al termine dell'esecuzione di `Test`, nel debugger verrà ripristinata la modalità di progettazione.

## <a name="mixed-mode-debugging"></a><a name="vxtskdebuggingdllprojectsmixedmodedebugging"></a>Debug in modalità mista

È possibile scrivere un'app chiamante per una DLL in codice gestito o nativo. Se l'app nativa chiama una DLL gestita e si desidera eseguire il debug di entrambe le regole, è possibile abilitare i debugger gestiti e nativi nelle proprietà del progetto. Il processo esatto varia a seconda che si desideri avviare il debug dal progetto DLL o dal progetto dell'app chiamante. Per ulteriori informazioni, vedere [Procedura: eseguire il debug in modalità mista](../debugger/how-to-debug-in-mixed-mode.md).

È inoltre possibile eseguire il debug di una DLL nativa da un progetto chiamante gestito. Per ulteriori informazioni, vedere Come eseguire il debug di [codice gestito e nativo](how-to-debug-managed-and-native-code.md).

## <a name="see-also"></a>Vedere anche
- [Eseguire il debug del codice gestito](../debugger/debugging-managed-code.md)
- [Preparare il debug dei progetti in C](../debugger/debugging-preparation-visual-cpp-project-types.md)
- [Tipi di progetto C#, F# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Impostazioni di progetto per una configurazione di debug di C](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Impostazioni di progetto per le configurazioni di debug di C](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Impostazioni di progetto per una configurazione di debug di Visual BasicProject settings for a Visual Basic Debug configuration](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Sicurezza del debugger](../debugger/debugger-security.md)
