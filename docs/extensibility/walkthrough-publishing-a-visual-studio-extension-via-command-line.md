---
title: Pubblicare l'estensione tramite riga di comando
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40be0252218f39b4ff98b58caedd7f9f20ce6d5d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697121"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Procedura dettagliata: pubblicazione di un'estensione di Visual Studio tramite riga di comandoWalkthrough: Publishing a Visual Studio extension from command line

Questa procedura dettagliata viene illustrato come pubblicare un'estensione di Visual Studio in Visual Studio Marketplace tramite la riga di comando. Quando aggiungi l'estensione al Marketplace, gli sviluppatori possono utilizzare la finestra di dialogo [**Estensioni e aggiornamenti**](../ide/finding-and-using-visual-studio-extensions.md) per cercare le estensioni nuove e aggiornate.

VsixPublisher.exe è lo strumento della riga di comando per la pubblicazione delle estensioni di Visual Studio nel Marketplace. È possibile accedervi da . I comandi disponibili in questo strumento sono: **publish**, **createPublisher**, **deletePublisher**, **deleteExtension**, **login**, **logout**.

## <a name="commands"></a>Comandi:

### <a name="publish"></a>Pubblica

Pubblica un'estensione nel Marketplace. L'estensione può essere un vsix, un file exe/msi o un collegamento. Se l'estensione esiste già con la stessa versione, sovrascriverà l'estensione. Se l'estensione non esiste già, verrà creata una nuova estensione.

|Opzioni di comando |Descrizione |
|---------|---------|
|payload (obbligatorio) | Un percorso al payload da pubblicare o un collegamento da utilizzare come "URL di informazioni ulteriori". |
|publishManifest (obbligatorio) | Percorso del file manifesto di pubblicazione da utilizzare. |
|ignoreWarnings | Elenco di avvisi da ignorare durante la pubblicazione di un'estensione. Questi avvisi vengono visualizzati come messaggi della riga di comando quando si pubblica un'estensione. (ad esempio, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken (informazioni in base al fatto di un | Token di accesso personale (PAT) utilizzato per autenticare il server di pubblicazione. Se non viene fornito, il PAT viene acquisito dagli utenti connessi. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Crea un editore nel Marketplace. Registra inoltre il server di pubblicazione nel computer per le azioni future (ad esempio, l'eliminazione/la pubblicazione di un'estensione).

|Opzioni di comando |Descrizione |
|---------|---------|
|displayName (obbligatorio) | Nome visualizzato del server di pubblicazione. |
|publisherName (obbligatorio) | Nome del server di pubblicazione, ad esempio l'identificatore. |
|personalAccessToken (obbligatorio) | Token di accesso personale utilizzato per autenticare il server di pubblicazione. |
|shortDescrizione | Una breve descrizione dell'editore (non un file). |
|LongDescrizione | Una lunga descrizione dell'editore (non un file). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Elimina un publisher nel Marketplace.

|Opzioni di comando |Descrizione |
|---------|---------|
|publisherName (obbligatorio) | Nome del server di pubblicazione, ad esempio l'identificatore. |
|personalAccessToken (obbligatorio) | Token di accesso personale utilizzato per autenticare il server di pubblicazione. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension (estensione)

Elimina un'estensione dal Marketplace.

|Opzioni di comando |Descrizione |
|---------|---------|
|extensionName (obbligatorio) | Nome dell'estensione da eliminare. |
|publisherName (obbligatorio) | Nome del server di pubblicazione, ad esempio l'identificatore. |
|personalAccessToken (informazioni in base al fatto di un | Token di accesso personale utilizzato per autenticare il server di pubblicazione. Se non viene specificato, il pat viene acquisito dagli utenti connessi. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

Registra un server di pubblicazione nel computer.

|Opzioni di comando |Descrizione |
|---------|---------|
|personalAccessToken (obbligatorio) | Token di accesso personale utilizzato per autenticare il server di pubblicazione. |
|publisherName (obbligatorio) | Nome del server di pubblicazione, ad esempio l'identificatore. |
|overwrite | Specifica che qualsiasi autore esistente deve essere sovrascritto con il nuovo token di accesso personale. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Disconnette un server di pubblicazione dal computer.

|Opzioni di comando |Descrizione |
|---------|---------|
|publisherName (obbligatorio) | Nome del server di pubblicazione, ad esempio l'identificatore. |
|ignoreMissingPublisher | Specifica che lo strumento non deve verificarsi un errore se l'autore specificato non è già connesso. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>publishManifest (file)

Un file publishManifest viene utilizzato dal comando **publish.** Rappresenta tutti i metadati relativi all'estensione che il Marketplace deve conoscere. Se l'estensione da caricare proviene da un'estensione VSIX, la proprietà "identity" deve avere solo il "internalName" impostato. Questo perché il resto delle proprietà "identity" può essere generato dal file vsixmanifest. Se l'estensione è un file msi/exe o un'estensione di collegamento, l'utente deve fornire i campi obbligatori nella proprietà "identity". Il resto del manifesto contiene informazioni specifiche del Marketplace (ad esempio, categorie, se Q&A è abilitato e così via).

Esempio di file publishManifest dell'estensione VSIX:VSIX extension publishManifest file sample:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],  // The categories of the extension. Between 1 and 3 categories are required.
    "identity": {
        "internalName": "MyVsixExtension" // If not specified, we try to generate the name from the display name of the extension in the vsixmanifest file.
                                            // Required if the display name is not the actual name of the extension.
    },
    "overview": "overview.md",            // Path to the "readme" file that gets uploaded to the Marketplace. Required.
    "priceCategory": "free",              // Either "free", "trial", or "paid". Defaults to "free".
    "publisher": "MyPublisherName",       // The name of the publisher. Required.
    "private": false,                     // Specifies whether or not the extension should be public when uploaded. Defaults to false.
    "qna": true,                          // Specifies whether or not the extension should have a Q&A section. Defaults to true.
    "repo": "https://github.com/MyPublisherName/MyVsixExtension" // Not required.
}
```

MSI/EXE o LINK publishManifest file sample:

```json
{
    "$schema": "http://json.schemastore.org/vsix-publish",
    "categories": [ "build", "coding" ],
    "identity": {
        "description": "My extension.", // The description of the extension. Required for non-vsix extensions.
        "displayName": "My Extension",  // The display name of the extension. Required for non-vsix extensions.
        "icon": "\\path\\to\\icon.ico", // The path to an icon file (can be relative to the json file location). Required for non-vsix extensions.
        "installTargets": [             // The installation targets for the extension. Required for non-vsix extensions.
            {
                "sku": "Microsoft.VisualStudio.Community",
                "version": "[10.0, 16.0)"
            }
        ],
        "internalName": "MyExtension",
        "language": "en-US",            // The default language id of the extension. Can be in the "1033" or "en-US" format. Required for non-vsix extensions.
        "tags": [ "tag1", "tag2" ],     // The tags for the extension. Not required.
        "version": "3.7.0",             // The version of the extension. Required for non-vsix extensions.
        "vsixId": "MyExtension",        // The vsix id of the extension. Not required but useful for showing updates to installed extensions.
    },
    "overview": "overview.md",
    "priceCategory": "free",
    "publisher": "MyPublisherName",
    "private": false,
    "qna": true,
    "repo": "https://github.com/MyPublisherName/MyVsixExtension"
}
```

## <a name="asset-files"></a>File di risorse

I file di risorse possono essere forniti per incorporare elementi come le immagini nel file Leggimi. Ad esempio, se un'estensione ha il seguente documento Markdown "panoramica":

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Per risolvere "images/testlogo.png" nell'esempio precedente, un utente può fornire "assetFiles" nel manifesto di pubblicazione come di seguito:

```json
{
    "assetFiles": [
        {
            "pathOnDisk": "\\path\\to\\logo.png",
            "targetPath": "images/logo.png"
        }
    ],
    // other required fields
}
```

## <a name="publishing-walkthrough"></a>Procedura dettagliata di pubblicazionePublishing walkthrough

### <a name="prerequisites"></a>Prerequisiti

Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Installazione di Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="create-a-visual-studio-extension"></a>Creare un'estensione di Visual StudioCreate a Visual Studio extension

In questo caso, useremo un'estensione VSPackage predefinita, ma gli stessi passaggi sono validi per ogni tipo di estensione.

1. Creare un pacchetto VSPackage in C , denominato "TestPublish" che dispone di un comando di menu. Per ulteriori informazioni, vedere [Creazione della prima estensione: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Creare il pacchetto dell'estensione

1. Aggiornare l'estensione vsixmanifest con le informazioni corrette sul nome del prodotto, autore e versione.

   ![aggiornamento estensione vsixmanifest](media/update-extension-vsixmanifest.png)

2. Compilare l'estensione in modalità **di rilascio.** A questo punto l'estensione verrà inclusa nel pacchetto come un valore VSIX nella cartella di rilascio.

3. È possibile fare doppio clic sul valore VSIX per verificare l'installazione.

### <a name="test-the-extension"></a>Testare l'estensione

 Prima di distribuire l'estensione, compilarla e testarla per assicurarsi che sia installata correttamente nell'istanza sperimentale di Visual Studio.

1. In Visual Studio avviare il debug. per aprire un'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale, accedere al menu **Strumenti** e fare clic su **Estensioni e aggiornamenti...**. L'estensione TestPublish deve essere visualizzata nel riquadro centrale ed essere abilitata.

3. Nel menu **Strumenti,** assicurarsi che venga visualizzato il comando test.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Pubblicare l'estensione nel Marketplace tramite la riga di comando

1. Assicurarsi di aver compilato la versione finale dell'estensione e che sia aggiornata.

2. Assicurarsi di aver creato publishmanifest.json e overview.md file.

3. Aprire la riga di comando e passare alla directory .

4. Per creare un nuovo editore, utilizzare il comando seguente:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Alla corretta creazione dell'editore, verrà visualizzato il seguente messaggio della riga di comando:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. È possibile verificare il nuovo editore creato passando a [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Per pubblicare una nuova estensione, utilizzare il comando seguente:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Alla corretta creazione dell'editore, verrà visualizzato il seguente messaggio della riga di comando:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. È possibile verificare la nuova estensione pubblicata passando a [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installare l'estensione da Visual Studio MarketplaceInstall the extension from the Visual Studio Marketplace

Ora che l'estensione è pubblicata, installarla in Visual Studio e testarla.

1. In Visual Studio scegliere **Estensioni e aggiornamenti**dal menu **Strumenti...** .

2. Fare clic su **Online** e quindi cercare TestPublish.

3. Fare clic su **Download**. L'estensione verrà quindi pianificata per l'installazione.

4. Per completare l'installazione, chiudere tutte le istanze di Visual Studio.To complete the installation, close all instances of Visual Studio.

## <a name="remove-the-extension"></a>Rimuovere l'estensione

È possibile rimuovere l'estensione da Visual Studio Marketplace e dal computer.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Per rimuovere l'estensione dal Marketplace tramite la riga di comando

1. Se si desidera rimuovere un'estensione, utilizzare il comando seguente:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Al termine dell'eliminazione dell'estensione, verrà visualizzato il seguente messaggio della riga di comando:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Per rimuovere l'estensione dal computer

1. In Visual Studio scegliere **Estensioni e aggiornamenti**dal menu **Strumenti** .

2. Selezionare "MyVsixExtension" e quindi fare clic su **Disinstalla**. L'estensione verrà quindi pianificata per la disinstallazione.

3. Per completare la disinstallazione, chiudere tutte le istanze di Visual Studio.To complete the uninstallation, close all instances of Visual Studio.
