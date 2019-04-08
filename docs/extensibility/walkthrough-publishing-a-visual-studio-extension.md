---
title: "Procedura dettagliata: Pubblicazione di un'estensione di Visual Studio | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 34a9a97e018642660d7424b0bfce2a1bbbc9c073
ms.sourcegitcommit: 4c7a0c2d712eb24609216577a793e912a6083eaf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2019
ms.locfileid: "57983520"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Procedura dettagliata: Pubblicare un'estensione di Visual Studio

Questa procedura dettagliata illustra come pubblicare un'estensione di Visual Studio in Visual Studio Marketplace. Quando si aggiunge l'estensione nel Marketplace, gli sviluppatori possono utilizzare **estensioni e aggiornamenti** per cercare estensioni nuove e aggiornate.

## <a name="prerequisites"></a>Prerequisiti

 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Creare un'estensione di Visual Studio

Questo articolo usa un'estensione VSPackage predefinito, ma i passaggi sono validi per ogni tipo di estensione.

1. Creare un pacchetto VSPackage in C# denominato `TestPublish` che dispone di un comando di menu. Per altre informazioni, vedere [creare la prima estensione: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Creare un pacchetto di estensione

1. Aggiornare l'estensione *vsixmanifest* con le informazioni corrette sul nome del prodotto, autore e versione.

   ![update extension vsixmanifest](media/update-extension-vsixmanifest.png)

2. Compilare l'estensione **rilascio** modalità. L'estensione è ora fornita come un progetto VSIX nella cartella \bin\Release.

3. È possibile fare doppio clic il progetto VSIX per verificare l'installazione.

## <a name="test-the-extension"></a>Testare l'estensione

 Prima di distribuire l'estensione, compilare e testare per verificare che sia installato correttamente nell'istanza sperimentale di Visual Studio.

1. In Visual Studio, avviare il debug per aprire un'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale, passare al **degli strumenti** dal menu **estensioni e aggiornamenti**. L'estensione TestPublish dovrebbe essere visualizzato nel riquadro centrale e abilitato.

3. Nel **strumenti** menu, assicurarsi che venga visualizzato il comando di test.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Pubblicare l'estensione per Visual Studio Marketplace

1. Assicurarsi di avere compilato la versione dell'estensione e che sia aggiornato.

2. In un web browser, aprire il [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) sito Web.

3. Nell'angolo superiore destro, fare clic su **Accedi**.

4. Usare l'account Microsoft per accedere. Se non hai un account Microsoft, è possibile creare uno a questo punto.

5. Fare clic su **pubblicare estensioni**.  Questa opzione si passa alla pagina di gestione per tutte le estensioni. Se non hai un account editore, viene chiesto di crearne uno in questo momento.

   ![Caricare in Marketplace](media/upload-to-marketplace.png)

6. Scegliere il server di pubblicazione da usare per caricare l'estensione. È possibile modificare i server di pubblicazione facendo clic sui nomi di server di pubblicazione elencati a sinistra. Fare clic su **nuova estensione** e selezionare **Visual Studio**.

7. In **1: Carica estensione**, è possibile scegliere di caricare un file VSIX direttamente in Visual Studio Marketplace o è sufficiente aggiungere un collegamento al proprio sito Web. In questo esempio, l'estensione *TestPublish.vsix* viene caricato. Trascinare l'estensione oppure usare il **fare clic su** collegamento per cercare il file. Trovare l'estensione nella cartella \bin\Release del progetto.  Scegliere **Continua**.

8. In **2: Fornire i dettagli dell'estensione**, alcuni campi sono popolati automaticamente dal *vsixmanifest* dall'estensione di file. Per informazioni dettagliate su ognuna di seguito:

    * **Nome interno** viene usato nell'URL della pagina dei dettagli dell'estensione. Per un esempio, la pubblicazione di un'estensione con il nome del server di pubblicazione "myname" e specificando il nome interno per essere "my extension" i risultati in un URL di "marketplace.visualstudio\.com/items?itemName=myname.myextension" per i dettagli dell'estensione pagina.

    * **Nome visualizzato** dell'estensione. Questo nome viene popolato automaticamente dal *vsixmanifest* file.

    * **Versione** numerica dell'estensione si sta caricando. Questa versione viene compilato automaticamente dal *vsixmanifest* file.

    * **ID VSIX** è l'identificatore univoco utilizzato per l'estensione per Visual Studio. Questo identificatore è obbligatorio se si vuole avere l'estensione aggiornate automaticamente. Questo identificatore viene popolato automaticamente dal *vsixmanifest* file.

   * **Logo** che viene usato per l'estensione. Questo logo viene popolato automaticamente dal *vsixmanifest* file se specificato.

     * **Descrizione breve** delle funzionalità dell'estensione. Questa descrizione viene popolato automaticamente dal *vsixmanifest* file.

     * **Panoramica** è un buon punto da includere le schermate e informazioni dettagliate sulla funzione associata l'estensione.

     * **Le versioni di Visual Studio supportate** consente di scegliere quali versioni di Visual Studio funzionalità sarà disponibile l'estensione. L'estensione viene installata solo per tali versioni.

     * * * Supportato edition consente di scegliere quali edizioni di Visual Studio sarà disponibile l'estensione di Visual Studio. L'estensione viene installata solo per queste edizioni.

     * **Tipo**. Il tipo più comune delle estensioni sono **strumenti**.

     * **Categorie**. Selezionare un massimo di tre che sono una soluzione ottimale per l'estensione.

     * **I tag** sono parole chiave che consentono agli utenti di trovare l'estensione. I tag consentono di aumentare la rilevanza di ricerca delle estensioni nel Marketplace.

     * **Categoria di prezzi** è il costo dell'estensione.

     * **Repository del codice sorgente** consente di condividere un collegamento al codice sorgente con la community.

     * **Consenti domande e risposte per l'estensione** consente agli utenti di lasciare domande nella pagina di voce di estensione.

9. Fare clic su **Salva e carica**. Pagina Gestisci visualizzata questa opzione di nuovo il server di pubblicazione. L'estensione non è ancora stata pubblicata. Per pubblicare l'estensione, fare clic sull'estensione e selezionare **Rendi pubblico**. È possibile visualizzare come l'estensione sarà simile in Marketplace, selezionando **Visualizza l'estensione**. Per i numeri di acquisizione, fare clic su **report**. Per apportare modifiche all'estensione, fare clic su **modifica**.

   ![Menu dell'estensione movimento](media/extension-entry-menu.png)

10. Dopo aver fatto clic **Rendi pubblico**, l'estensione è ora pubblica. Visual Studio Marketplace per l'estensione di ricerca.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Aggiungere altri utenti per gestire l'account editore

Marketplace supporta la concessione di autorizzazioni aggiuntive agli utenti per accedere e gestire un account editore.

1. Passare all'account del server di pubblicazione che si desidera aggiungere altri utenti a.

2. Selezionare **membri** e fare clic su **Add**.

   ![Aggiungere altro utente](media/add-users.png)

3. È quindi possibile specificare l'indirizzo di posta elettronica dell'utente che si desidera aggiungere e concedere il corretto livello di accesso nel **selezionare un ruolo**.  È possibile scegliere una delle opzioni seguenti:

   * **Creatore**: L'utente può pubblicare estensioni, ma non è possibile visualizzare o gestire estensioni pubblicate da altri utenti.

   * **Lettore**: L'utente può visualizzare le estensioni, ma non è possibile pubblicare o gestire le estensioni.

   * **Collaboratore**: L'utente può pubblicare e gestire le estensioni, ma non è possibile modificare le impostazioni di pubblicazione o gestire l'accesso.

   * **Owner**: L'utente può pubblicare e gestire le estensioni, modificare le impostazioni di pubblicazione e gestire l'accesso.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installare l'estensione da Visual Studio Marketplace

Ora che la pubblicazione dell'estensione, installarlo in Visual Studio e testarlo.

1. In Visual Studio sul **degli strumenti** menu, fare clic su **estensioni e aggiornamenti**.

2. Fare clic su **Online** e quindi cercare **TestPublish**.

3. Scegliere **Download**. Quindi, l'estensione è pianificata per l'installazione.

4. Per completare l'installazione, chiudere tutte le istanze di Visual Studio.

## <a name="remove-the-extension"></a>Rimuovere l'estensione.

È possibile rimuovere l'estensione da Visual Studio Marketplace e dal computer.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Per rimuovere l'estensione da Visual Studio Marketplace

1. Aprire il [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) sito Web.

2. Nell'angolo superiore destro, fare clic su **pubblica** estensioni. Selezionare il server di pubblicazione usato per pubblicare **TestPublish**. L'elenco relativo al **TestPublish** viene visualizzata.

3. Fare doppio clic sulla voce estensione e fare clic su **rimuovere**. Viene chiesto di confermare se si vuole rimuovere l'estensione. Fare clic su **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Per rimuovere l'estensione dal computer

1. In Visual Studio sul **degli strumenti** menu, fare clic su **estensioni e aggiornamenti**.

2. Selezionare **TestPublish** e quindi fare clic su **Disinstalla**. L'estensione è pianificata quindi per la disinstallazione.

3. Per completare la disinstallazione, chiudere tutte le istanze di Visual Studio.
