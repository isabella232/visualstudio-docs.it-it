---
title: 'Procedura dettagliata: Pubblicare un Visual Studio di estensione | Microsoft Docs'
description: Informazioni su come pubblicare un'estensione Visual Studio in Visual Studio Marketplace, che consente agli sviluppatori di cercare estensioni nuove e aggiornate.
ms.custom: SEO-VS-2020
ms.date: 01/15/2021
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 53fa4543bd56bd85f58b5c4251af19300a12fecf
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634484"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Procedura dettagliata: Pubblicare un'Visual Studio personalizzata

Questa procedura dettagliata illustra come pubblicare un'estensione Visual Studio in Visual Studio Marketplace. Quando si aggiunge l'estensione Visual Studio Marketplace, gli sviluppatori possono usare **estensioni** e aggiornamenti per cercare estensioni nuove e aggiornate.

## <a name="prerequisites"></a>Prerequisiti

 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-visual-studio-extension"></a>Creare un'Visual Studio predefinita

Questo articolo usa un'estensione VSPackage predefinita, ma i passaggi sono validi per ogni tipo di estensione.

- Creare un VSPackage in C# denominato `TestPublish` con un comando di menu. Per altre informazioni, vedere [Creare la prima estensione: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Creare il pacchetto dell'estensione

1. Aggiornare *l'estensione .vsixmanifest con* le informazioni corrette su nome del prodotto, autore e versione.

   ![aggiornare l'estensione vsixmanifest](media/update-extension-vsixmanifest.png)

2. Compilare l'estensione in **modalità** di rilascio. A questo punto l'estensione è in pacchetto come VSIX nella cartella \bin\Release.

3. È possibile fare doppio clic su VSIX per verificare l'installazione.

## <a name="test-the-extension"></a>Testare l'estensione

 Prima di distribuire l'estensione, compilarla e testarla per assicurarsi che sia installata correttamente nell'istanza sperimentale di Visual Studio.

1. In Visual Studio avviare il debug per aprire un'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale passare al menu **Strumenti** e fare clic su **Estensioni e aggiornamenti.** L'estensione TestPublish dovrebbe essere visualizzata nel riquadro centrale ed essere abilitata.

3. Nel menu **Strumenti** verificare che sia visualizzato il comando test.

## <a name="publish-the-extension-to-visual-studio-marketplace"></a>Pubblicare l'estensione in Visual Studio Marketplace

1. Assicurarsi di aver compilato la versione di rilascio dell'estensione e che sia aggiornata.

2. In un Web browser passare a [Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

3. Nell'angolo in alto a destra fare clic **su Accedi.**

4. Usare l'account Microsoft per accedere. Se non è disponibile un account Microsoft, è possibile crearne uno a questo punto.

5. Fare clic **su Pubblica estensioni**. Questa opzione consente di passare alla pagina di gestione per tutte le estensioni. Se non si ha un account editore, al momento viene richiesto di crearne uno.

   ![Upload a Marketplace](media/upload-to-marketplace.png)

6. Scegliere l'editore da usare per caricare l'estensione. È possibile modificare i server di pubblicazione facendo clic sui nomi degli editori elencati a sinistra. Fare **clic su Nuova** estensione e selezionare **Visual Studio**.

7. In **1: Upload** è possibile scegliere di caricare un file VSIX direttamente in Visual Studio Marketplace o semplicemente aggiungere un collegamento al proprio sito Web. In questo esempio viene caricata *l'estensione TestPublish.vsix.* Trascinare e rilasciare l'estensione oppure usare il **collegamento** di clic per cercare il file. Trovare l'estensione nella cartella \bin\Release del progetto.  Fare clic su **Continue**.

8. In **2: Specificare i dettagli dell'estensione**, alcuni campi vengono popolati automaticamente dal file *source.extension.vsixmanifest* dall'estensione. Altre informazioni su ognuno di essi sono riportate di seguito:

    * **Il nome** interno viene usato nell'URL della pagina dei dettagli dell'estensione. Ad esempio, se si pubblica un'estensione con il nome dell'editore "myname" e si specifica il nome interno come "my extension", viene restituito l'URL "marketplace.visualstudio \. com/items?itemName=myname.myextension" per la pagina dei dettagli dell'estensione.

    * **Nome visualizzato** dell'estensione. Questo nome viene popolato automaticamente dal file *source.extension.vsixmanifest.*

    * **Numero** di versione dell'estensione che si sta caricando. Questa versione viene popolata automaticamente dal file *source.extension.vsixmanifest.*

    * **L'ID VSIX** è l'identificatore univoco Visual Studio per l'estensione. Questo identificatore è obbligatorio se si vuole che l'estensione sia aggiornata automaticamente. Questo identificatore viene popolato automaticamente dal file *source.extension.vsixmanifest.*

    * **Logo** usato per l'estensione. Questo logo viene popolato automaticamente dal file *source.extension.vsixmanifest,* se specificato.

    * **Breve descrizione** delle attività dell'estensione. Questa descrizione viene popolata automaticamente dal file *source.extension.vsixmanifest.*

    * **Panoramica** è un buon punto in cui includere screenshot e informazioni dettagliate sulle funzionalità dell'estensione.

    * **Le Visual Studio supportate** consentono di scegliere le versioni di Visual Studio in cui l'estensione funzionerà. L'estensione viene installata solo in tali versioni.

    * **L Visual Studio edizione** supportata consente di scegliere le edizioni di Visual Studio su cui l'estensione funzionerà. L'estensione viene installata solo in tali edizioni.

    * **Type**. Il tipo di estensione più comune è **Strumenti**.

    * **Categorie**. Scegliere fino a tre che sono la scelta migliore per l'estensione.

    * **I tag** sono parole chiave che consentono agli utenti di trovare l'estensione. I tag consentono di aumentare la pertinenza della ricerca delle estensioni in Visual Studio Marketplace.

    * **La categoria di** prezzi è il costo dell'estensione.

    * **Il repository del** codice sorgente consente di condividere un collegamento al codice sorgente con la community.

    * **Consenti domande&A per l'estensione consente agli** utenti di lasciare domande nella pagina di immissione dell'estensione.

9. Fare **clic su Salva & Upload**. Questa opzione consente di tornare alla pagina di gestione dell'editore. L'estensione non è ancora stata pubblicata.

10. Per pubblicare l'estensione, fare clic con il pulsante destro del mouse sull'estensione e **scegliere Rendi pubblica.** Per visualizzare l'aspetto dell'estensione in Visual Studio Marketplace, selezionare **Visualizza estensione.** Per i numeri di acquisizione, fare clic su **Report**. Per apportare modifiche all'estensione, fare clic su **Modifica.**

    ![Menu di voce dell'estensione](media/extension-entry-menu.png)

11. Fare **clic su Rendi** pubblico per rendere pubblica l'estensione. Cercare Visual Studio Marketplace per l'estensione.

## <a name="update-a-published-extension-in-visual-studio-marketplace"></a>Aggiornare un'estensione pubblicata in Visual Studio Marketplace

Prima di iniziare, assicurarsi di aver compilato la nuova versione di rilascio dell'estensione e che sia aggiornata.

1.  In un Web browser passare a [Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

1.  Nell'angolo in alto a destra fare clic **su Accedi** e quindi accedere con il account Microsoft.

    :::image type="content" source="media/marketplace-upload-extension.png" alt-text="Screenshot che mostra la selezione di un file di estensione caricato in Esplora file.":::

1.  Fare **clic su Pubblica** estensioni e quindi scegliere l'editore da usare per caricare l'estensione aggiornata.

    :::image type="content" source="media/marketplace-select-extension-version.png" alt-text="Screenshot di Visual Studio Marketplace con il collegamento Pubblica estensioni evidenziato.":::

1.  Accanto all'estensione da aggiornare, posizionare il puntatore del mouse sui tre punti orizzontali e quindi scegliere **Modifica.**

    :::image type="content" source="media/marketplace-select-extension.png" alt-text="Screenshot che mostra la scelta di un'estensione da modificare.":::

1.  In **1: Upload,** dopo il nome del file VSIX, fare clic sull'icona a forma di matita per modificare l'estensione pubblicata.

     :::image type="content" source="media/marketplace-edit-extension-details.png" alt-text="Screenshot che mostra il clic sull'icona a forma di matita per modificare l'estensione.":::

1.  Passare al file VSIX dell'estensione aggiornato. Fare clic sul file e quindi su **Apri.**

    Caricamenti dell'estensione aggiornati.

    :::image type="content" source="media/marketplace-upload-extension-notification.png" alt-text="Screenshot di una notifica di caricamento del file dopo il caricamento di un'estensione modificata.":::

1. In **2:** Specificare i dettagli dell'estensione , alcuni dettagli sono di sola lettura per un aggiornamento dell'estensione o vengono popolati automaticamente dal file *source.extension.vsixmanifest* dall'estensione. Di seguito sono riportate altre informazioni sui dettagli dell'estensione:

    - **Nome interno** \* viene usato nell'URL della pagina dei dettagli dell'estensione. Ad esempio, se si pubblica un'estensione con il nome dell'editore "myname" e si specifica il nome interno come "my extension", viene restituito l'URL "marketplace.visualstudio.com/items?itemName=myname.myextension" per la pagina dei dettagli dell'estensione.

    - **Nome visualizzato** \* dell'estensione. Questo nome viene popolato automaticamente dal file *source.extension.vsixmanifest.*

    - **Versione** \* numero dell'estensione che si sta caricando. Questa versione viene popolata automaticamente dal file *source.extension.vsixmanifest.*

    - **ID VSIX** \* è l'identificatore univoco Visual Studio per l'estensione. Questo identificatore è obbligatorio se si vuole che l'estensione sia aggiornata automaticamente. Questo identificatore viene popolato automaticamente dal file *source.extension.vsixmanifest.*

    - **Logo** \* utilizzato per l'estensione. Questo logo viene popolato automaticamente dal file *source.extension.vsixmanifest,* se specificato.

    - **Breve descrizione** \* di ciò che fa l'estensione. Questa descrizione viene popolata automaticamente dal file *source.extension.vsixmanifest.*

    - **Panoramica** è un buon punto in cui includere screenshot e informazioni dettagliate sulle funzionalità dell'estensione.

    - **Versioni Visual Studio supportate** \* consente di scegliere le versioni di Visual Studio su cui l'estensione funzionerà. L'estensione viene installata solo in tali versioni.

    - **Edizione Visual Studio supportata** \* consente di scegliere le edizioni di Visual Studio su cui l'estensione funzionerà. L'estensione viene installata solo in tali edizioni.

    - **Type**. Il tipo di estensione più comune è **Strumenti**.

    - **Categorie**. Scegliere fino a tre che sono la scelta migliore per l'estensione.

    - **I tag** sono parole chiave che consentono agli utenti di trovare l'estensione. I tag consentono di aumentare la pertinenza della ricerca delle estensioni in Visual Studio Marketplace.

    - **La categoria di** prezzi è il costo dell'estensione.

    - **Il repository del** codice sorgente consente di condividere un collegamento al codice sorgente con la community.

    - **Consenti domande&A per l'estensione consente agli** utenti di lasciare domande nella pagina di immissione dell'estensione.

       \* Questo dettaglio non può essere modificato per un aggiornamento dell'estensione.

1. Fare **clic su Salva & Upload**. Questa opzione consente di tornare alla pagina di gestione dell'editore. L'estensione non è ancora stata pubblicata.

1. Per pubblicare l'estensione, fare clic con il pulsante destro del mouse sull'estensione e **scegliere Rendi pubblica.** Per visualizzare l'aspetto dell'estensione in Visual Studio Marketplace, selezionare **Visualizza estensione.** Per i numeri di acquisizione, fare clic **su Report**. Per apportare modifiche all'estensione, fare clic su **Modifica.**

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Aggiungere altri utenti per gestire l'account editore

Visual Studio Marketplace supporta la concessione di autorizzazioni aggiuntive agli utenti per l'accesso e la gestione di un account editore.

1. Passare all'account editore a cui si vogliono aggiungere altri utenti.

2. Selezionare **Membri e** fare clic su **Aggiungi.**

   ![Aggiungere un altro utente](media/add-users.png)

3. È quindi possibile specificare l'indirizzo di posta elettronica dell'utente che si vuole aggiungere e concedere il livello di accesso corretto in **Selezionare un ruolo.**  È possibile scegliere tra le opzioni seguenti:

   * **Autore:** l'utente può pubblicare estensioni, ma non può visualizzare o gestire le estensioni pubblicate da altri utenti.

   * **Lettore:** l'utente può visualizzare le estensioni, ma non può pubblicare o gestire le estensioni.

   * **Collaboratore:** l'utente può pubblicare e gestire le estensioni, ma non può modificare le impostazioni dell'editore o gestire l'accesso.

   * **Proprietario:** l'utente può pubblicare e gestire le estensioni, modificare le impostazioni dell'editore e gestire l'accesso.

## <a name="install-the-extension-from-visual-studio-marketplace"></a>Installare l'estensione da Visual Studio Marketplace

Ora che l'estensione è pubblicata, installarla in Visual Studio e testarla.

1. In Visual Studio scegliere Estensioni e aggiornamenti **dal** menu **Strumenti**.

2. Fare **clic su Online** e quindi cercare **TestPublish.**

3. Fare clic su **Download**. L'estensione è quindi pianificata per l'installazione.

4. Per completare l'installazione, chiudere tutte le istanze di Visual Studio.

## <a name="remove-the-extension"></a>Rimuovere l'estensione

È possibile rimuovere l'estensione Visual Studio Marketplace e dal computer.

### <a name="to-remove-the-extension-from-visual-studio-marketplace"></a>Per rimuovere l'estensione da Visual Studio Marketplace

1. Passare a [Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

2. Nell'angolo in alto a destra fare clic su **Pubblica** estensioni. Selezionare l'editore usato per pubblicare **TestPublish.** Verrà visualizzato **l'elenco per TestPublish.**

3. Fare clic con il pulsante destro del mouse sulla voce dell'estensione e **scegliere Rimuovi.** Viene chiesto di confermare se si vuole rimuovere l'estensione. Fare clic su **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Per rimuovere l'estensione dal computer

1. In Visual Studio scegliere Estensioni e aggiornamenti **dal** menu **Strumenti**.

2. Selezionare **TestPubblica** e quindi fare clic su **Disinstalla.** L'estensione è quindi pianificata per la disinstallazione.

3. Per completare la disinstallazione, chiudere tutte le istanze di Visual Studio.
