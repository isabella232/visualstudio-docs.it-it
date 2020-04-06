---
title: "Procedura dettagliata: Pubblicazione di un'estensione di Visual Studio Documenti Microsoft"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- publishing web controls
- web controls, publishing
ms.assetid: a7816161-0490-4043-86f5-0f7331ed83b3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a34260124baedeba297dbd64e8a2c1856b55ec5a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697132"
---
# <a name="walkthrough-publish-a-visual-studio-extension"></a>Procedura dettagliata: Pubblicare un'estensione di Visual StudioWalkthrough: Publish a Visual Studio extension

Questa procedura dettagliata viene illustrato come pubblicare un'estensione di Visual Studio in Visual Studio Marketplace.This walkthrough shows you how to publish a Visual Studio extension to the Visual Studio Marketplace. Quando aggiungi l'estensione al Marketplace, gli sviluppatori possono utilizzare **le estensioni e gli aggiornamenti** per cercare estensioni nuove e aggiornate.

## <a name="prerequisites"></a>Prerequisiti

 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-visual-studio-extension"></a>Creare un'estensione di Visual StudioCreate a Visual Studio extension

Questo articolo usa un'estensione VSPackage predefinita, ma i passaggi sono validi per ogni tipo di estensione.

1. Creare un pacchetto VSPackage `TestPublish` in nome C , che dispone di un comando di menu. Per ulteriori informazioni, vedere [Creare la prima estensione: Hello World](../extensibility/extensibility-hello-world.md).

## <a name="package-your-extension"></a>Creare il pacchetto dell'estensione

1. Aggiornare l'estensione *vsixmanifest* con le informazioni corrette sul nome del prodotto, l'autore e la versione.

   ![aggiornamento estensione vsixmanifest](media/update-extension-vsixmanifest.png)

2. Compilare l'estensione in modalità **di rilascio.** A questo punto l'estensione è inclusa in un pacchetto VSIX nella cartella di rilascio.

3. È possibile fare doppio clic sul valore VSIX per verificare l'installazione.

## <a name="test-the-extension"></a>Testare l'estensione

 Prima di distribuire l'estensione, compilarla e testarla per assicurarsi che sia installata correttamente nell'istanza sperimentale di Visual Studio.

1. In Visual Studio, start debugging to open an experimental instance of Visual Studio.

2. Nell'istanza sperimentale, accedere al menu **Strumenti** e fare clic su **Estensioni e aggiornamenti**. L'estensione TestPublish deve essere visualizzata nel riquadro centrale ed essere abilitata.

3. Nel menu **Strumenti,** assicurarsi che venga visualizzato il comando test.

## <a name="publish-the-extension-to-the-visual-studio-marketplace"></a>Pubblicare l'estensione in Visual Studio Marketplace

1. Assicurati di aver creato la versione di rilascio dell'estensione e che sia aggiornata.

2. In un Web browser aprire il sito Web di [Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

3. Nell'angolo superiore destro fare clic su **Accedi**.

4. Usare l'account Microsoft per accedere. Se non si dispone di un account Microsoft, è possibile crearne uno a questo punto.

5. Fare clic su **Pubblica estensioni**.  Questa opzione consente di accedere alla pagina di gestione di tutte le estensioni. Se non si dispone di un account editore, viene richiesto di crearne uno in questo momento.

   ![Carica su Marketplace](media/upload-to-marketplace.png)

6. Scegli l'editore che desideri utilizzare per caricare l'estensione. Puoi cambiare editore facendo clic sui nomi dei publisher elencati a sinistra. Fare clic su **Nuova estensione** e selezionare **Visual Studio**.

7. In **1: Carica estensione**, è possibile scegliere di caricare un file VSIX direttamente in Visual Studio Marketplace o semplicemente aggiungere un collegamento al proprio sito Web. In questo esempio viene caricata l'estensione *TestPublish.vsix.In* this example, the extension, TestPublish.vsix is uploaded. Trascina e rilascia l'estensione o usa il link **di clic** per cercare il file. Individuare l'estensione nella cartella di rilascio del progetto.  Fare clic su **Continua**.

8. In **2: fornire i dettagli dell'estensione**, alcuni campi vengono popolati automaticamente dal file *source.extension.vsixmanifest* dall'estensione. Per maggiori dettagli su ciascuno di essi qui sotto:

    * **Nome interno** viene utilizzato nell'URL della pagina dei dettagli dell'estensione. Ad esempio, la pubblicazione di un'estensione con il nome dell'editore "myname" e la specifica\.del nome interno come "mia estensione" genera un URL di "marketplace.visualstudio com/items?itemName.myname.myextension" per la pagina dei dettagli dell'estensione.

    * **Nome visualizzato** dell'estensione. Questo nome viene compilato automaticamente dal file *source.extension.vsixmanifest.*

    * **Numero** di versione dell'estensione che si sta caricando. Questa versione viene compilata automaticamente dal file *source.extension.vsixmanifest.*

    * **ID VSIX** è l'identificatore univoco utilizzato da Visual Studio per l'estensione. Questo identificatore è obbligatorio se si desidera aggiornare automaticamente l'estensione. Questo identificatore viene compilato automaticamente dal file *source.extension.vsixmanifest.*

    * **Logo** utilizzato per l'estensione. Questo logo viene compilato automaticamente dal file *source.extension.vsixmanifest,* se specificato.

    * **Breve descrizione** delle operazioni eseguite dall'estensione. Questa descrizione viene compilata automaticamente dal file *source.extension.vsixmanifest.*

    * **Panoramica** è un buon posto per includere screenshot e informazioni dettagliate su ciò che l'estensione fa.

    * **Le versioni di Visual Studio supportate** consentono di scegliere le versioni di Visual Studio su cui funzionerà l'estensione. L'estensione viene installata solo in tali versioni.

    * L'edizione di Visual Studio supportata consente di scegliere le edizioni di Visual Studio su cui funzionerà l'estensione. L'estensione viene installata solo in tali edizioni.

    * **Tipo**. Il tipo più comune di estensioni sono **Tools**.

    * **Categorie**. Scegli fino a tre che sono la soluzione migliore per la tua estensione.

    * **I tag** sono parole chiave che aiutano gli utenti a trovare la tua estensione. I tag consentono di aumentare la pertinenza della ricerca delle estensioni nel Marketplace.

    * **Categoria di prezzo** è il costo dell'estensione.

    * **Il repository** del codice sorgente consente di condividere un collegamento al codice sorgente con la community.

    * **Consenti Q&A per l'estensione** consente agli utenti di lasciare domande nella pagina di immissione dell'estensione.

9. Fare clic su **Salva & caricamento**. Questa opzione consente di tornare alla pagina di gestione del publisher. L'estensione non è ancora stata pubblicata. Per pubblicare l'estensione, fare clic con il pulsante destro del mouse sull'estensione e **scegliere Rendi pubblico**. È possibile visualizzare l'aspetto dell'estensione su Marketplace selezionando **Visualizza estensione**. Per i numeri di acquisizione, fare clic su **Report**. Per apportare modifiche all'estensione, fare clic su **Modifica**.

   ![Menu Voce estensione](media/extension-entry-menu.png)

10. Dopo aver fatto clic su **Rendi pubblico**, l'estensione è ora pubblica. Cercare l'estensione in Visual Studio Marketplace.

## <a name="add-additional-users-to-manage-your-publisher-account"></a>Aggiungere altri utenti per gestire l'account publisher

Marketplace supporta la concessione di ad altri utenti autorizzazioni per accedere e gestire un account publisher.

1. Accedi all'account publisher a cui desideri aggiungere altri utenti.

2. Selezionare **Membri** e fare clic su **Aggiungi**.

   ![Aggiungi utente aggiuntivo](media/add-users.png)

3. È quindi possibile specificare l'indirizzo di posta elettronica dell'utente che si desidera aggiungere e concedere il livello di accesso corretto in **Selezionare un ruolo**.  È possibile scegliere tra le opzioni seguenti:

   * **Creatore:** l'utente può pubblicare estensioni, ma non può visualizzare o gestire le estensioni pubblicate da altri utenti.

   * **Lettore:** l'utente può visualizzare le estensioni, ma non può pubblicare o gestire le estensioni.

   * **Collaboratore:** l'utente può pubblicare e gestire le estensioni, ma non può modificare le impostazioni dell'editore o gestire l'accesso.

   * **Proprietario**: L'utente può pubblicare e gestire le estensioni, modificare le impostazioni dell'editore e gestire l'accesso.

## <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installare l'estensione da Visual Studio MarketplaceInstall the extension from the Visual Studio Marketplace

Ora che l'estensione è pubblicata, installarla in Visual Studio e testarla.

1. In Visual Studio scegliere **Estensioni e aggiornamenti**dal menu **Strumenti** .

2. Fare clic su **Online** e quindi cercare **TestPublish**.

3. Fare clic su **Download**. L'estensione viene quindi pianificata per l'installazione.

4. Per completare l'installazione, chiudere tutte le istanze di Visual Studio.To complete the installation, close all instances of Visual Studio.

## <a name="remove-the-extension"></a>Rimuovere l'estensione

È possibile rimuovere l'estensione da Visual Studio Marketplace e dal computer.

### <a name="to-remove-the-extension-from-the-visual-studio-marketplace"></a>Per rimuovere l'estensione da Visual Studio Marketplace

1. Aprire il sito Web [di Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

2. Nell'angolo superiore destro fare clic su **Pubblica** estensioni. Selezionare l'autore utilizzato per pubblicare **TestPublish**. Viene visualizzato l'elenco per **TestPublish.**

3. Fare clic con il pulsante destro del mouse sulla voce di estensione e **scegliere Rimuovi**. Viene chiesto di confermare se si desidera rimuovere l'estensione. Fare clic su **OK**.

### <a name="to-remove-the-extension-from-your-computer"></a>Per rimuovere l'estensione dal computer

1. In Visual Studio scegliere **Estensioni e aggiornamenti**dal menu **Strumenti** .

2. Selezionare **TestPublish** e quindi fare clic su **Disinstalla**. L'estensione viene quindi pianificata per la disinstallazione.

3. Per completare la disinstallazione, chiudere tutte le istanze di Visual Studio.To complete the uninstallation, close all instances of Visual Studio.
