---
title: Caricare un subset di progetti
description: Informazioni sui filtri delle soluzioni e su come consente di caricare rapidamente un subset di progetti in una soluzione.
ms.custom: SEO-VS-2020
ms.date: 04/22/2019
ms.topic: conceptual
helpviewer_keywords:
- filtered solution
- solution filtering
author: TerryGLee
ms.author: stsu
manager: jmartens
ms.technology: vs-ide-general
monikerRange: '>= vs-2019'
ms.openlocfilehash: 52c06a218c14fa09a6c879fa90805ddc48b22d8d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625925"
---
# <a name="filtered-solutions-in-visual-studio"></a>Soluzioni filtrate in Visual Studio

I team di sviluppo con tanti utenti spesso collaborano usando un'unica soluzione di grandi dimensioni con molti progetti. Tuttavia, i singoli sviluppatori in genere lavorano su un subset limitato di questi progetti. Per migliorare le prestazioni quando si aprono soluzioni di grandi dimensioni, Visual Studio 2019 ha introdotto la funzionalità di *filtro delle soluzioni*. Il filtro delle soluzioni consente di aprire una soluzione caricando solo i progetti selezionati. Il caricamento di un subset di progetti in una soluzione riduce i tempi di caricamento, compilazione ed esecuzione dei test della soluzione e consente una revisione più mirata.

Sono disponibili le funzionalità seguenti:

- È possibile lavorare sul codice più velocemente aprendo una soluzione senza caricare nessuno dei relativi progetti. Dopo aver aperto la soluzione, è possibile scegliere in modo selettivo i progetti da caricare.

- Quando si riapre una soluzione, Visual Studio memorizza i progetti che sono stati caricati nella sessione precedente e carica solo quelli.

- È possibile creare un file di filtro della soluzione per salvare una o più configurazioni di caricamento del progetto o condividere la configurazione con i colleghi.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows.

## <a name="open-a-filtered-solution"></a>Aprire una soluzione filtrata

È possibile aprire una soluzione senza caricare uno dei relativi progetti direttamente dalla finestra di dialogo **Apri progetto** o tramite la [riga di comando](#command-line).

### <a name="open-project-dialog"></a>Finestra di dialogo Apri progetto

Per aprire una soluzione senza caricare uno dei relativi progetti dalla finestra di dialogo **Apri progetto**:

1. Scegliere **Apri**  >  **file**  >  **Project/Soluzione** dalla barra dei menu.

2. Nella finestra di dialogo **Apri progetto** selezionare la soluzione e quindi selezionare la casella di controllo **Non caricare i progetti**.

   ![Finestra di dialogo Apri progetto di Visual Studio con l'opzione Non caricare i progetti selezionata](media/filtered-solutions/do-not-load-projects.png)

3. Scegliere **Apri**.

   La soluzione viene aperta senza i relativi progetti caricati.

4. In **Esplora soluzioni** selezionare i progetti da caricare (premere **CTRL** mentre si fa clic per selezionare più di un progetto) e quindi fare clic sul progetto con il pulsante destro del mouse e scegliere **Ricarica progetto**.

   ![Ricaricare più progetti in Esplora soluzioni di Visual Studio](media/filtered-solutions/reload-project.png)

   Visual Studio memorizzerà i progetti caricati alla successiva apertura della soluzione in locale.

### <a name="command-line"></a>Riga di comando

(Novità di Visual Studio 2019 versione 16.1)

Per aprire una soluzione senza caricare alcun progetto dalla riga di comando, usare [`/donotloadprojects`](../ide/reference/donotloadprojects-devenv-exe.md) l'opzione come illustrato nell'esempio seguente:

```cmd
devenv /donotloadprojects MySln.sln
```

## <a name="toggle-unloaded-project-visibility"></a>Attivare o disattivare la visibilità dei progetti non caricati

È possibile scegliere di visualizzare tutti i progetti nella soluzione o solo quelli caricati usando una delle opzioni seguenti in **Esplora soluzioni**:

- Fare clic con il pulsante destro del mouse sulla soluzione e scegliere **Show Unloaded Projects** (Mostra progetti non caricati) oppure **Hide Unloaded Projects** (Nascondi progetti non caricati).

- Selezionare il nodo della soluzione per abilitare il pulsante **Mostra tutti i file** e quindi fare clic sul pulsante per attivare o disattivare la visibilità dei progetti non caricati.

   ![Pulsante Mostra tutti i file in Esplora soluzioni di Visual Studio](media/filtered-solutions/show-all-files.PNG)

## <a name="load-project-dependencies"></a>Caricare le dipendenze del progetto

In una soluzione in cui vengono caricati solo i progetti selezionati potrebbero non essere caricate tutte le dipendenze di un progetto. Usare l'opzione di menu **Carica dipendenze del progetto** per assicurarsi che vengano caricati anche tutti i progetti da cui dipende un progetto. Fare clic con il pulsante destro del mouse su uno o più progetti caricati in **Esplora soluzioni** e scegliere **Carica dipendenze del progetto**.

![Caricare le dipendenze del progetto in Visual Studio 2019](media/filtered-solutions/load-project-dependencies.png)

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

## <a name="see-also"></a>Vedi anche

- [Personalizzare l'annidamento file in Esplora soluzioni](file-nesting-solution-explorer.md)
- [Ottimizzare le prestazioni di Visual Studio](optimize-visual-studio-performance.md)
