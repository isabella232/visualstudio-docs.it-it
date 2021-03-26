---
title: Pubblica estensione con riga di comando
description: Informazioni su come usare la riga di comando per pubblicare un'estensione per la Visual Studio Marketplace, che consente agli sviluppatori di individuare le estensioni nuove e aggiornate.
ms.custom: SEO-VS-2020
ms.date: 07/12/2018
ms.topic: how-to
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d3548c9a206e874848756944fb48d447c34e28cc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078370"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Procedura dettagliata: pubblicazione di un'estensione di Visual Studio tramite la riga di comando

Questa procedura dettagliata illustra come pubblicare un'estensione di Visual Studio nel Visual Studio Marketplace usando la riga di comando. Quando si aggiunge l'estensione al Marketplace, gli sviluppatori possono usare la finestra di dialogo [**estensioni e aggiornamenti**](../ide/finding-and-using-visual-studio-extensions.md) per individuare le estensioni nuove e aggiornate.

VsixPublisher.exe è lo strumento da riga di comando per la pubblicazione di estensioni di Visual Studio nel Marketplace. È possibile accedervi da $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. I comandi disponibili in questo strumento sono: **Publish**, **createPublisher**, **deletePublisher**, **deleteExtension**, **login**, **Logout**.

## <a name="commands"></a>Comandi

### <a name="publish"></a>Pubblica

Pubblica un'estensione nel Marketplace. L'estensione può essere VSIX, un file exe/MSI o un collegamento. Se l'estensione esiste già con la stessa versione, l'estensione verrà sovrascritta. Se l'estensione non esiste già, verrà creata una nuova estensione.

|Opzioni del comando |Descrizione |
|---------|---------|
|payload (obbligatorio) | Un percorso del payload da pubblicare o un collegamento da usare come "URL più informazioni". |
|publishManifest (obbligatorio) | Percorso del file manifesto di pubblicazione da usare. |
|ignoreWarnings | Elenco di avvisi da ignorare durante la pubblicazione di un'estensione. Questi avvisi vengono visualizzati come messaggi della riga di comando durante la pubblicazione di un'estensione. (ad esempio, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Token di accesso personale (PAT) usato per autenticare il server di pubblicazione. Se non viene specificato, il PAT viene acquisito dagli utenti connessi. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Consente di creare un server di pubblicazione nel Marketplace. Registra anche il server di pubblicazione nel computer per azioni future, ad esempio l'eliminazione o la pubblicazione di un'estensione.

|Opzioni del comando |Descrizione |
|---------|---------|
|displayName (obbligatorio) | Nome visualizzato del server di pubblicazione. |
|PublisherName (obbligatorio) | Nome del server di pubblicazione (ad esempio, l'identificatore). |
|personalAccessToken (obbligatorio) | Token di accesso personale usato per autenticare il server di pubblicazione. |
|shortDescription | Breve descrizione del server di pubblicazione (non di un file). |
|longDescription | Descrizione estesa del server di pubblicazione (non di un file). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Elimina un server di pubblicazione nel Marketplace.

|Opzioni del comando |Descrizione |
|---------|---------|
|PublisherName (obbligatorio) | Nome del server di pubblicazione (ad esempio, l'identificatore). |
|personalAccessToken (obbligatorio) | Token di accesso personale usato per autenticare il server di pubblicazione. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Elimina un'estensione dal Marketplace.

|Opzioni del comando |Descrizione |
|---------|---------|
|ExtensionName (obbligatorio) | Nome dell'estensione da eliminare. |
|PublisherName (obbligatorio) | Nome del server di pubblicazione (ad esempio, l'identificatore). |
|personalAccessToken | Token di accesso personale usato per autenticare il server di pubblicazione. Se non viene specificato, il Pat viene acquisito dagli utenti connessi. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

Registra un server di pubblicazione nel computer.

|Opzioni del comando |Descrizione |
|---------|---------|
|personalAccessToken (obbligatorio | Token di accesso personale usato per autenticare il server di pubblicazione. |
|PublisherName (obbligatorio) | Nome del server di pubblicazione (ad esempio, l'identificatore). |
|overwrite | Specifica che tutti i server di pubblicazione esistenti devono essere sovrascritti con il nuovo token di accesso personale. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Registra un server di pubblicazione fuori dal computer.

|Opzioni del comando |Descrizione |
|---------|---------|
|PublisherName (obbligatorio) | Nome del server di pubblicazione (ad esempio, l'identificatore). |
|ignoreMissingPublisher | Specifica che lo strumento non dovrebbe essere in errore se il server di pubblicazione specificato non è già connesso. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>file publishManifest

Un file publishManifest viene utilizzato dal comando **Publish** . Rappresenta tutti i metadati relativi all'estensione che il Marketplace deve conoscere. Se l'estensione da caricare è da un'estensione VSIX, la proprietà "Identity" deve avere solo il set "InternalName". Questo perché il resto delle proprietà "Identity" può essere generato dal file vsixmanifest. Se si tratta di un'estensione msi/exe o di collegamento, l'utente deve fornire i campi obbligatori nella proprietà "Identity". Il resto del manifesto contiene informazioni specifiche del Marketplace, ad esempio le categorie, se Q&A è abilitato e così via.

Esempio di file publishManifest estensione VSIX:

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

Esempio di file MSI/EXE o LINK publishManifest:

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

## <a name="asset-files"></a>File di asset

I file di asset possono essere forniti per incorporare elementi come le immagini nel file Leggimi. Se, ad esempio, un'estensione presenta il documento Markdown "Overview" seguente:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Per risolvere "images/testlogo.png" nell'esempio precedente, un utente può specificare "assetFiles" nel manifesto di pubblicazione come riportato di seguito:

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

## <a name="publishing-walkthrough"></a>Procedura dettagliata di pubblicazione

### <a name="prerequisites"></a>Prerequisiti

Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Creare un'estensione di Visual Studio

In questo caso, verrà usata un'estensione VSPackage predefinita, ma gli stessi passaggi sono validi per ogni tipo di estensione.

1. Creare un pacchetto VSPackage in C# denominato "TestPublish" con un comando di menu. Per ulteriori informazioni, vedere [creazione della prima estensione: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Creare il pacchetto dell'estensione

1. Aggiornare l'estensione vsixmanifest con le informazioni corrette sul nome del prodotto, l'autore e la versione.

   ![aggiornamento dell'estensione vsixmanifest](media/update-extension-vsixmanifest.png)

2. Compilare l'estensione in modalità di **rilascio** . A questo punto l'estensione verrà assemblata come VSIX nella cartella \bin\Release.

3. È possibile fare doppio clic su VSIX per verificare l'installazione.

### <a name="test-the-extension"></a>Testare l'estensione

 Prima di distribuire l'estensione, compilarla e testarla per assicurarsi che sia installata correttamente nell'istanza sperimentale di Visual Studio.

1. In Visual Studio avviare il debug. per aprire un'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale, andare al menu **strumenti** e fare clic su **estensioni e aggiornamenti**. L'estensione TestPublish dovrebbe essere visualizzata nel riquadro centrale ed essere abilitata.

3. Nel menu **strumenti** verificare che sia visualizzato il comando test.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Pubblicare l'estensione nel Marketplace tramite la riga di comando

1. Assicurarsi di aver compilato la versione di rilascio dell'estensione e che sia aggiornata.

2. Assicurarsi di aver creato publishmanifest.jsfile in e overview.md.

3. Aprire la riga di comando e passare alla directory $ {VSInstallDir} \VSSDK\VisualStudioIntegration\Tools\Bin\

4. Per creare un nuovo server di pubblicazione, utilizzare il comando seguente:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Al completamento della creazione del server di pubblicazione, viene visualizzato il seguente messaggio della riga di comando:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. È possibile verificare il nuovo server di pubblicazione creato passando a [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Per pubblicare una nuova estensione, usare il comando seguente:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Al completamento della creazione del server di pubblicazione, viene visualizzato il seguente messaggio della riga di comando:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. È possibile verificare la nuova estensione pubblicata passando a [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installare l'estensione dal Visual Studio Marketplace

Ora che l'estensione è pubblicata, installarla in Visual Studio ed eseguirne il test.

1. In Visual Studio scegliere **estensioni e aggiornamenti** dal menu **strumenti** .

2. Fare clic su **online** e quindi cercare TestPublish.

3. Fare clic su **Download**. L'estensione verrà quindi pianificata per l'installazione.

4. Per completare l'installazione, chiudere tutte le istanze di Visual Studio.

## <a name="remove-the-extension"></a>Rimuovere l'estensione

È possibile rimuovere l'estensione dal Visual Studio Marketplace e dal computer.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Per rimuovere l'estensione dal Marketplace tramite la riga di comando

1. Se si vuole rimuovere un'estensione, usare il comando seguente:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Al completamento dell'eliminazione dell'estensione, viene visualizzato il messaggio della riga di comando seguente:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Per rimuovere l'estensione dal computer

1. In Visual Studio scegliere **estensioni e aggiornamenti** dal menu **strumenti** .

2. Selezionare "MyVsixExtension" e quindi fare clic su **Disinstalla**. L'estensione verrà quindi pianificata per la disinstallazione.

3. Per completare la disinstallazione, chiudere tutte le istanze di Visual Studio.
