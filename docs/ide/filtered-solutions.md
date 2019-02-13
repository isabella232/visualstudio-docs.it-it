---
title: Caricare un subset di progetti
ms.date: 12/04/2018
ms.prod: visual-studio-dev16
ms.topic: conceptual
helpviewer_keywords:
- filtered solution
- solution filtering
author: gewarren
ms.author: stsu
manager: jillfra
monikerRange: '>= vs-2019'
ms.openlocfilehash: 2f7163ecda377d8fa8b7c27ed50dae4068d39600
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55952918"
---
# <a name="filtered-solutions-in-visual-studio"></a>Soluzioni filtrate in Visual Studio

**Novità di Visual Studio 2019 Preview 1**

I team di sviluppo con tanti utenti spesso collaborano usando un'unica soluzione di grandi dimensioni con molti progetti. Tuttavia, i singoli sviluppatori in genere lavorano su un subset limitato di questi progetti. Per migliorare le prestazioni quando si aprono soluzioni di grandi dimensioni, Visual Studio 2019 Preview 1 introduce la funzionalità di *filtro delle soluzioni*. Il filtro delle soluzioni consente di aprire una soluzione caricando solo i progetti selezionati. Il caricamento di un subset di progetti in una soluzione riduce i tempi di caricamento, compilazione ed esecuzione dei test della soluzione e consente una revisione più mirata.

Sono disponibili le funzionalità seguenti:

- È possibile lavorare sul codice più velocemente aprendo una soluzione senza caricare nessuno dei relativi progetti. Dopo aver aperto la soluzione, è possibile scegliere in modo selettivo i progetti da caricare.

- Quando si riapre una soluzione, Visual Studio memorizza i progetti che sono stati caricati nella sessione precedente e carica solo quelli.

- È possibile creare un file di filtro della soluzione per salvare una o più configurazioni di caricamento del progetto o condividere la configurazione con i colleghi.

## <a name="open-a-filtered-solution"></a>Aprire una soluzione filtrata

Per aprire una soluzione con solo alcuni dei progetti caricati, seguire questa procedura:

1. Scegliere **File** > **Apri** > **Progetto/Soluzione** dalla barra dei menu.

2. Nella finestra di dialogo **Nuovo progetto** selezionare la soluzione e quindi selezionare la casella di controllo **Non caricare i progetti**.

   ![Finestra di dialogo Apri progetto di Visual Studio con l'opzione Non caricare i progetti selezionata](media/filtered-solutions/do-not-load-projects.png)

3. Scegliere **Apri**.

   La soluzione viene aperta senza i relativi progetti caricati.

4. In **Esplora soluzioni** selezionare i progetti da caricare (premere **CTRL** mentre si fa clic per selezionare più di un progetto) e quindi fare clic sul progetto con il pulsante destro del mouse e scegliere **Ricarica progetto**.

   ![Ricaricare più progetti in Esplora soluzioni di Visual Studio](media/filtered-solutions/reload-project.png)

   Visual Studio memorizzerà i progetti caricati alla successiva apertura della soluzione in locale.

## <a name="toggle-unloaded-project-visibility"></a>Attivare o disattivare la visibilità dei progetti non caricati

È possibile scegliere di visualizzare tutti i progetti nella soluzione o solo quelli caricati usando una delle opzioni seguenti in **Esplora soluzioni**:

- Fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Show Unloaded Projects** (Mostra progetti non caricati) oppure **Hide Unloaded Projects** (Nascondi progetti non caricati).

- Selezionare il pulsante **Mostra tutti i file** per attivare o disattivare la visibilità dei progetti non caricati.

   ![Pulsante Mostra tutti i file in Esplora soluzioni di Visual Studio](media/filtered-solutions/show-all-files.PNG)

## <a name="solution-filter-files"></a>File di filtro della soluzione

Se si vuole condividere la configurazione di caricamento del progetto o eseguirne il commit al controllo del codice sorgente, è possibile creare un file di filtro della soluzione (con estensione *slnf*). Quando si apre un file di filtro della soluzione, la soluzione viene aperta in Visual Studio con i progetti specificati caricati e tutti i progetti non caricati nascosti. È possibile [attivare/disattivare](#toggle-unloaded-project-visibility) la visualizzazione dei progetti non caricati.

I file di filtro della soluzione si differenziano visivamente dai normali file della soluzione per il glifo a forma di imbuto nell'icona accanto alla soluzione in **Esplora soluzioni**. Il nome del filtro e il numero di progetti caricati vengono inoltre visualizzati accanto al nome della soluzione.

![File di filtro della soluzione aperto in Esplora soluzioni di Visual Studio](media/filtered-solutions/solution-filter.PNG)

> [!NOTE]
> Se dopo la creazione del file di filtro della soluzione alla soluzione originale vengono aggiunti nuovi progetti, verranno visualizzati come progetti non caricati in **Esplora soluzioni**.

### <a name="create-a-solution-filter-file"></a>Creare un file di filtro della soluzione

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Salva come filtro soluzione**.

   ![Voce di menu Salva come filtro soluzione in Esplora soluzioni di Visual Studio](media/filtered-solutions/save-as-solution-filter.png)

2. Scegliere un nome e un percorso per il file di filtro della soluzione.

Dopo essere stato creato, il file di filtro della soluzione viene aggiunto all'elenco **Progetti e soluzioni recenti** per facilitare l'accesso:

![Apri recenti in Visual Studio](media/filtered-solutions/open-recent.png)

## <a name="see-also"></a>Vedere anche

- [Personalizzare l'annidamento file in Esplora soluzioni](file-nesting-solution-explorer.md)
- [Ottimizzare le prestazioni di Visual Studio](optimize-visual-studio-performance.md)