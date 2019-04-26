---
title: Documentazione della Guida offline
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca207f06640d5ef2df02d966b733d3065c80fce6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62975679"
---
# <a name="microsoft-help-viewer"></a>Microsoft Help Viewer

È possibile installare e visualizzare il contenuto di vari prodotti e tecnologie nel computer locale usando Microsoft Help Viewer. Questi prodotti includono Visual Studio, .NET Framework, riferimenti al linguaggio, SQL Server e lo sviluppo Windows. Help Viewer consente di:

- Scaricare set di contenuti, definiti anche libri. Ciò può essere utile se è necessario lavorare "offline" e mantenere l'accesso alla documentazione.

- Trovare gli argomenti in base al titolo visualizzando il sommario ed eseguendo ricerche nel sommario.

- Cercare gli argomenti nell'indice.

- Cercare informazioni tramite la ricerca full-text.

- Visualizzare e stampare gli argomenti, nonché contrassegnarli con un segnalibro.

Per installare Help Viewer, vedere [Installazione di Microsoft Help Viewer](../help-viewer/installation.md). Per iniziare a leggere gli argomenti della Guida in Help Viewer anziché online, accedere al menu **?** di Visual Studio e quindi scegliere **Imposta preferenza Guida** > **Avvia in Help Viewer**.

> [!TIP]
> Per scaricare il contenuto in locale e visualizzarlo quando non è disponibile una connessione a Internet, è anche possibile scaricare una versione PDF del contenuto. Molte documentazioni in docs.microsoft.com includono un collegamento nella parte inferiore del sommario (TOC) per scaricare un file PDF contenente tutti gli articoli del sommario.
>
> ![Scaricare il file PDF per la documentazione di Visual Studio](media/overview/download-pdf.png)

## <a name="help-viewer-tour"></a>Presentazione di Help Viewer

È possibile cercare informazioni nel contenuto installato usando le schede di navigazione, visualizzare il contenuto installato nella scheda o nelle schede dell'argomento e gestire il contenuto usando la scheda **Gestisci contenuto**. È anche possibile eseguire attività aggiuntive mediante i pulsanti della barra degli strumenti e trovare altre informazioni nell'angolo inferiore destro della finestra.

### <a name="navigation-tabs"></a>Schede di spostamento

|Scheda|Description|
|---|-----------|
|Sommario|Visualizza il contenuto installato come una gerarchia (sommario). È possibile specificare criteri per filtrare i titoli visualizzati.|
|Indice|Visualizza un elenco alfabetico di termini indicizzati. È possibile eseguire ricerche nell'indice, specificare i criteri per filtrare le voci e specificare che le voci di indice contengano o inizino con il testo desiderato.|
|Preferiti|È possibile contrassegnare argomenti come "Preferiti" scegliendo il pulsante **Aggiungi a Preferiti**. Gli argomenti così contrassegnati vengono visualizzati in questa scheda. Nella sezione **Cronologia** viene visualizzato un elenco di argomenti visualizzati di recente.|
|Cerca|In questa scheda è disponibile una casella di testo per cercare i termini in tutto il contenuto, inclusi il codice e i titoli degli argomenti.|

### <a name="view-topics"></a>Visualizza gli argomenti

Ogni argomento viene visualizzato in una scheda a parte ed è possibile aprire più argomenti contemporaneamente.

### <a name="manage-content"></a>Gestisci contenuto

È possibile installare, aggiornare, spostare ed eliminare il contenuto usando la scheda **Gestisci contenuto**. Nella parte superiore della scheda è possibile usare il controllo **Origine dell'installazione** per specificare se installare i libri da un percorso di rete, da un disco o da un URI. Nella casella **Percorso archivio locale** viene visualizzato il percorso in cui vengono installati i libri nel computer locale. Per spostare i libri in un percorso diverso, scegliere il pulsante **Sposta**.

L'elenco del contenuto visualizza i libri che è possibile installare o quelli già installati, se è disponibile un aggiornamento e le dimensioni di ciascun libro. È possibile installare o rimuovere uno o più libri scegliendo i collegamenti appropriati **Aggiungi** o **Rimuovi** e quindi scegliendo il pulsante **Aggiorna** nel riquadro **Modifiche in sospeso**. Se sono disponibili aggiornamenti per la documentazione già installata, è possibile aggiornare il contenuto scegliendo il collegamento **Fare clic qui per scaricare ora** nella parte inferiore della finestra. Inoltre, tutti i libri installati vengono aggiornati se sono disponibili aggiornamenti quando si installano altri libri.

> [!NOTE]
> La funzionalità della scheda **Gestisci contenuto** può essere diversa se l'amministratore di Help Viewer disattiva queste funzionalità o se non è disponibile l'accesso a Internet.

### <a name="toolbar-buttons"></a>Pulsanti della barra degli strumenti

La barra degli strumenti nella finestra **Help Viewer** contiene i pulsanti seguenti:

- Il pulsante **Mostra argomento nel contenuto** mostra la posizione dell'argomento nella scheda **Sommario**.

- Il pulsante **Aggiungi a Preferiti** aggiunge l'argomento attivo alla scheda **Preferiti**.

- Il pulsante **Trova in argomento** evidenzia il testo di ricerca nell'argomento attivo.

- Il pulsante**Stampa** stampa o mostra un'anteprima dell'argomento attivo.

- Il pulsante **Opzioni Visualizzatore** visualizza le impostazioni come la grandezza del testo visualizzato, il numero di risultati di ricerca da restituire, il numero di argomenti da mostrare nella cronologia e se verificare la disponibilità di aggiornamenti online.

- Il pulsante **Gestisci contenuto** rende attiva la scheda **Gestisci contenuto**.

- Il piccolo triangolo sul lato destro apre un elenco di schede, incluse le schede degli argomenti e la scheda **Gestisci contenuto**. È possibile scegliere un nome di scheda per renderla attiva.

## <a name="see-also"></a>Vedere anche

- [Installazione di Microsoft Help Viewer](../help-viewer/installation.md)
- [Guida dell'amministratore di Help Viewer](../help-viewer/administrator-guide.md)
- [Installare e gestire il contenuto locale](../help-viewer/install-manage-local-content.md)
