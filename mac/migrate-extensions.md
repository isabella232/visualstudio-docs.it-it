---
title: "Risoluzione dei problemi: Ricerca per categorie rilasciare una nuova versione dell'estensione esistente?"
description: Guida sull'aggiornamento delle estensioni esistenti tramite il flusso di lavoro di pubblicazione.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/14/2020
ms.technology: vs-ide-general
ms.assetid: 5DA76197-7859-421f-AC45-401F22F5D794
ms.topic: troubleshooting
ms.openlocfilehash: 862ae404571da44d9ca28db2c94d2ebeb39ce79f
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97488465"
---
# <a name="troubleshooting-how-do-i-release-a-new-version-of-my-existing-extension"></a>Risoluzione dei problemi: Ricerca per categorie rilasciare una nuova versione dell'estensione esistente?

> [!IMPORTANT]
> Attualmente, la creazione di nuove estensioni non è supportata ufficialmente in Visual Studio 2019 per Mac.

Il server del repository di estensione Visual Studio per Mac verrà spostato il 15 gennaio 2021. Questa operazione non influirà sugli utenti che hanno già scaricato l'estensione, ma modificheranno il modo in cui vengono pubblicate le nuove versioni dell'estensione dopo questa data.

Come autore di un'estensione esistente, è necessario seguire un flusso di lavoro diverso per rilasciare altri aggiornamenti. Questo processo è costituito da:
- Configurazione di un repository GitHub pubblico per ogni estensione
- Condivisione dell'URL del repository nel team di Visual Studio per Mac tramite la [lista di distribuzione di pubblicazione dell'estensione](mailto:vsmextpub@microsoft.com)
- Aggiornamento dell'estensione con la funzionalità versioni in GitHub


## <a name="initial-setup"></a>Configurazione iniziale 

Per continuare a pubblicare gli aggiornamenti nelle estensioni, è necessario creare un repository GitHub pubblico. Se si pubblicano più estensioni, è necessario disporre di un repository separato per ognuno, a meno che non sia sempre stata eseguita la versione e la pubblicazione insieme, nel qual caso è possibile usare un unico repository.

> [!NOTE]
> Anche se il repository GitHub per l'estensione deve essere pubblico, non è necessario ospitare alcun codice. Seguendo questo processo non è necessario disporre di codice in GitHub.


## <a name="share-the-location-of-your-repository"></a>Condividere il percorso del repository

Dopo aver configurato il repository, inviare un messaggio di posta elettronica all' [estensione Publishing mailing list](mailto:vsmextpub@microsoft.com) con l'URL.


## <a name="release-a-new-version"></a>Rilascia una nuova versione

Si userà il collegamento "crea una nuova versione" nella pagina principale del repository per iniziare il processo di aggiornamento dell'estensione. Dopo aver selezionato il collegamento, attenersi alla procedura seguente:

1. Aggiungere informazioni alla **versione tag della versione** nel formato seguente:

    > v \<releaseVersion> \- VSM\<targetVersion>

    Dove:
     - **&lt; releaseVersion &gt;** è il numero di versione dell'estensione
     - **&lt; TargetVersion &gt;** è la versione minima di Visual Studio per Mac l'estensione è la destinazione

2. Opzionale I campi **titolo** e **Descrizione** possono essere riempiti con tutte le informazioni desiderate; Questo flusso di lavoro non usa le informazioni in questi campi.

3. Verificare che la casella di controllo **versione non definitiva** sia deselezionata. Se questa opzione è selezionata, il rilascio non verrà prelevato dal processo di pubblicazione.

4. Alleghi i file **. mPack** che implementano l'estensione nella sezione **file binari** . È possibile alleghi più file con **estensione mPack** in una versione.

Visual Studio per Mac visualizzerà la versione più recente dell'estensione compatibile con l'installazione di Visual Studio per Mac usata per accedere al repository di estensione.

Fino a quando il repository GitHub è stato registrato con il team di Visual Studio per Mac, la versione dell'estensione verrà prelevata da Visual Studio per Mac entro 24 ore.

## <a name="additional-information"></a>Informazioni aggiuntive

- Le versioni non conformi ai requisiti descritti in precedenza non verranno pubblicate. 
- Dopo il 15 gennaio 2021, gli aggiornamenti delle estensioni vengono visualizzati solo in Visual Studio per Mac 8,0 o versione successiva.
- Le estensioni esistenti rimarranno disponibili per Visual Studio per Mac utenti senza alcuna azione da parte dell'utente. È sufficiente seguire le istruzioni riportate in questa guida se si pubblica una nuova versione dopo il 15 gennaio 2021.
