---
title: Visualizzazione di dati con R
description: Come tracciare dati da programmi R in Visual Studio usando finestre dei tracciati.
ms.date: 06/29/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.technology: vs-rtvs
ms.workload:
- data-science
ms.openlocfilehash: 150bc0a1fb78c58ecc9e086cf20a25e32243215b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060505"
---
# <a name="create-visual-data-plots-with-r"></a>Creare tracciati visivi dei dati con R

Il tracciato è una parte fondamentale del flusso di lavoro di un data scientist. In R Tools per Visual Studio (RTVS), tutte le attività di tracciato coinvolgono una o più finestre dei tracciati, che sono progettate per migliorare la produttività con questa attività chiave.

![Immagine banner tracciato](media/plotting-hero-image.png)

:::row:::
    :::column:::
        ![icona della telecamera per un video](../install/media/video-icon.png "Guardare un video")
    :::column-end:::
    :::column:::
        [Guardare un video (youtube.com)](https://www.youtube.com/watch?v=ZTbKmz5RSgY) sui tracciati con R (2m 02s).
    :::column-end:::
:::row-end:::

## <a name="the-plot-window"></a>Finestra dei tracciati

Una finestra dei tracciati contiene una serie di tracciati, in cui ognuno viene generato da un comando `plot`. Ad esempio, con `plot(1:100)` si crea una nuova finestra dei tracciati se non è già disponibile:

![Tracciato lineare 1 a 100](media/plotting-1-to-100.png)

Tecnicamente, i comandi `plot` di R eseguono il rendering dell'output a un dispositivo di grafica R; una finestra dei tracciati esegue il rendering dei contenuti di un dispositivo di grafica R, motivo per cui a ogni finestra dei tracciati viene assegnato un numero di dispositivo.

Le finestre dei tracciati sono indipendenti dai progetti di Visual Studio e rimangono aperte quando si caricano e si chiudono i progetti.

La generazione di un tracciato usa la finestra dei tracciati "attiva", salvando gli eventuali tracciati precedenti nella cronologia dei tracciati (vedere [Cronologia dei tracciati](#plot-history)). Ad esempio, immettere `plot(100:1)` e il primo tracciato viene sostituito con una riga verso il basso.

Come tutte le altre finestre di Visual Studio, la finestra dei tracciati supporta i layout personalizzati (vedere [Personalizzare il layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md)). Le finestre dei tracciati possono essere ancorate in diverse posizioni all'interno della cornice di Visual Studio, ridimensionate all'interno di essa o interamente estratte per il ridimensionamento separato.

In tutti i casi il ridimensionamento di una finestra dei tracciati esegue nuovamente il rendering del tracciato per offrire la migliore qualità di immagine. In genere è consigliabile ridimensionare un tracciato prima di esportarlo in un file o negli Appunti con i comandi descritti nella sezione successiva.

## <a name="plot-window-commands"></a>Comandi della finestra dei tracciati

La barra degli strumenti della finestra del tracciato contiene i comandi applicabili, la maggior parte dei quali sono disponibili anche tramite il menu  >  **Tracciati di** R Tools.

| Button | Comando | Descrizione |
| --- | --- | --- |
| ![Pulsante Nuova finestra dei tracciati](media/plotting-toolbar-01-new-plot-window.png) | Nuova finestra dei tracciati | Crea una finestra dei tracciati separata con la propria cronologia. Vedere [Più finestre dei tracciati](#multiple-plot-windows). |
| ![Pulsante di attivazione della finestra dei tracciati](media/plotting-toolbar-02-activate-plot-window.png) | Attiva finestra dei tracciati | Imposta la finestra dei tracciati corrente come finestra attiva, in modo che i comandi `plot` successivi vengano sottoposti a rendering per quella finestra. Vedere [Più finestre dei tracciati](#multiple-plot-windows). Vedere [Più finestre dei tracciati](#multiple-plot-windows). |
| ![Pulsante della finestra cronologia dei tracciati](media/plotting-toolbar-03-plot-history.png) | Finestra cronologia dei tracciati | Apre una finestra con tutti i tracciati nella cronologia visualizzati come miniature. Vedere [Cronologia dei tracciati](#plot-history). |
| ![Pulsanti della cronologia dei tracciati](media/plotting-toolbar-04-plot-history-arrows.png) | Tracciato precedente/successivo |  Passa al tracciato precedente o successivo nella cronologia. È anche possibile passare alla cronologia con CTRL+ ALT+F11 (Precedente) e CTRL+ALT F12 (Successivo). Vedere [Cronologia dei tracciati](#plot-history). |
| ![Pulsante Salva come immagine](media/plotting-toolbar-05-save-as-image.png)| Salva come immagine | Richiede un nome di file e salva il tracciato corrente (il contenuto della finestra nelle dimensioni della finestra) in un file di immagine. I formati disponibili sono `.png`, `.jpg`, `.bmp` e `.tif`. |
| ![Pulsante Salva come PDF](media/plotting-toolbar-06-save-as-pdf.png)| Salva come PDF | Salva il tracciato corrente in un file PDF, usando le dimensioni della finestra corrente. Il tracciato verrà nuovamente sottoposto a rendering in caso di ridimensionamento del PDF. |
| ![Pulsante Copia come bitmap](media/plotting-toolbar-07-copy-as-bitmap.png)| Copia come bitmap | Copia il tracciato negli Appunti come bitmap raster, usando le dimensioni della finestra corrente. |
| ![Pulsante Copia come metafile](media/plotting-toolbar-08-copy-as-metafile.png)| Copia come metafile | Copia il tracciato negli Appunti come un [metafile di Windows](https://en.wikipedia.org/wiki/Windows_Metafile) (Wikipedia). |
| ![Pulsante Rimuovi tracciato](media/plotting-toolbar-09-remove-plot.png)| Rimuovi tracciato | Rimuove il tracciato corrente dalla cronologia. |
| ![Pulsante Cancella tutti i tracciati](media/plotting-toolbar-10-clear-all-plots.png) | Cancella tutti i tracciati | Rimuove tutti i tracciati dalla cronologia (richiede una conferma). |

## <a name="multiple-plot-windows"></a>Più finestre dei tracciati

Poiché gli esperti di dati spesso lavorano con molti tracciati provenienti da set di dati diversi, RTVS consente di creare il numero necessario di finestre dei tracciati indipendenti. Le finestre possono essere disposte come si preferisce all'interno del frame di Visual Studio o anche all'esterno del frame. (Vedere [Personalizzare il layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md) per informazioni generali su ancoraggio e ridimensionamento delle finestre.)

Si crea una nuova finestra del tracciato usando il pulsante della barra degli strumenti o **R Tools**  >  **Traccia nuova** finestra  >  **tracciato**. La nuova finestra dei tracciati diventa la finestra *attiva*, in cui viene eseguito il rendering dei nuovi tracciati. Per modificare la finestra attiva, accedere a essa e selezionare il pulsante della barra degli strumenti **Attiva finestra dei tracciati** o **R Tools** > **Tracciati** > **Attiva finestra dei tracciati**.

I tracciati sono anch'essi oggetti indipendenti, quindi è possibile copiarli o spostarli tra le finestre dei tracciati usando il mouse per trascinare la selezione oppure i comandi **Copia**, **Taglia** e **Incolla** disponibili nel menu **Modifica** e nel menu di scelta rapida visualizzato facendo clic con il pulsante destro del mouse.

Il comportamento predefinito per il trascinamento della selezione è copy. per spostarsi, trascinare e rilasciare mentre si preme **MAIUSC.**

## <a name="plot-history"></a>Cronologia dei tracciati

I comandi dei tracciati vengono mantenuti nella cronologia dei tracciati per ogni finestra, assicurando il mantenimento di tutti i tracciati all'interno di una sessione. Per esplorare la cronologia, usare i pulsanti freccia sulla barra degli strumenti della finestra del tracciato o **CTRL** + **ALT** + **F11** e **CTRL** +  + **ALT+F12.** È anche possibile rimuovere singoli tracciati o cancellare di nuovo tutti i tracciati dalla finestra usando i pulsanti della barra degli strumenti o i comandi di menu  >  **Tracciati** di R Tools.

Per visualizzare l'intera raccolta di tracciati, aprire la finestra cronologia tracciato usando il pulsante della barra degli strumenti o la finestra Cronologia tracciati di **R**  >    >  **Tools**.
Nella cronologia è disponibile un elenco di miniature per i tracciati che sono stati visualizzati in tale finestra, raggruppate in base alle diverse finestre dei tracciati (o ai dispositivi). Con i pulsanti dello zoom presenti sulla barra degli strumenti è possibile modificare la dimensione delle miniature.

![Finestra cronologia dei tracciati](media/plotting-plot-history-window.png)

Per aprire un tracciato nella finestra associata, fare doppio clic sul tracciato, selezionarlo e quindi selezionare il **pulsante Mostra barra degli** strumenti Tracciato. In alternativa, fare clic con il pulsante destro del mouse sul tracciato e **scegliere Mostra tracciato**. È anche possibile selezionare un singolo tracciato e copiare, tagliare o eliminare dal menu di scelta rapida **o** Modifica.

La durata della cronologia dei tracciati in tutte le finestre è associata alla durata della sessione di R interattiva. Se si reimposta la sessione di R o si esce e si riavvia Visual Studio, la cronologia dei tracciati viene reimpostata.

## <a name="programmatically-manipulate-plot-windows"></a>Modificare a livello di programmazione le finestre dei tracciati

È possibile modificare a livello di programmazione le finestre dei tracciati dal codice R, usando i numeri dei dispositivi per identificare specifiche finestre dei tracciati.

- `dev.list()`: elenca tutti i dispositivi di grafica all'interno della sessione di R corrente.
- `dev.new()`: crea un nuovo dispositivo di grafica (una nuova finestra dei tracciati).
- `dev.set(<device number>)`: imposta il dispositivo di grafica attivo.
- `dev.off()`: elimina il dispositivo attivo.
