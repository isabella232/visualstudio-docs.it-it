---
title: "Procedura dettagliata: Pubblicazione di un'estensione di Visual Studio tramite la riga di comando | Microsoft Docs"
ms.date: 07/12/2018
ms.topic: conceptual
helpviewer_keywords:
- publishing extensions
- extension, publishing
ms.assetid: 6ff9efc4-919d-4071-a80d-6dbdd2ceb2f8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aebd1cbd46eeaf80d165140dc58c5e81a0e02b91
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695375"
---
# <a name="walkthrough-publishing-a-visual-studio-extension-via-command-line"></a>Procedura dettagliata: Pubblicazione di un'estensione di Visual Studio tramite la riga di comando

Questa procedura dettagliata illustra come pubblicare un'estensione di Visual Studio in Visual Studio Marketplace tramite riga di comando. Quando si aggiunge l'estensione nel Marketplace, gli sviluppatori possono usare la [ **estensioni e aggiornamenti** ](../ide/finding-and-using-visual-studio-extensions.md) finestra di dialogo per cercare estensioni nuove e aggiornate.

VsixPublisher.exe è lo strumento da riga di comando per la pubblicazione di estensioni di Visual Studio nel Marketplace. È possibile accedervi da ${VSInstallDir}\VSSDK\VisualStudioIntegration\Tools\Bin\VsixPublisher.exe. I comandi disponibili su questo strumento sono: **pubblicare**, **createPublisher**, **deletePublisher**, **deleteExtension**,  **account di accesso**, **disconnessione**.

## <a name="commands"></a>Comandi:

### <a name="publish"></a>publish

Pubblica un'estensione nel Marketplace. L'estensione può essere un file vsix, un file exe o msi o un collegamento. Se l'estensione esiste già con la stessa versione, l'estensione verrà sovrascritta. Se l'estensione non esiste già, creerà una nuova estensione.

|Opzioni di comando |Descrizione |
|---------|---------|
|payload (obbligatorio) | Un percorso per il payload per la pubblicazione o un collegamento da usare come "Altre informazioni sull'URL". |
|publishManifest (obbligatorio) | Percorso di pubblicazione del manifesto file da utilizzare. |
|ignoreWarnings | Elenco di avvisi da ignorare durante la pubblicazione di un'estensione. Questi avvisi vengono visualizzati come i messaggi della riga di comando quando si pubblica un'estensione. (ad esempio, "VSIXValidatorWarning01, VSIXValidatorWarning02")
|personalAccessToken | Personal Access Token (PAT) che viene usato per autenticare il server di pubblicazione. Se non specificato, viene acquisito il token di accesso personale degli utenti ha eseguito l'accesso. |

```
VsixPublisher.exe publish -payload "{path to vsix}" -publishManifest "{path to vs-publish.json}" -ignoreWarnings "VSIXValidatorWarning01,VSIXValidatorWarning02"
```

### <a name="createpublisher"></a>createPublisher

Crea un server di pubblicazione nel Marketplace. Registra inoltre il server di pubblicazione al computer per le azioni future (ad esempio, l'eliminazione/pubblicazione di un'estensione).

|Opzioni di comando |Descrizione |
|---------|---------|
|displayName (obbligatorio) | Nome visualizzato del server di pubblicazione. |
|Nome editore (obbligatorio) | Il nome del server di pubblicazione (ad esempio, l'identificatore). |
|personalAccessToken (obbligatorio) | Token di accesso personale usato per autenticare il server di pubblicazione. |
|shortDescription | Una breve descrizione del server di pubblicazione (non un file). |
|longDescription | Descrizione lunga del server di pubblicazione (non un file). |

```
VsixPublisher.exe createPublisher -publisherName "{Publisher Name}" -displayName "{Publisher Display Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deletepublisher"></a>deletePublisher

Elimina un server di pubblicazione nel Marketplace.

|Opzioni di comando |Descrizione |
|---------|---------|
|Nome editore (obbligatorio) | Il nome del server di pubblicazione (ad esempio, l'identificatore). |
|personalAccessToken (obbligatorio) | Token di accesso personale usato per autenticare il server di pubblicazione. |

```
VsixPublisher.exe deletePublisher -publisherName "{Publisher Name}" -personalAccessToken "{Personal Access Token}"
```

### <a name="deleteextension"></a>deleteExtension

Elimina un'estensione dal Marketplace.

|Opzioni di comando |Descrizione |
|---------|---------|
|extensionName (obbligatorio) | Il nome dell'estensione da eliminare. |
|Nome editore (obbligatorio) | Il nome del server di pubblicazione (ad esempio, l'identificatore). |
|personalAccessToken | Token di accesso personale usato per autenticare il server di pubblicazione. Se non specificato, viene acquisito il token di accesso personale degli utenti ha eseguito l'accesso. |

```
VsixPublisher.exe deleteExtension -extensionName "{Extension Name}" -publisherName "{Publisher Name}"
```

### <a name="login"></a>Accesso

Accede al computer un server di pubblicazione.

|Opzioni di comando |Descrizione |
|---------|---------|
|personalAccessToken (obbligatorio | Token di accesso personale usato per autenticare il server di pubblicazione. |
|Nome editore (obbligatorio) | Il nome del server di pubblicazione (ad esempio, l'identificatore). |
|overwrite | Specifica che qualsiasi server di pubblicazione esistente devono essere sovrascritti con il nuovo token di accesso personale. |

```
VsixPublisher.exe login -personalAccessToken "{Personal Access Token}" -publisherName "{Publisher Name}"
```

### <a name="logout"></a>logout

Registra un server di pubblicazione dal computer.

|Opzioni di comando |Descrizione |
|---------|---------|
|Nome editore (obbligatorio) | Il nome del server di pubblicazione (ad esempio, l'identificatore). |
|ignoreMissingPublisher | Specifica che lo strumento non di errore se il server di pubblicazione specificato non è già effettuato aggiuntivo. |

```
VsixPublisher.exe logout -publisherName "{Publisher Name}"
```

## <a name="publishmanifest-file"></a>file publishManifest

Viene usato da un file di publishManifest il **pubblicare** comando. Rappresenta tutti i metadati sull'estensione nel Marketplace deve conoscere. Se l'estensione in fase di caricamento proviene da un'estensione VSIX, la proprietà "identity" necessario solo il "internalName" impostare. Questo avviene perché il resto delle proprietà "identity" può essere generato dal file vsixmanifest. Se l'estensione è un file msi o exe o un'estensione di collegamento, l'utente deve fornire i campi obbligatori nella proprietà "identity". Il resto del manifesto contiene informazioni specifiche per il Marketplace (ad esempio, categorie, fatto che domande e risposte è abilitata, e così via.).

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

Esempio di file publishManifest MSI o EXE o un collegamento:

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

File di asset possono essere forniti per l'incorporamento di elementi quali immagini nel file Leggimi. Ad esempio, se l'estensione include il documento di Markdown seguente "Panoramica":

```markdown
TestExtension
...
This is test extension.
![Test logo](images/testlogo.png "Test logo")
```

Per risolvere il "images/testlogo.png" nell'esempio precedente, un utente può fornire "assetFiles" nel loro pubblicazione manifesto come di seguito:

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

Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-visual-studio-extension"></a>Creare un'estensione di Visual Studio

In questo caso, si userà un'estensione VSPackage predefinito, ma gli stessi passaggi sono validi per ogni tipo di estensione.

1. Creare un pacchetto VSPackage in c# denominato "TestPublish" che dispone di un comando di menu. Per altre informazioni, vedere [creazione della prima estensione: Hello World](../extensibility/extensibility-hello-world.md).

### <a name="package-your-extension"></a>Creare un pacchetto di estensione

1. Aggiornare l'estensione vsixmanifest con le informazioni corrette sul nome del prodotto, autore e versione.

   ![update extension vsixmanifest](media/update-extension-vsixmanifest.png)

2. Compilare l'estensione **rilascio** modalità. L'estensione verrà ora essere compresso come un progetto VSIX nella cartella \bin\Release.

3. È possibile fare doppio clic il progetto VSIX per verificare l'installazione.

### <a name="test-the-extension"></a>Testare l'estensione

 Prima di distribuire l'estensione, compilare e testarlo per verificare che sia installato correttamente nell'istanza sperimentale di Visual Studio.

1. In Visual Studio, avviare il debug. Per aprire un'istanza sperimentale di Visual Studio.

2. Nell'istanza sperimentale, passare al **degli strumenti** dal menu **estensioni e aggiornamenti...** . L'estensione TestPublish dovrebbe essere visualizzato nel riquadro centrale e abilitato.

3. Nel **strumenti** menu, assicurarsi che venga visualizzato il comando di test.

### <a name="publish-the-extension-to-the-marketplace-via-command-line"></a>Pubblicare l'estensione nel marketplace tramite riga di comando

1. Assicurarsi di avere compilato la versione dell'estensione e che sia aggiornato.

2. Assicurarsi che il file publishmanifest.json e overview.md creati.

3. Aprire la riga di comando e passare alla directory \VSSDK\VisualStudioIntegration\Tools\Bin\ ${VSInstallDir}.

4. Per creare un nuovo server di pubblicazione, usare il comando seguente:

   ```
   VsixPublisher.exe createPublisher -publisherName "TestVSIXPublisher" -displayName "Test VSIX Publisher" -personalAccessToken "{Personal Access Token that is used to authenticate the publisher. If not provided, the pat is acquired from the logged-in users.}"
   ```

5. Al termine della creazione del server di pubblicazione, si verrà visualizzato il messaggio della riga di comando seguente:

   ```
   Added 'Test VSIX Publisher' as a publisher on the Marketplace.
   ```

6. È possibile verificare il nuovo server di pubblicazione creata passando a [Visual Studio Marketplace](https://marketplace.visualstudio.com/manage/publishers)

7. Per pubblicare una nuova estensione, usare il comando seguente:

   ```
   VsixPublisher.exe publish -payload "{Path to vsix file}"  -publishManifest "{path to publishManifest file}"
   ```

8. Al termine della creazione del server di pubblicazione, si verrà visualizzato il messaggio della riga di comando seguente:

   ```
   Uploaded 'MyVsixExtension' to the Marketplace.
   ```

9. È possibile verificare la nuova estensione è stato pubblicato, passare a [Visual Studio Marketplace](https://marketplace.visualstudio.com/)

### <a name="install-the-extension-from-the-visual-studio-marketplace"></a>Installare l'estensione da Visual Studio Marketplace

Ora che la pubblicazione dell'estensione, installarlo in Visual Studio e testarlo.

1. In Visual Studio sul **degli strumenti** menu, fare clic su **estensioni e aggiornamenti...** .

2. Fare clic su **Online** e quindi cercare TestPublish.

3. Scegliere **Download**. Quindi l'estensione verrà pianificata per l'installazione.

4. Per completare l'installazione, chiudere tutte le istanze di Visual Studio.

## <a name="remove-the-extension"></a>Rimuovere l'estensione.

È possibile rimuovere l'estensione da Visual Studio Marketplace e dal computer.

### <a name="to-remove-the-extension-from-the-marketplace-via-command-line"></a>Per rimuovere l'estensione dal Marketplace tramite riga di comando

1. Se si desidera rimuovere un'estensione, usare il comando seguente:

   ```
   VsixPublisher.exe deleteExtension -publisherName "TestVSIXPublisher" -extensionName "MyVsixExtension"
   ```

2. Al completamento dell'eliminazione dell'estensione, si verrà visualizzato il messaggio della riga di comando seguente:

   ```
   Removed 'MyVsixExtension' from the Marketplace.
   ```

### <a name="to-remove-the-extension-from-your-computer"></a>Per rimuovere l'estensione dal computer

1. In Visual Studio sul **degli strumenti** menu, fare clic su **estensioni e aggiornamenti...** .

2. Selezionare "MyVsixExtension" e quindi fare clic su **Disinstalla**. Quindi l'estensione verrà pianificata per la disinstallazione.

3. Per completare la disinstallazione, chiudere tutte le istanze di Visual Studio.
