---
title: Pubblicare l'estensione tramite la riga di comando
description: Informazioni su come usare la riga di comando per pubblicare un'estensione in Visual Studio Marketplace, che consente agli sviluppatori di cercare estensioni nuove e aggiornate.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b6d02c4eb0125007086e209897e11b2038adc26d116cd0dd03f346fc02291a51
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121374598"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Procedura dettagliata: Pubblicazione di un'estensione Visual Studio tramite la riga di comando

Questa procedura dettagliata illustra come pubblicare un'estensione Visual Studio in Visual Studio Marketplace usando la riga di comando. Quando si aggiunge l'estensione al Marketplace, gli sviluppatori possono usare la finestra di dialogo Estensioni e aggiornamenti per cercare estensioni nuove e aggiornate. [](../ide/finding-and-using-visual-studio-extensions.md)

VsixPublisher.exe è lo strumento da riga di comando per la Visual Studio estensioni nel Marketplace. È possibile accedervi da ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. I comandi disponibili in questo strumento sono: **publish,** **createPublisher,** **deletePublisher,** **deleteExtension,** **login,** **logout.**

## <a name="commands"></a>Comandi

### <a name="publish"></a>Pubblica

Pubblica un'estensione nel Marketplace. L'estensione può essere un file vsix, un file exe/msi o un collegamento. Se l'estensione esiste già con la stessa versione, sovrascriverà l'estensione. Se l'estensione non esiste già, verrà creata una nuova estensione.

|Opzioni dei comandi |Descrizione |
|---------|---------|
|payload (obbligatorio) | Percorso del payload da pubblicare o collegamento da usare come "URL di informazioni aggiuntive". |
|publishManifest (obbligatorio) | Percorso del file manifesto di pubblicazione da usare. |
|ignoreWarnings | Elenco di avvisi da ignorare quando si pubblica un'estensione. Questi avvisi vengono visualizzati come messaggi della riga di comando quando si pubblica un'estensione. (ad esempio, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Token di accesso personale (PAT) usato per autenticare l'autore. Se non viene specificato, il PAT viene acquisito dagli utenti connessi. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Crea un editore nel Marketplace. Registra anche il server di pubblicazione nel computer per le azioni future, ad esempio l'eliminazione/pubblicazione di un'estensione.

|Opzioni dei comandi |Descrizione |
|---------|---------|
|displayName (obbligatorio) | Nome visualizzato del server di pubblicazione. |
|publisherName (obbligatorio) | Nome del server di pubblicazione, ad esempio l'identificatore . |
|personalAccessToken (obbligatorio) | Token di accesso personale usato per autenticare l'autore. |
|shortDescription | Breve descrizione del server di pubblicazione (non di un file). |
|longDescription | Descrizione lunga del server di pubblicazione (non di un file). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Elimina un editore nel Marketplace.

|Opzioni dei comandi |Descrizione |
|---------|---------|
|publisherName (obbligatorio) | Nome del server di pubblicazione, ad esempio l'identificatore . |
|personalAccessToken (obbligatorio) | Token di accesso personale usato per autenticare l'autore. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Elimina un'estensione dal Marketplace.

|Opzioni dei comandi |Descrizione |
|---------|---------|
|extensionName (obbligatorio) | Nome dell'estensione da eliminare. |
|publisherName (obbligatorio) | Nome del server di pubblicazione, ad esempio l'identificatore . |
|personalAccessToken | Token di accesso personale usato per autenticare l'autore. Se non specificato, il pat viene acquisito dagli utenti connessi. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>login

Registra un server di pubblicazione nel computer.

|Opzioni dei comandi |Descrizione |
|---------|---------|
|personalAccessToken (obbligatorio) | Token di accesso personale usato per autenticare l'autore. |
|publisherName (obbligatorio) | Nome del server di pubblicazione, ad esempio l'identificatore . |
|overwrite | Specifica che qualsiasi server di pubblicazione esistente deve essere sovrascritto con il nuovo token di accesso personale. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Disconnette un server di pubblicazione dal computer.

|Opzioni dei comandi |Descrizione |
|---------|---------|
|publisherName (obbligatorio) | Nome del server di pubblicazione, ad esempio l'identificatore . |
|ignoreMissingPublisher | Specifica che lo strumento non deve determinare errori se il server di pubblicazione specificato non è già connesso. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>file publishManifest

Un file publishManifest viene usato dal **comando publish.** Rappresenta tutti i metadati relativi all'estensione che il Marketplace deve conoscere. Se l'estensione caricata è da un'estensione VSIX, la proprietà "identity" deve avere impostato solo "internalName". Ciò è dovuto al fatto che le altre proprietà "identity" possono essere generate dal file vsixmanifest. Se l'estensione è msi/exe o un'estensione di collegamento, l'utente deve specificare i campi obbligatori nella proprietà "identity". Il resto del manifesto contiene informazioni specifiche per il Marketplace,ad esempio le categorie, se Q&A è abilitato e così via.

Esempio di file publishManifest dell'estensione VSIX:

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

I file di asset possono essere forniti per incorporare elementi come le immagini nel file Leggimi. Ad esempio, se un'estensione ha il documento Markdown "panoramica" seguente:

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Per risolvere "images/testlogo.png" nell'esempio precedente, un utente può fornire "assetFiles" nel manifesto di pubblicazione come indicato di seguito:

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

## <a name="publishing-walkthrough"></a>Procedura dettagliata per la pubblicazione

### <a name="prerequisites"></a>Prerequisiti

Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Creare un'Visual Studio predefinita

In questo caso, si userà un'estensione VSPackage predefinita, ma gli stessi passaggi sono validi per ogni tipo di estensione.

1. Creare un VSPackage in C# denominato "TestPublish" con un comando di menu. Per altre informazioni, vedere [Creazione della prima estensione: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Creare il pacchetto dell'estensione

1. Aggiornare l'estensione vsixmanifest con le informazioni corrette sul nome del prodotto, sull'autore e sulla versione.

   ![estensione di aggiornamento vsixmanifest](media/update-extension-vsixmanifest.png)

2. Compilare l'estensione in **modalità** di rilascio. L'estensione verrà ora in pacchetto come VSIX nella cartella \bin\Release.

3. È possibile fare doppio clic su VSIX per verificare l'installazione.

### <a name="test-the-extension"></a>Testare l'estensione

 Prima di distribuire l'estensione, compilarla e testarla per assicurarsi che sia installata correttamente nell'istanza sperimentale di Visual Studio.

1. In Visual Studio avviare il debug. per aprire un'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale passare al menu **Strumenti** e fare clic su **Estensioni e aggiornamenti...**. L'estensione TestPublish dovrebbe essere visualizzata nel riquadro centrale ed essere abilitata.

3. Nel menu **Strumenti** assicurarsi di visualizzare il comando test.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Pubblicare l'estensione nel Marketplace tramite la riga di comando

1. Assicurarsi di aver compilato la versione di rilascio dell'estensione e che sia aggiornata.

2. Assicurarsi di aver creato publishmanifest.jsfile e overview.md file.

3. Aprire la riga di comando e passare alla directory ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\.

4. Per creare un nuovo server di pubblicazione, usare il comando seguente:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Al completamento della creazione del server di pubblicazione, verrà visualizzato il messaggio della riga di comando seguente:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. È possibile verificare il nuovo editore creato passando a [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Per pubblicare una nuova estensione, usare il comando seguente:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Al completamento della creazione del server di pubblicazione, verrà visualizzato il messaggio della riga di comando seguente:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. È possibile verificare la nuova estensione pubblicata passando a [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installare l'estensione da Visual Studio Marketplace

Ora che l'estensione è stata pubblicata, installarla Visual Studio e testarla.

1. In Visual Studio scegliere Estensioni e aggiornamenti **dal** menu **Strumenti.**

2. Fare **clic su Online** e quindi cercare TestPublish.

3. Fare clic su **Download**. L'estensione verrà quindi pianificata per l'installazione.

4. Per completare l'installazione, chiudere tutte le istanze di Visual Studio.

## <a name="remove-the-extension"></a>Rimuovere l'estensione

È possibile rimuovere l'estensione dal Visual Studio Marketplace e dal computer.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Per rimuovere l'estensione dal Marketplace tramite la riga di comando

1. Se si vuole rimuovere un'estensione, usare il comando seguente:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Al completamento dell'eliminazione dell'estensione, verrà visualizzato il messaggio della riga di comando seguente:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Per rimuovere l'estensione dal computer

1. In Visual Studio scegliere Estensioni e aggiornamenti **dal** menu **Strumenti**.

2. Selezionare "MyVsixExtension" e quindi fare clic su **Disinstalla**. L'estensione verrà quindi pianificata per la disinstallazione.

3. Per completare la disinstallazione, chiudere tutte le istanze di Visual Studio.
