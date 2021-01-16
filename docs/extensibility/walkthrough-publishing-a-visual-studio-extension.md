---
title: "Procedura dettagliata: pubblicare un'estensione di Visual Studio | Microsoft Docs"
description: Informazioni su come pubblicare un'estensione di Visual Studio in Visual Studio Marketplace, che consente agli sviluppatori di cercare estensioni nuove e aggiornate.
ms.custom: SEO-VS-2020
ms.date: 01/15/2021
ms.topic: how-to
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 01a46f54bfbce6126c16fa418d5c4bef53afd09b
ms.sourcegitcommit: 7a5c4f60667b5792f876953d55192b49a73f5fe9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2021
ms.locfileid: "98533919"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Procedura dettagliata: pubblicare un'estensione di Visual Studio

Questa procedura dettagliata illustra come pubblicare un'estensione di Visual Studio per Visual Studio Marketplace. Quando si aggiunge l'estensione a Visual Studio Marketplace, gli sviluppatori possono usare **estensioni e aggiornamenti** per cercare estensioni nuove e aggiornate.

## <a name="prerequisites"></a>Prerequisiti

 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-visual-studio-extension"></a>Creare un'estensione di Visual Studio

Questo articolo usa un'estensione VSPackage predefinita, ma i passaggi sono validi per ogni tipo di estensione.

- Creare un pacchetto VSPackage in C# denominato `TestPublish` con un comando di menu. Per altre informazioni, vedere [creare la prima estensione: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Creare il pacchetto dell'estensione

1. Aggiornare l'estensione *. vsixmanifest* con le informazioni corrette sul nome del prodotto, l'autore e la versione.

   ![aggiornamento dell'estensione vsixmanifest](media/update-extension-vsixmanifest.png)

2. Compilare l'estensione in modalità di **rilascio** . A questo punto l'estensione viene assemblata come VSIX nella cartella \bin\Release.

3. È possibile fare doppio clic su VSIX per verificare l'installazione.

## <a name="test-the-extension"></a>Testare l'estensione

 Prima di distribuire l'estensione, compilarla e testarla per assicurarsi che sia installata correttamente nell'istanza sperimentale di Visual Studio.

1. In Visual Studio avviare il debug per aprire un'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale, andare al menu **strumenti** e fare clic su **estensioni e aggiornamenti**. L'estensione TestPublish dovrebbe essere visualizzata nel riquadro centrale ed essere abilitata.

3. Nel menu **strumenti** verificare che sia visualizzato il comando test.

## <a name="publish-the-extension-to-visual-studio-marketplace"></a>Pubblicare l'estensione in Visual Studio Marketplace

1. Assicurarsi di aver compilato la versione di rilascio dell'estensione e che sia aggiornata.

2. In un Web browser passare a [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

3. Nell'angolo in alto a destra fare clic su **Sign in (accedi**).

4. Usare l'account Microsoft per accedere. Se non si dispone di un account Microsoft, è possibile crearne uno a questo punto.

5. Fare clic su **Publish extensions**. Questa opzione consente di passare alla pagina Gestisci per tutte le estensioni. Se non si dispone di un account editore, viene richiesto di crearne uno in questo momento.

   ![Carica nel Marketplace](media/upload-to-marketplace.png)

6. Scegliere il server di pubblicazione che si vuole usare per caricare l'estensione. È possibile modificare i server di pubblicazione facendo clic sui nomi dei server di pubblicazione elencati a sinistra. Fare clic su **nuova estensione** e selezionare **Visual Studio**.

7. In **1: caricare l'estensione**, è possibile scegliere di caricare un file VSIX direttamente in Visual Studio Marketplace o semplicemente aggiungere un collegamento al proprio sito Web. In questo esempio viene caricata l'estensione *TestPublish. vsix* . Trascinare e rilasciare l'estensione o usare il collegamento **fare clic** per cercare il file. Trovare l'estensione nella cartella \bin\Release del progetto.  Fare clic su **Continue**.

8. In **2: specificare i dettagli dell'estensione**. alcuni campi vengono popolati automaticamente dal file *source. Extension. vsixmanifest* dall'estensione. Per ulteriori dettagli, vedere:

    * Il **nome interno** viene usato nell'URL della pagina dei dettagli dell'estensione. Per un esempio, la pubblicazione di un'estensione con il nome del server di pubblicazione "nome" e la specifica del nome interno come "My extension" genera un URL "Marketplace. VisualStudio \. com/items? ItemName = nome. estensione" per la pagina dei dettagli dell'estensione.

    * **Nome visualizzato** dell'estensione. Questo nome viene popolato automaticamente dal file *source. Extension. vsixmanifest* .

    * Numero di **versione** dell'estensione che si sta caricando. Questa versione viene popolata automaticamente dal file *source. Extension. vsixmanifest* .

    * **VSIX ID** è l'identificatore univoco usato da Visual Studio per l'estensione. Questo identificatore è obbligatorio se si desidera che l'estensione venga aggiornata automaticamente. Questo identificatore viene popolato automaticamente dal file *source. Extension. vsixmanifest* .

    * **Logo** usato per l'estensione. Questo logo viene popolato automaticamente dal file *source. Extension. vsixmanifest* , se specificato.

    * **Breve descrizione** dell'estensione. Questa descrizione viene popolata automaticamente dal file *source. Extension. vsixmanifest* .

    * **Panoramica** è una posizione ideale per includere schermate e informazioni dettagliate sul funzionamento dell'estensione.

    * **Versioni supportate di Visual Studio** consente di scegliere le versioni di Visual Studio su cui funzionerà l'estensione. L'estensione viene installata solo in queste versioni.

    * L' **edizione di Visual Studio supportata** consente di scegliere le edizioni di Visual Studio su cui funzionerà l'estensione. L'estensione viene installata solo in queste edizioni.

    * **Type**. Il tipo più comune di estensione è **Tools**.

    * **Categorie**. È possibile scegliere un massimo di tre adatta per l'estensione.

    * I **tag** sono parole chiave che consentono agli utenti di trovare l'estensione. I tag possono contribuire ad aumentare la pertinenza della ricerca delle estensioni in Visual Studio Marketplace.

    * La **Categoria prezzi** è il costo dell'estensione.

    * Il **repository del codice sorgente** consente di condividere un collegamento al codice sorgente con la community.

    * **Consenti Q&a per l'estensione** consente agli utenti di lasciare le domande nella pagina voce dell'estensione.

9. Fare clic su **salva & caricare**. Questa opzione consente di tornare alla pagina di gestione del server di pubblicazione. L'estensione non è ancora stata pubblicata.

10. Per pubblicare l'estensione, fare clic con il pulsante destro del mouse sull'estensione e selezionare **Rendi pubblico**. Per verificare l'aspetto dell'estensione in Visual Studio Marketplace, selezionare **Visualizza estensione**. Per i numeri di acquisizione, fare clic su **report**. Per apportare modifiche all'estensione, fare clic su **modifica**.

    ![Menu voce dell'estensione](media/extension-entry-menu.png)

11. Fare clic su **Rendi pubblico** e l'estensione è ora pubblica. Cerca Visual Studio Marketplace per l'estensione.

## <a name="update-a-published-extension-in-visual-studio-marketplace"></a>Aggiornare un'estensione pubblicata in Visual Studio Marketplace

Prima di iniziare, assicurarsi di aver compilato la nuova versione di rilascio dell'estensione e che sia aggiornata.

1.  In un Web browser passare a [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

1.  Nell'angolo in alto a destra fare clic su **Accedi** e quindi accedere con il account Microsoft.

    :::image type="content" source="media/marketplace-upload-extension.png" alt-text="Screenshot che mostra la selezione di un file di estensione caricato in Esplora file.":::

1.  Fare clic su **Publish extensions**, quindi scegliere il server di pubblicazione che si desidera utilizzare per caricare l'estensione aggiornata.

    :::image type="content" source="media/marketplace-select-extension-version.png" alt-text="Screenshot di Visual Studio Marketplace con il collegamento Publish extensions evidenziato.":::

1.  Accanto all'estensione che si desidera aggiornare, posizionare il puntatore del mouse sui tre puntini orizzontali, quindi scegliere **modifica**.

    :::image type="content" source="media/marketplace-select-extension.png" alt-text="Screenshot che mostra la scelta di un'estensione da modificare.":::

1.  In **1: caricare l'estensione**, dopo il nome del file VSIX, fare clic sull'icona a matita per modificare l'estensione pubblicata.

     :::image type="content" source="media/marketplace-edit-extension-details.png" alt-text="Screenshot che Mostra come fare clic sull'icona della matita per modificare l'estensione.":::

1.  Passare al file VSIX di estensione aggiornato. Fare clic sul file e quindi su **Apri**.

    Caricamenti dell'estensione aggiornati.

    :::image type="content" source="media/marketplace-upload-extension-notification.png" alt-text="Screenshot di una notifica di caricamento file dopo il caricamento di un'estensione modificata.":::

1. In **2: fornire i dettagli dell'estensione**, alcuni dettagli sono di sola lettura per un aggiornamento dell'estensione o vengono popolati automaticamente dal file *source. Extension. vsixmanifest* dall'estensione. Di seguito sono riportate altre informazioni sui dettagli dell'estensione:

    - **Nome interno** \* viene usato nell'URL della pagina dei dettagli dell'estensione. Per un esempio, la pubblicazione di un'estensione con il nome del server di pubblicazione "nome" e il nome interno come "My extension" genera un URL "marketplace.visualstudio.com/items?itemName=myname.myextension" per la pagina dei dettagli dell'estensione.

    - **Nome visualizzato** \* dell'estensione. Questo nome viene popolato automaticamente dal file *source. Extension. vsixmanifest* .

    - **Versione** \* di numero dell'estensione che si sta caricando. Questa versione viene popolata automaticamente dal file *source. Extension. vsixmanifest* .

    - **ID VSIX** \* Identificatore univoco utilizzato da Visual Studio per l'estensione. Questo identificatore è obbligatorio se si desidera che l'estensione venga aggiornata automaticamente. Questo identificatore viene popolato automaticamente dal file *source. Extension. vsixmanifest* .

    - **Logo** \* di utilizzato per l'estensione. Questo logo viene popolato automaticamente dal file *source. Extension. vsixmanifest* , se specificato.

    - **Descrizione breve** \* del funzionamento dell'estensione. Questa descrizione viene popolata automaticamente dal file *source. Extension. vsixmanifest* .

    - **Panoramica** è una posizione ideale per includere schermate e informazioni dettagliate sul funzionamento dell'estensione.

    - Versioni di Visual **Studio supportate** \* consente di scegliere le versioni di Visual Studio su cui funzionerà l'estensione. L'estensione viene installata solo in queste versioni.

    - Edizione di Visual **Studio supportata** \* consente di scegliere le edizioni di Visual Studio su cui funzionerà l'estensione. L'estensione è installata solo in queste edizioni.

    - **Type**. Il tipo più comune di estensione è **Tools**.

    - **Categorie**. È possibile scegliere un massimo di tre adatta per l'estensione.

    - I **tag** sono parole chiave che consentono agli utenti di trovare l'estensione. I tag possono contribuire ad aumentare la pertinenza della ricerca delle estensioni in Visual Studio Marketplace.

    - La **Categoria prezzi** è il costo dell'estensione.

    - Il **repository del codice sorgente** consente di condividere un collegamento al codice sorgente con la community.

    - **Consenti Q&a per l'estensione** consente agli utenti di lasciare le domande nella pagina voce dell'estensione.

       \* Non è possibile modificare questo dettaglio per un aggiornamento dell'estensione.

1. Fare clic su **salva & caricare**. Questa opzione consente di tornare alla pagina di gestione del server di pubblicazione. L'estensione non è ancora stata pubblicata.

1. Per pubblicare l'estensione, fare clic con il pulsante destro del mouse sull'estensione e selezionare **Rendi pubblico**. Per verificare l'aspetto dell'estensione in Visual Studio Marketplace, selezionare **Visualizza estensione**. Per i numeri di acquisizione, fare clic su **report**. Per apportare modifiche all'estensione, fare clic su **modifica**.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Aggiungere altri utenti per gestire l'account di pubblicazione

Visual Studio Marketplace supporta la concessione di autorizzazioni utente aggiuntive per l'accesso e la gestione di un account di pubblicazione.

1. Passare all'account di pubblicazione a cui si desidera aggiungere altri utenti.

2. Selezionare **membri** e fare clic su **Aggiungi**.

   ![Aggiungi utente aggiuntivo](media/add-users.png)

3. È quindi possibile specificare l'indirizzo di posta elettronica dell'utente che si vuole aggiungere e concedere il livello di accesso corretto in **selezionare un ruolo**.  È possibile scegliere tra le opzioni seguenti:

   * **Creator**: l'utente può pubblicare le estensioni, ma non visualizzare o gestire le estensioni pubblicate da altri utenti.

   * **Reader**: l'utente può visualizzare le estensioni, ma non può pubblicare o gestire le estensioni.

   * **Collaboratore**: l'utente può pubblicare e gestire le estensioni, ma non può modificare le impostazioni del server di pubblicazione o gestire l'accesso.

   * **Proprietario**: l'utente può pubblicare e gestire le estensioni, modificare le impostazioni dell'editore e gestire l'accesso.

## <a name="install-the-extension-from-visual-studio-marketplace"></a>Installare l'estensione da Visual Studio Marketplace

Ora che l'estensione è pubblicata, installarla in Visual Studio ed eseguirne il test.

1. In Visual Studio scegliere **estensioni e aggiornamenti** dal menu **strumenti** .

2. Fare clic su **online** e quindi cercare **TestPublish**.

3. Fare clic su **Download**. L'estensione viene quindi pianificata per l'installazione.

4. Per completare l'installazione, chiudere tutte le istanze di Visual Studio.

## <a name="remove-the-extension"></a>Rimuovere l'estensione

È possibile rimuovere l'estensione da Visual Studio Marketplace e dal computer.

### <a name="to-remove-the-extension-from-visual-studio-marketplace"></a>Per rimuovere l'estensione da Visual Studio Marketplace

1. Passare a [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

2. Nell'angolo in alto a destra fare clic su **Publish** Extensions. Selezionare il server di pubblicazione usato per pubblicare **TestPublish**. Viene visualizzato l'elenco di **TestPublish** .

3. Fare clic con il pulsante destro del mouse sulla voce dell'estensione e scegliere **Rimuovi**. Viene richiesto di confermare se si desidera rimuovere l'estensione. Fare clic su **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Per rimuovere l'estensione dal computer

1. In Visual Studio scegliere **estensioni e aggiornamenti** dal menu **strumenti** .

2. Selezionare **TestPublish** e quindi fare clic su **Disinstalla**. L'estensione viene quindi pianificata per la disinstallazione.

3. Per completare la disinstallazione, chiudere tutte le istanze di Visual Studio.
