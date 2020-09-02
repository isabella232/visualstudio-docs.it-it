---
title: 'Procedura: Visualizzare, salvare e configurare file di log di compilazione | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: ffc1c620136c55c42f3468129ed164075d762bff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670499"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Procedura: visualizzare, salvare e configurare file di log di compilazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dopo aver compilato un progetto nell'IDE di Visual Studio, è possibile visualizzare informazioni sulla compilazione nella finestra **Output**. Usando queste informazioni è possibile ad esempio risolvere un errore di compilazione. Per i progetti C++ è possibile visualizzare le stesse informazioni anche in un file con estensione txt creato e salvato automaticamente. Per i progetti di codice gestito è possibile copiare e incollare le informazioni dalla finestra **Output** in un file con estensione txt e salvarlo manualmente. È anche possibile usare l'IDE per specificare i tipi di informazioni da visualizzare per ogni compilazione.

 Se si compila qualsiasi tipo di progetto usando MSBuild, è possibile creare un file con estensione txt per salvare le informazioni sulla compilazione. Per altre informazioni, vedere [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md).

### <a name="to-view-the-build-log-file-for-a-c-project"></a>Per visualizzare il file di log di compilazione per un progetto C++

1. In Esplora **risorse** o **Esplora file**aprire il file seguente: \\ . ..\Visual Studio *Version*\projects \\ *NomeProgetto* \\ *NomeProgetto*\Debug \\ *ProjectName*. txt

### <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Per creare un file di log di compilazione per un progetto di codice gestito

1. Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.

2. Nella finestra **output** evidenziare le informazioni della compilazione e quindi copiarle negli Appunti.

3. Aprire un editor di testo, ad esempio Blocco note, incollare le informazioni nel file e quindi salvarlo.

### <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Per modificare la quantità di informazioni inclusa nel log di compilazione

1. Sulla barra dei menu scegliere **strumenti**, **Opzioni**.

2. Nella pagina **Progetti e soluzioni** scegliere la pagina **Compila ed esegui**.

3. Nell'elenco **Livello di dettaglio output in compilazione progetto MSBuild** scegliere uno dei valori seguenti e quindi scegliere il pulsante **OK**.

    |Livello di dettaglio|Descrizione|
    |---------------------|-----------------|
    |Quiet|Visualizza solo un riepilogo della compilazione.|
    |Minimal|Visualizza un riepilogo della compilazione e gli errori, gli avvisi e i messaggi classificati con priorità elevata.|
    |Normale|Visualizza un riepilogo della compilazione, gli errori, gli avvisi e i messaggi classificati con priorità elevata e le fasi principali della compilazione. Si tratta del livello di dettaglio usato più di frequente.|
    |Dettagliato|Visualizza un riepilogo della compilazione, gli errori, gli avvisi e i messaggi classificati con priorità elevata, tutte le fasi della compilazione e i messaggi classificati con priorità normale.|
    |Diagnostic|Visualizza tutti i dati disponibili per la compilazione. È possibile usare questo livello di dettaglio per facilitare il debug di problemi con gli script di compilazione personalizzati e altri problemi di compilazione.|

     Per ulteriori informazioni, vedere finestra di [dialogo Opzioni, progetti e soluzioni, compila ed Esegui](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) e <xref:Microsoft.Build.Framework.LoggerVerbosity> .

    > [!IMPORTANT]
    > È necessario ricompilare il progetto per rendere effettive le modifiche nella finestra **output** (tutti i progetti) e nel file *NomeProgetto*. txt (solo progetti C++).

## <a name="see-also"></a>Vedere anche
 [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md) [creazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [compilazione e creazione](../ide/compiling-and-building-in-visual-studio.md)
