---
title: 'Procedura: Visualizzare, salvare e configurare file di log di compilazione | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e0185e8879718e068cd624559087db9369d7e190
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58789926"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Procedura: Visualizzare, salvare e configurare file di log di compilazione

Dopo aver compilato un progetto nell'IDE di Visual Studio, è possibile visualizzare informazioni sulla compilazione nella finestra **Output**. Usando queste informazioni è possibile ad esempio risolvere un errore di compilazione. 

  - Per i progetti C++ è possibile visualizzare le stesse informazioni anche in un file con estensione *txt* creato e salvato automaticamente. 

  - Per i progetti di codice gestito, è possibile fare clic nella finestra dell'output di compilazione e premere **CTRL**+**S**. Visual Studio chiede il percorso per salvare le informazioni dalla finestra **Output** in un file con estensione *txt*. 
  
È anche possibile usare l'IDE per specificare i tipi di informazioni da visualizzare per ogni compilazione.

Se si compila qualsiasi tipo di progetto usando MSBuild, è possibile creare un file con estensione *txt* per salvare le informazioni sulla compilazione. Per altre informazioni, vedere [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Per visualizzare il file di log di compilazione per un progetto C++

1.  In **Esplora risorse** o **Esplora file** aprire il file seguente: *\\...\Visual Studio \<Version\>\Projects\\<ProjectName\>\\<ProjectName\>\Debug\\<ProjectName\>.txt*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Per creare un file di log di compilazione per un progetto di codice gestito

1.  Nella barra dei menu scegliere **Compila** > **Compila soluzione**.

2.  Nella finestra **Output** fare clic in un punto qualsiasi nel testo.

3.  Premere **CTRL**+**S**.

   Visual Studio richiede di specificare il percorso in cui salvare l'output di compilazione.

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Per modificare la quantità di informazioni inclusa nel log di compilazione

1.  Nella barra dei menu scegliere **Strumenti** > **Opzioni**.

2.  Nella pagina **Progetti e soluzioni** scegliere la pagina **Compila ed esegui**.

3.  Nell'elenco **Livello di dettaglio output in compilazione progetto MSBuild** scegliere uno dei valori seguenti e quindi scegliere il pulsante **OK**.

    |Livello di dettaglio|Description|
    | - |-----------------|
    |**Quiet**|Visualizza solo un riepilogo della compilazione.|
    |**Minimo**|Visualizza un riepilogo della compilazione e gli errori, gli avvisi e i messaggi classificati con priorità elevata.|
    |**Normale**|Visualizza un riepilogo della compilazione, gli errori, gli avvisi e i messaggi classificati con priorità elevata e le fasi principali della compilazione. Si tratta del livello di dettaglio usato più di frequente.|
    |**Dettagliato**|Visualizza un riepilogo della compilazione, gli errori, gli avvisi e i messaggi classificati con priorità elevata, tutte le fasi della compilazione e i messaggi classificati con priorità normale.|
    |**Diagnostico**|Visualizza tutti i dati disponibili per la compilazione. È possibile usare questo livello di dettaglio per facilitare il debug di problemi con gli script di compilazione personalizzati e altri problemi di compilazione.|

     Per altre informazioni, vedere [Finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) e <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > È necessario ricompilare il progetto per rendere effettive le modifiche nella finestra **Output** (tutti i progetti) e nel file *\<ProjectName.txt* (solo progetti C++).

## <a name="see-also"></a>Vedere anche

- [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Compilazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Compilare](../ide/compiling-and-building-in-visual-studio.md)
