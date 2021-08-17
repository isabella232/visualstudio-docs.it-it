---
title: Pubblicare ClickOnce'applicazione usando la Pubblicazione guidata
description: Informazioni sull'uso della Pubblicazione guidata per rendere l'applicazione ClickOnce disponibile agli utenti, incluse le proprietà di pubblicazione da usare.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 195dc94991def92e1612e7f1752d348e1eb8d578
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089966"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Procedura: Pubblicare un'applicazione ClickOnce mediante la Pubblicazione guidata
Per rendere disponibile un'applicazione ClickOnce agli utenti, è necessario pubblicarla in un una condivisione file, in un percorso, in un server FTP o su un supporto rimovibile. Per pubblicare l'applicazione, usare la Pubblicazione guidata. Altre proprietà relative alla pubblicazione sono disponibili nella pagina **Pubblica** di **Creazione progetti**. Per altre informazioni, vedere [Pubblicazione di applicazioni ClickOnce](../deployment/publishing-clickonce-applications.md).

Prima di eseguire la Pubblicazione guidata, impostare correttamente le opzioni di pubblicazione. Ad esempio, se si vuole designare una chiave per la firma dell'applicazione ClickOnce, accedere alla pagina **Firma** di **Creazione progetti**. Per altre informazioni, vedere [Proteggere ClickOnce applicazioni](../deployment/securing-clickonce-applications.md).

> [!NOTE]
> Quando si installa più di una versione di un'applicazione usando ClickOnce, l'installazione sposta le versioni precedenti dell'applicazione in una cartella denominata *Archive* nel percorso di pubblicazione specificato. L'archiviazione delle versioni precedenti consente di mantenere pulita la directory di installazione.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero non corrispondere a quelli descritti nella Guida in quanto dipendono dall'edizione o dalle impostazioni in uso. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="to-publish-to-a-file-share-or-path"></a>Per pubblicare in una condivisione file o in un percorso

1. In **Esplora soluzioni** selezionare il progetto di applicazione.

2. Scegliere **Pubblica** **nomeprogetto** dal menu *Compila*.

    Verrà visualizzata la Pubblicazione guidata.

3. Nella pagina **Specificare la posizione in cui pubblicare l'applicazione** immettere l'indirizzo valido di un server FTP o un percorso file corretto usando uno dei formati indicati e quindi fare clic su **Avanti**.

4. Nella pagina **Specificare la modalità di installazione dell'applicazione utilizzata dagli utenti** selezionare il percorso a cui accederanno gli utenti per installare l'applicazione:

   - Se gli utenti eseguiranno l'installazione da un sito Web, fare clic su **Da un sito Web** e immettere un URL corrispondente al percorso file specificato nel passaggio precedente. Fare clic su **Avanti**. In genere questa opzione viene usata quando si specifica un indirizzo FTP come percorso di pubblicazione. Il download diretto da FTP non è supportato, di conseguenza, è necessario specificare un URL.

   - Se gli utenti installeranno l'applicazione direttamente dalla condivisione file, fare clic su **Da un percorso UNC o condivisione file** e quindi scegliere **Avanti**. Questo vale per i percorsi di pubblicazione nel formato *c:\deploy\myapp* o *\\\server\myapp*.

   - Se gli utenti eseguiranno l'installazione da un supporto rimovibile, fare clic su **Da CD-ROM o DVD-ROM** e quindi scegliere **Avanti**.

5. Nella pagina **Specificare se l'applicazione sarà disponibile offline** fare clic sull'opzione appropriata:

   - Se si vuole consentire l'esecuzione dell'applicazione anche quando l'utente è disconnesso dalla rete, fare clic su **Applicazione disponibile online o offline**. Nel menu **Start** verrà creato un collegamento per l'applicazione.

   - Se si vuole che l'applicazione venga eseguita direttamente dalla posizione di pubblicazione, fare clic su **Applicazione disponibile solo online**. Nel menu **Start** non verrà creato alcun collegamento.

     Fare clic su **Avanti** per continuare.

6. Fare clic su **Fine** per pubblicare l'applicazione.

    Lo stato di pubblicazione è visualizzato nell'area di notifica dello stato.

## <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Per pubblicare su CD-ROM o DVD-ROM

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul progetto di applicazione e scegliere **Proprietà**.

    Verrà **Project finestra di progettazione.**

2. Fare clic sulla scheda **Pubblica** per aprire la pagina **Pubblica** in **Creazione progetti** e quindi fare clic sul pulsante **Pubblicazione guidata**.

    Verrà visualizzata la Pubblicazione guidata.

3. Nella pagina **Specificare la posizione in cui pubblicare l'applicazione** immettere il percorso del file o il percorso FTP in cui verrà pubblicata l'applicazione, ad esempio *d:\deploy*. Quindi, fare clic su **Avanti** per continuare.

4. Nella pagina **Specificare la modalità di installazione dell'applicazione usata dagli utenti** fare clic su **Da CD-ROM o DVD-ROM** e quindi fare clic su **Avanti**.

   > [!NOTE]
   > Se si vuole che l'installazione venga eseguita automaticamente quando il CD-ROM viene inserito nell'unità, aprire la pagina **Pubblica** in **Creazione progetti**, fare clic sul pulsante **Opzioni** e quindi nella procedura guidata **Opzioni di pubblicazione** selezionare **Per le installazioni da CD, avvia automaticamente l'installazione all'inserimento del CD**.

5. Se l'applicazione viene distribuita tramite CD-ROM, sarà necessario pubblicare gli aggiornamenti in un sito Web. Nella pagina **Specificare la posizione per il controllo degli aggiornamenti per l'applicazione** scegliere un'opzione di aggiornamento:

   - Se l'applicazione verificherà la disponibilità di aggiornamenti, fare clic su **Controlla la disponibilità di aggiornamenti dal seguente percorso** e immettere il percorso in cui verranno pubblicati gli aggiornamenti. Può trattarsi di un percorso di file, un sito Web o un server FTP.

   - Se l'applicazione non verificherà la disponibilità di aggiornamenti,fare clic su **Non controllare la disponibilità di aggiornamenti**.

     Fare clic su **Avanti** per continuare.

6. Fare clic su **Fine** per pubblicare l'applicazione.

    Lo stato di pubblicazione è visualizzato nell'area di notifica dello stato.

   > [!NOTE]
   > Al termine della pubblicazione, sarà necessario usare un masterizzatore CD o DVD per copiare i file dal percorso specificato nel passaggio 3 al CD-ROM o DVD-ROM.

## <a name="see-also"></a>Vedi anche

- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Proteggere le applicazioni ClickOnce](../deployment/securing-clickonce-applications.md)
- [Distribuzione di una Office di distribuzione tramite ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)