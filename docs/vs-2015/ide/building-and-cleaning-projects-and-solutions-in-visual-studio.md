---
title: Creazione di soluzioni di pulizia di progetti
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.BuildProjectPicker
- vs.batchbuild
helpviewer_keywords:
- Clean Solution command
- builds [Visual Studio], managing
- solution build configurations, starting
- Build Solution command
- project build configurations, starting
- build configurations, starting
- project build configurations, dependencies
- Rebuild Solution command
- solution build configurations, build order
- builds [Visual Studio], preparing
ms.assetid: 710891fd-379e-42c2-a84b-44a7af694ca0
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 05e8d13454ab9698ae855f1e937e85eb287a3a35
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057633"
---
# <a name="building-and-cleaning-projects-and-solutions-in-visual-studio"></a>Compilazione e pulizia di progetti e soluzioni in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tramite le procedure descritte in questo argomento è possibile compilare, ricompilare o pulire tutti o alcuni progetti o elementi di progetto di una soluzione. Per un'esercitazione dettagliata, vedere [procedura dettagliata: Compilazione di un'applicazione](../ide/walkthrough-building-an-application.md).

> [!NOTE]
>  L'interfaccia utente dell'edizione di Visual Studio in uso potrebbe essere diversa da quanto descritto in questo argomento, a seconda delle impostazioni attive. Per modificare le impostazioni, aprire il menu **Strumenti** e quindi scegliere **Importa/Esporta impostazioni**. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

### <a name="to-build-rebuild-or-clean-an-entire-solution"></a>Per compilare, ricompilare o pulire un'intera soluzione

1.  In **Esplora soluzioni**  scegliere una soluzione o aprire la soluzione voluta.

2.  Nella barra dei menu, scegliere **Compila** e quindi scegliere uno dei comandi seguenti:

    -   Scegliere **Compila** o **Compila soluzione** per compilare solo i file e i componenti del progetto che sono stati modificati dalla compilazione più recente.

        > [!NOTE]
        >  Il comando **Compila** diventa **Compila soluzione** se una soluzione include più progetti.

    -   Scegliere **Ricompila soluzione** per "pulire" la soluzione e quindi compilare tutti i componenti e i file dei progetti.

    -   Scegliere **Pulisci soluzione** per eliminare eventuali file intermedi e di output. Quando sono rimasti solo i file dei componenti e dei progetti, è possibile compilare nuove istanze di file intermedi e di output.

### <a name="to-build-or-rebuild-a-single-project"></a>Per compilare o ricompilare un progetto singolo

1.  In **Esplora soluzioni**  scegliere un progetto o aprire il progetto voluto.

2.  Sulla barra dei menu scegliere **Compila** e quindi scegliere **Compila**_NomeProgetto_ o **Ricompila**_NomeProgetto_.

    -   Scegliere **Compila**_NomeProgetto_ per compilare solo i componenti del progetto che sono stati modificati dalla build più recente.

    -   Scegliere **Ricompila**_NomeProgetto_ per "pulire" il progetto e quindi compilare i file e tutti i componenti del progetto.

### <a name="to-build-only-the-startup-project-and-its-dependencies"></a>Per compilare il progetto di avvio e le relative dipendenze

1. Nella barra dei menu scegliere **Strumenti**, **Opzioni**.

2. Nella finestra di dialogo **Opzioni** espandere il nodo **Progetti e soluzioni** e quindi scegliere la pagina **Compila ed esegui**.

    Si apre la finestra di dialogo **Compila ed esegui, Progetti e soluzioni, Opzioni**.

3. Selezionare la casella di controllo **Compila progetti di avvio e dipendenze solo in fase di esecuzione**.

    Se questa casella di controllo è selezionata, solo il progetto di avvio corrente e le relative dipendenze vengono compilati quando si esegue la procedura seguente:

   - Scegliere **Debug**, **Avvia** (F5) dalla barra dei menu.

   - Dalla barra dei menu scegliere **Compila**, **Compila soluzione** (CTRL+MAIUSC+B).

     Quando questa casella di controllo è deselezionata e si eseguono i comandi precedenti vengono compilati tutti i progetti, le relative dipendenze e i file della soluzione. Per impostazione predefinita, questa casella di controllo è deselezionata.

### <a name="to-build-only-the-selected-visual-c-project"></a>Per compilare solo il progetto di Visual C++ selezionato

1. Scegliere un progetto di [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] e quindi dalla barra dei menu scegliere **Compila**, **Project Only** (Solo progetto) e quindi uno dei comandi seguenti:

   - **Build Only** (Compila solo) *NomeProgetto*

   - **Rebuild Only** (Ricompila solo) *NomeProgetto*

   - **Clean Only** (Pulisci solo) *NomeProgetto*

   - **Link Only** (Collega solo) *NomeProgetto*

     Questi comandi si applicano solo al progetto di [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] scelto. Non eseguono la compilazione, la ricompilazione, la pulizia o il collegamento di eventuali dipendenze del progetto o file di soluzione. A seconda della versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], il sottomenu **Project Only** (Solo progetto) potrebbe contenere altri comandi.

### <a name="to-compile-multiple-c-project-items"></a>Per compilare più elementi di un progetto C++

1.  In **Esplora soluzioni** scegliere più file che dispongono di azioni che possono essere compilate, aprire il menu di scelta rapida per uno di questi file e quindi scegliere **Compila**.

     Se i file hanno dipendenze, vengono compilati in ordine di dipendenza. L'operazione di compilazione non riesce se i file richiedono un'intestazione precompilata non disponibile quando si esegue la compilazione. L'operazione di compilazione usa la configurazione della soluzione attiva corrente.

### <a name="to-stop-a-build"></a>Per interrompere una compilazione

1.  Effettuare uno dei passaggi seguenti:

    -   Nella barra dei menu scegliere **Compila**, **Annulla**.

    -   Scegliere la combinazione di tasti Ctrl + Interr.

## <a name="see-also"></a>Vedere anche
 [Procedura: Visualizzare, salvare e configurare file di Log di compilazione](../ide/how-to-view-save-and-configure-build-log-files.md) [ottenere log di compilazione](../msbuild/obtaining-build-logs-with-msbuild.md) [compilazione e creazione](../ide/compiling-and-building-in-visual-studio.md) [informazioni sulle configurazioni della Build](../ide/understanding-build-configurations.md) [Eseguire il debug e rilascio delle configurazioni di progetto](http://msdn.microsoft.com/en-us/0440b300-0614-4511-901a-105b771b236e) [C/C++ Building Reference](http://msdn.microsoft.com/library/100b4ccf-572c-4d1f-970c-fa0bc0cc0d2d) [opzioni della riga di comando Devenv](../ide/reference/devenv-command-line-switches.md) [soluzioni e progetti](../ide/solutions-and-projects-in-visual-studio.md)
