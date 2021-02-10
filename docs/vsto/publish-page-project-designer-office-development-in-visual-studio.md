---
title: Pagina pubblica, Progettazione progetti (sviluppo per Office)
description: Informazioni sulla modalità di utilizzo della pagina pubblica di progettazione progetti in Visual Studio per configurare le proprietà per la distribuzione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bc80a71516f1de8f2a6943d9df7b02341ea786aa
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971726"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Pagina pubblica, Progettazione progetti (sviluppo per Office in Visual Studio)
  La pagina **Pubblica** di **Creazione progetti** viene usata per configurare le proprietà per la distribuzione.

 Per accedere a questa pagina, selezionare il progetto in **Esplora soluzioni**, quindi, nel menu **Progetto** , scegliere *NomeProgetto* **Proprietà**. Se la pagina **Pubblica** non viene visualizzata, scegliere la scheda **Pubblica** .

> [!NOTE]
> È anche possibile impostare il percorso di pubblicazione nella **Pubblicazione guidata**. Per altre informazioni, vedere [procedura: pubblicare una soluzione Office tramite ClickOnce](/previous-versions/bb386095(v=vs.110)).

## <a name="uielement-list"></a>Elenco degli elementi di interfaccia
 Percorso **cartella di pubblicazione (sito Web, server FTP o percorso file)** Obbligatorio.

 La posizione della cartella di pubblicazione è la directory in cui Visual Studio copia i file della soluzione, ad esempio i manifesti, gli assembly e altri file della compilazione. È necessario l'accesso in scrittura a questa directory.

 Le opzioni includono il computer locale, una condivisione file UNC o un sito Web HTTP/HTTPS. Il percorso può essere local (*c:\foldername\publishfolder*), relativo (*Publish \\*) o un percorso completo (*\\ \servername\foldername* o http://<em>ServerName/FolderName</em>).

 Per impostazione predefinita, il percorso di pubblicazione è *http://localhost/projectname/* se IIS è installato o la directory di *pubblicazione \\* se IIS non è installato.

 **URL cartella di installazione** Opzionale.

 L'URL della cartella di installazione è la directory dalla quale l'utente finale installa la personalizzazione. È anche il percorso usato dalla soluzione per controllare la disponibilità di aggiornamenti. Il percorso può essere uguale a quello della cartella di pubblicazione, ma non è obbligatorio.

 Le opzioni includono il computer locale, una condivisione file UNC o un sito Web HTTP/HTTPS. Il percorso può essere local (*c:\foldername\publishfolder*), relativo (*Publish \\*) o un percorso completo (*\\ \servername\foldername* o http://<em>ServerName/FolderName</em>). Tutti i percorsi HTTP/HTTPS devono essere creati con caratteri US-ASCII. I caratteri Unicode non sono supportati.

 Se il percorso di installazione è impostato, i file di personalizzazione devono trovarsi nel percorso in cui gli utenti installano la personalizzazione. Il percorso deve essere impostato solo se si conosce il percorso di distribuzione finale.

 Se i file di installazione si trovano in un percorso relativo al documento o al programma di installazione, ad esempio l'opzione CD, lasciare vuota questa casella.

 Questo valore può essere assegnato successivamente da un amministratore. Per altre informazioni, vedere [procedura: modificare il percorso di installazione di una soluzione Office](/previous-versions/bb608626(v=vs.110)).

 **Prerequisiti** I prerequisiti possono essere inclusi nel programma di installazione o scaricati su richiesta durante l'installazione.

- **Scarica prerequisiti dal sito Web del fornitore del componente**: usare questa opzione per scaricare questi prerequisiti da Microsoft.

- **Scarica prerequisiti dallo stesso percorso dell'applicazione**: usare questa opzione per incorporare i prerequisiti nel programma di installazione. Se i file dei prerequisiti vengono inclusi nel programma di installazione, le dimensioni della soluzione aumentano.

- **Scarica prerequisiti dal seguente percorso**: usare questa opzione per rendere disponibili i prerequisiti agli utenti finali separatamente tramite un altro programma di installazione in una pagina Web o in una condivisione di rete.

  **Aggiornamenti** di L'intervallo di aggiornamento determina la frequenza con cui la soluzione controlla la disponibilità di aggiornamenti. L'impostazione predefinita è ogni sette giorni.

  Il controllo della disponibilità di aggiornamenti ogni volta che viene caricata una personalizzazione a livello di documento o un componente aggiuntivo VSTO manterrebbe aggiornati i componenti, ma influirebbe sulle prestazioni di avvio.

  Se si esegue la distribuzione tramite CD o unità rimovibile, selezionare l'impostazione **Non controllare mai**.

  **Opzioni (descrizione)** È possibile impostare le opzioni di pubblicazione per le proprietà seguenti:

- Lingua di pubblicazione: le impostazioni locali della soluzione Office.

- Nome editore: il nome della società o dello sviluppatore, come visualizzato in **Installazione applicazioni** o **Programmi e funzionalità**.

- Nome prodotto: il nome della soluzione Office, come visualizzato in **Installazione applicazioni** o **Programmi e funzionalità**.

- URL supporto tecnico: la posizione che gli utenti finali possono usare per contattare il supporto tecnico per la soluzione Office.

  **Opzioni (impostazioni Office)** È possibile impostare le opzioni di pubblicazione per le proprietà seguenti:

- Nome soluzione: il nome della soluzione Office, come visualizzato nell'applicazione di Office.

- Descrizione: la descrizione della soluzione Office, come visualizzata nell'applicazione di Office.

- Comportamento di caricamento del componente aggiuntivo VSTO.

  - Carica all'avvio: specifica che il componente aggiuntivo VSTO viene caricato all'avvio dell'applicazione di Office.

  - Carica su richiesta: specifica che il componente aggiuntivo VSTO viene caricato quando lo richiede l'applicazione, ad esempio quando un utente fa clic su un elemento dell'interfaccia utente che usa la funzionalità nel componente aggiuntivo VSTO.

  **Lingua di pubblicazione** Questa opzione imposta la lingua delle condizioni di licenza software Microsoft e include i Language Pack nell'elenco dei prerequisiti. Non influisce sulla lingua della personalizzazione. La lingua del programma di installazione viene determinata dalle lingue installate di Visual Studio.

  Per ulteriori informazioni su come modificare la **lingua di pubblicazione**, vedere [procedura: modificare la lingua di pubblicazione per un'applicazione ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md).

  **Versione di pubblicazione** Imposta il numero di versione per la personalizzazione. Quando il numero di versione viene modificato, l'applicazione viene pubblicata come aggiornamento. Viene creata una nuova cartella per ogni versione durante il processo di compilazione per evitare la sovrascrittura della versione precedentemente pubblicata. Ogni parte della versione di pubblicazione (**Principale**, **Secondaria**, **Compilazione**, **Revisione**) può contenere fino a cinque cifre.

  **Incrementa automaticamente revisione a ogni versione** Opzionale. Quando è selezionata (impostazione predefinita), la parte **Revisione** del numero di versione viene incrementata di un'unità ogni volta che viene pubblicata la personalizzazione. In questo modo la personalizzazione viene pubblicata come aggiornamento.

  **Pubblica ora** Pubblica l'applicazione usando le impostazioni correnti. Equivale al pulsante **Fine** nella **Pubblicazione guidata**.

## <a name="see-also"></a>Vedi anche

- [Distribuire una soluzione Office](../vsto/deploying-an-office-solution.md)
- [Distribuire una soluzione Office tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Prerequisiti della soluzione Office per la distribuzione](/previous-versions/bb608617(v=vs.110))