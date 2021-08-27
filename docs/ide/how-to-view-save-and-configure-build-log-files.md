---
title: 'Procedura: Visualizzare, salvare e configurare file di log di compilazione | Microsoft Docs'
description: Informazioni su come visualizzare, salvare e configurare i file di log di compilazione. Questi file forniscono informazioni utili per attività come la risoluzione di un errore di compilazione.
ms.custom: SEO-VS-2020
ms.date: 08/28/2019
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: 75d38b76-26d6-4f43-bbe7-cbacd7cc81e7
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 3316bf26f660b04c4f003b02523be3f9c408e73f
ms.sourcegitcommit: 42aec4a2ea6dec67dbe4c93bcf0fa1116a4b93d9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/26/2021
ms.locfileid: "122980930"
---
# <a name="how-to-view-save-and-configure-build-log-files"></a>Procedura: Visualizzare, salvare e configurare file di log di compilazione

Dopo aver compilato un progetto nell'IDE di Visual Studio, è possibile visualizzare informazioni sulla compilazione nella finestra **Output**. Usando queste informazioni è possibile ad esempio risolvere un errore di compilazione.

- Per i progetti C++, è anche possibile visualizzare le stesse informazioni in un file di log creato e salvato quando si compila un progetto. 

- Per i progetti di codice gestito, è possibile fare clic nella finestra di output di compilazione e premere **CTRL** + **S**. Visual Studio richiede un percorso per salvare le informazioni dalla finestra **Output** in un file di log.

È anche possibile usare l'IDE per specificare i tipi di informazioni da visualizzare per ogni compilazione.

Se si compila qualsiasi tipo di progetto usando MSBuild, è possibile creare un file di log per salvare le informazioni sulla compilazione. Per altre informazioni, vedere [Recupero di log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-view-the-build-log-file-for-a-c-project"></a>Per visualizzare il file di log di compilazione per un progetto C++

1. In **Windows Explorer** o **Esplora file** aprire il file seguente (relativo alla cartella radice del progetto): *Versione* \\ {ProjectName}. Log* o *Debug \\ {ProjectName}.log*

## <a name="to-create-a-build-log-file-for-a-managed-code-project"></a>Per creare un file di log di compilazione per un progetto di codice gestito

1. Sulla barra dei menu scegliere **Compila**  >  **soluzione**.

2. Nella finestra **Output** fare clic in un punto qualsiasi nel testo.

3. Premere  + **CTRL+S.**

   Visual Studio richiede di specificare il percorso in cui salvare l'output di compilazione.

È anche possibile generare log eseguendo MSBuild direttamente dalla riga di comando, tramite l'opzione `-fileLogger` (`-fl`) della riga di comando. Vedere [Recuperare log di compilazione con MSBuild](../msbuild/obtaining-build-logs-with-msbuild.md).

## <a name="to-change-the-amount-of-information-included-in-the-build-log"></a>Per modificare la quantità di informazioni inclusa nel log di compilazione

1. Sulla barra dei menu scegliere **Opzioni**  >  **strumenti**.

2. Nella pagina **Progetti e soluzioni** scegliere la pagina **Compila ed esegui**.

3. Nell'elenco **Livello di dettaglio output in compilazione progetto MSBuild** scegliere uno dei valori seguenti e quindi scegliere il pulsante **OK**.

    |Livello di dettaglio|Descrizione|
    | - |-----------------|
    |**Quiet**|Visualizza solo un riepilogo della compilazione.|
    |**Minima**|Visualizza un riepilogo della compilazione e gli errori, gli avvisi e i messaggi classificati con priorità elevata.|
    |**Normal**|Visualizza un riepilogo della compilazione, gli errori, gli avvisi e i messaggi classificati con priorità elevata e le fasi principali della compilazione. Si tratta del livello di dettaglio usato più di frequente.|
    |**Dettagliato**|Visualizza un riepilogo della compilazione, gli errori, gli avvisi e i messaggi classificati con priorità elevata, tutte le fasi della compilazione e i messaggi classificati con priorità normale.|
    |**Diagnostic**|Visualizza tutti i dati disponibili per la compilazione. È possibile usare questo livello di dettaglio per facilitare il debug di problemi con gli script di compilazione personalizzati e altri problemi di compilazione.|

     Per altre informazioni, vedere [Finestra di dialogo Opzioni, Progetti e soluzioni, Compila ed esegui](../ide/reference/options-dialog-box-projects-and-solutions-build-and-run.md) e <xref:Microsoft.Build.Framework.LoggerVerbosity>.

    > [!IMPORTANT]
    > È necessario ricompilare il progetto per rendere effettive le modifiche nella finestra **Output** (tutti i progetti) e nel file con estensione *\<ProjectName>txt* (solo progetti C++).

## <a name="use-binary-logs-to-make-it-easier-to-browse-large-log-files"></a>Usare i log binari per semplificare la ricerca di file di log di grandi dimensioni

I log binari sono una funzionalità facoltativa per i progetti .NET che consente di ottenere un'esperienza di ricerca dei log più completa, con la quale sarebbe possibile trovare facilmente informazioni nei log di grandi dimensioni. Per usare i log binari, installare gli [strumenti dei sistemi di progetto](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ProjectSystemTools). Per altre informazioni, vedere [https://msbuildlog.com](https://msbuildlog.com) e [Log binario](https://github.com/microsoft/msbuild/blob/master/documentation/wiki/Binary-Log.md)

## <a name="see-also"></a>Vedi anche

- [Compilazione e pulizia di progetti e soluzioni in Visual Studio](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Compilare](../ide/compiling-and-building-in-visual-studio.md)
