---
title: Documentazione della Guida offline
description: Installare e visualizzare la documentazione della Guida offline per vari prodotti e tecnologie, ad esempio Visual Studio e .NET, usando Microsoft Help Viewer.
ms.date: 11/02/2017
ms.topic: conceptual
f1_keywords:
- hv_general
helpviewer_keywords:
- Microsoft Help Viewer Help
- Help Viewer, printing a topic
- printing a topic [Help Viewer]
- Help Viewer, toolbar
- Help on Help [Help Viewer]
- Help Viewer, window components
- Help Viewer, navigating
- toolbar [Help Viewer]
ms.assetid: 74e41666-2ce8-4ac0-a0e5-3723d1e322c2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-help-viewer
ms.workload:
- multiple
ms.openlocfilehash: 4bf24de415421f0407f0de68357e607050acdbb6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041477"
---
# <a name="microsoft-help-viewer"></a>Microsoft Help Viewer

È possibile installare e visualizzare il contenuto di vari prodotti e tecnologie nel computer locale usando Microsoft Help Viewer. Questi prodotti includono Visual Studio, .NET, riferimenti al linguaggio, SQL Server e lo sviluppo Windows. Help Viewer consente di:

- Scaricare set di contenuti, definiti anche libri. Ciò può essere utile se è necessario lavorare "offline" e mantenere l'accesso alla documentazione.

- Trovare gli argomenti in base al titolo visualizzando il sommario ed eseguendo ricerche nel sommario.

- Cercare gli argomenti nell'indice.

- Cercare informazioni tramite la ricerca full-text.

- Visualizzare e stampare gli argomenti, nonché contrassegnarli con un segnalibro.

Per installare Help Viewer, vedere l Microsoft Help Viewer installazione [di](../help-viewer/installation.md). Per iniziare a leggere gli argomenti della Guida in Help Viewer anziché online, accedere al menu **?** di Visual Studio e quindi scegliere **Imposta preferenza Guida** > **Avvia in Help Viewer**.

> [!TIP]
> Per scaricare il contenuto in locale e visualizzarlo quando non è disponibile una connessione a Internet, è anche possibile scaricare una versione PDF del contenuto. Molte documentazioni in docs.microsoft.com includono un collegamento nella parte inferiore del sommario (TOC) per scaricare un file PDF contenente tutti gli articoli del sommario.
>
> ![Scaricare il file PDF per la documentazione di Visual Studio](media/overview/download-pdf.png)

## <a name="help-viewer-tour"></a>Presentazione di Help Viewer

È possibile trovare informazioni nel contenuto installato usando le schede di spostamento, visualizzare il contenuto installato nella scheda o nelle schede dell'argomento e gestire il contenuto usando **la scheda Gestisci** contenuto. È anche possibile eseguire attività aggiuntive usando i pulsanti sulla barra degli strumenti e trovare informazioni aggiuntive nell'angolo inferiore destro della finestra.

### <a name="navigation-tabs"></a>Schede di spostamento

|Scheda|Descrizione|
|---|-----------|
|Contenuto|Visualizza il contenuto installato come una gerarchia (sommario). È possibile specificare criteri per filtrare i titoli visualizzati.|
|Indice|Visualizza un elenco alfabetico di termini indicizzati. È possibile eseguire ricerche nell'indice, specificare i criteri per filtrare le voci e specificare che le voci di indice contengano o inizino con il testo desiderato.|
|Preferiti|È possibile aggiungere gli argomenti ai Preferiti scegliendo il **pulsante Aggiungi** a Preferiti per visualizzare gli argomenti in questa scheda. La **sezione** Cronologia visualizza un elenco di argomenti visualizzati di recente.|
|Cerca|In questa scheda è disponibile una casella di testo per cercare i termini in tutto il contenuto, inclusi il codice e i titoli degli argomenti.|

### <a name="view-topics"></a>Visualizza gli argomenti

Ogni argomento viene visualizzato in una scheda a parte ed è possibile aprire più argomenti contemporaneamente.

### <a name="manage-content"></a>Gestione del contenuto

È possibile installare, aggiornare, spostare ed eliminare contenuto usando la **scheda Gestisci** contenuto. Nella parte superiore della scheda è  possibile usare il controllo del codice sorgente Installazione per specificare se installare libri da un percorso di rete o da un disco o un URI. Nella casella **Percorso archivio locale** viene visualizzato il percorso in cui vengono installati i libri nel computer locale. Per spostare i libri in un percorso diverso, scegliere il pulsante **Sposta**.

L'elenco del contenuto visualizza i libri che è possibile installare o quelli già installati, se è disponibile un aggiornamento e le dimensioni di ciascun libro. È possibile installare o rimuovere uno o più libri scegliendo i collegamenti appropriati **Aggiungi** o **Rimuovi** e quindi scegliendo il pulsante **Aggiorna** nel riquadro **Modifiche in sospeso**. Se sono disponibili aggiornamenti per la documentazione già installata, è possibile aggiornare il contenuto scegliendo il collegamento **Fare clic qui per scaricare ora** nella parte inferiore della finestra. Inoltre, tutti i libri installati vengono aggiornati se sono disponibili aggiornamenti quando si installano altri libri.

> [!NOTE]
> La funzionalità della scheda **Gestisci contenuto** può essere diversa se l'amministratore di Help Viewer disattiva queste funzionalità o se non è disponibile l'accesso a Internet.

### <a name="toolbar-buttons"></a>Pulsanti della barra degli strumenti

La barra degli strumenti **nella finestra help viewer** contiene i pulsanti seguenti:

- Il pulsante **Mostra argomento nel contenuto** mostra la posizione dell'argomento nella scheda **Sommario**.

- Il pulsante **Aggiungi a Preferiti** aggiunge l'argomento attivo alla scheda **Preferiti**.

- Il pulsante **Trova in argomento** evidenzia il testo di ricerca nell'argomento attivo.

- Il pulsante **Stampa** stampa o mostra un'anteprima dell'argomento attivo.

- Il pulsante **Opzioni Visualizzatore** visualizza le impostazioni come la grandezza del testo visualizzato, il numero di risultati di ricerca da restituire, il numero di argomenti da mostrare nella cronologia e se verificare la disponibilità di aggiornamenti online.

- Il pulsante **Gestisci contenuto** rende attiva la scheda **Gestisci contenuto**.

- Il piccolo triangolo sul lato destro apre un elenco di schede, incluse le schede degli argomenti e **la scheda Gestisci** contenuto. È possibile scegliere un nome di scheda per renderla attiva.

## <a name="see-also"></a>Vedi anche

- [Microsoft Help Viewer installazione](../help-viewer/installation.md)
- [Guida dell'amministratore di Help Viewer](../help-viewer/administrator-guide.md)
- [Installare e gestire il contenuto locale](../help-viewer/install-manage-local-content.md)
