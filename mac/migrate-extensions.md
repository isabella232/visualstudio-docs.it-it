---
title: "Risoluzione dei problemi: Come rilasciare una nuova versione dell'estensione esistente?"
description: Guida all'aggiornamento delle estensioni esistenti tramite il flusso di lavoro di pubblicazione.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/14/2020
ms.technology: vs-ide-general
ms.assetid: 5DA76197-7859-421f-AC45-401F22F5D794
ms.topic: troubleshooting
ms.openlocfilehash: 921d61da140baa5b4dc36b79de18b0c260b1dd733e0b3089b0a4ff38f300f7ce
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121381581"
---
# <a name="troubleshooting-how-do-i-release-a-new-version-of-my-existing-extension"></a>Risoluzione dei problemi: Come rilasciare una nuova versione dell'estensione esistente?

> [!IMPORTANT]
> Attualmente, la creazione di nuove estensioni non è ufficialmente supportata in Visual Studio 2019 per Mac.

Il Visual Studio per Mac repository delle estensioni verrà spostata il 15 gennaio 2021. Questo spostamento non inciderà sugli utenti che hanno già scaricato l'estensione, ma modificherà la modalità di pubblicazione delle nuove versioni dell'estensione dopo questa data.

In quanto autore di un'estensione esistente, è necessario seguire un flusso di lavoro diverso per rilasciare altri aggiornamenti. Questo processo è costituito da:
- Configurazione di un repository GitHub pubblico per ogni estensione
- Condivisione dell'URL del repository con il team Visual Studio per Mac tramite la lista di distribuzione di pubblicazione [dell'estensione](mailto:vsmextpub@microsoft.com)
- Aggiornamento dell'estensione tramite la funzionalità versioni in GitHub


## <a name="initial-setup"></a>Configurazione iniziale 

Per continuare a pubblicare gli aggiornamenti per le estensioni, è necessario creare un repository GitHub pubblico. Se si pubblicano più estensioni, è necessario avere un repository separato per ognuna, a meno che non si eserciti sempre una versione e le si pubblicherà insieme, nel qual caso è possibile usare un singolo repository.

> [!NOTE]
> Anche se GitHub repository per l'estensione deve essere pubblico, non è necessario ospitare il codice. Per seguire questo processo non è necessario che il codice sia in GitHub.


## <a name="share-the-location-of-your-repository"></a>Condividere il percorso del repository

Dopo aver configurato il repository, inviare un messaggio di posta elettronica alla lista di distribuzione di pubblicazione [dell'estensione](mailto:vsmextpub@microsoft.com) con l'URL.


## <a name="release-a-new-version"></a>Rilasciare una nuova versione

Si userà il collegamento "Crea una nuova versione" nella pagina principale del repository per iniziare il processo di aggiornamento dell'estensione. Dopo aver selezionato il collegamento, seguire questa procedura:

1. Aggiungere informazioni alla **versione del tag** della versione nel formato seguente

    > v \<releaseVersion> \- vsm\<targetVersion>

    Dove:
     - **&lt; releaseVersion &gt; è** il numero di versione dell'estensione
     - **&lt; targetVersion &gt; è** la versione minima di Visual Studio per Mac destinazione dell'estensione

2. (Facoltativo) I **campi** del **titolo** e della descrizione possono essere compilati con tutte le informazioni necessarie. questo flusso di lavoro non usa le informazioni in questi campi.

3. Assicurarsi che **la casella di controllo versione non** definitiva sia deselezionata. Se è selezionata, la versione non verrà prelevata da questo processo di pubblicazione.

4. Allegare i file con estensione **mpack** che implementano l'estensione nella **sezione binaries.** È possibile allegare più **file con estensione mpack** in una versione.

Visual Studio per Mac verrà visualizzata la versione più recente dell'estensione compatibile con l'installazione Visual Studio per Mac usata per accedere al repository delle estensioni.

Se il repository di GitHub è stato registrato con il team Visual Studio per Mac, la versione dell'estensione verrà prelevata entro Visual Studio per Mac 24 ore.

## <a name="additional-information"></a>Informazioni aggiuntive

- Le versioni non conformi ai requisiti descritti in precedenza non verranno pubblicate. 
- Dopo il 15 gennaio 2021, gli aggiornamenti delle estensioni verranno visualizzati solo in Visual Studio per Mac 8.0 o versione più recente.
- Le estensioni esistenti rimarranno disponibili per Visual Studio per Mac utenti senza alcuna azione da parte dell'utente. È necessario seguire le istruzioni riportate in questa guida solo se si pubblica una nuova versione dopo il 15 gennaio 2021.
