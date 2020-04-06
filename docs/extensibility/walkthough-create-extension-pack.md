---
title: Creazione di un pacchetto di estensione con il modello di elemento del pacchetto di estensione Documenti Microsoft
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: acangialosi
ms.author: anthc
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: fa1c141e18a3870eaad4b155d816e30ee207f45d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697755"
---
# <a name="walkthrough-create-an-extension-pack"></a>Procedura dettagliata: Creare un pacchetto di estensione

Un Extension Pack è un insieme di estensioni che possono essere installate insieme. I pacchetti di estensione consentono di condividere facilmente le estensioni preferite con altri utenti o di raggruppare un insieme di estensioni per un particolare scenario.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, Visual Studio SDK è incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.Starting in Visual Studio 2015, the Visual Studio SDK is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installazione di Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

La funzionalità Extension Pack è disponibile a partire da Visual Studio 15.8 Preview 2.The Extension Pack feature is available starting with Visual Studio 15.8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Creare un'estensione con un modello di elemento Extension PackCreate an extension with an Extension Pack item template

Il modello di elemento Extension Pack crea un extension Pack con un set di estensioni che possono essere installate insieme.

1. Nella finestra di dialogo **Nuovo progetto** cercare "vsix" e selezionare **Progetto VSIX**. Per **Nome progetto**digitare "Test Extension Pack". Selezionare **Create** (Crea).

2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** > **nuovo elemento**. Passare al nodo **Extensibility** di Visual C, quindi selezionare **Extension Pack**. Lasciare il nome file predefinito (ExtensionPack1.cs).

3. ExtensionPack1.vsext viene aggiunto che contiene il codice seguente

   ```json
   {
    "id": "ExtensionPack1",
    "name": "ExtensionPack1",
    "description": "Read about creating extension packs at https://aka.ms/vsextpack",
    "version": "1.0.0.0",
    "extensions": [  // List of extensions that are included in the Extension Pack.
      {
        "vsixId": "41858b2d-ff0b-4a43-80b0-f1b2d6084935", // The vsix id of the extension you want to   include.
        "name": "AlignAssignments"
      },
      {
          "vsixId": "42374550-426a-400e-96f9-237682e8dea6",
        "name": "CopyAsHtml"
      }
    ]
   }
   ```

4. Il vsixid dell'estensione da includere in Extension Pack è disponibile in [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Trovare l'estensione che si desidera includere e fare clic su **Copia ID**. È possibile aggiornare il **vsixId** esistente nel file precedente o aggiungere un'altra estensione all'elenco.

    ![Copia VsixId da Marketplace](media/vsixid-marketplace.png)

5. Compilare il progetto e caricare l'estensione nel Marketplace. Vedere [Pubblicazione di un'estensione](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)di Visual Studio .

> [!NOTE]
> Un pacchetto di estensione può installare solo le estensioni disponibili in [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o nella raccolta [privata.](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Installare il pacchetto di estensione da Visual Studio Marketplace

Ora che l'estensione è pubblicata, installarla in Visual Studio e testarla.

::: moniker range="vs-2017"

1. In Visual Studio scegliere **Estensioni e aggiornamenti**dal menu **Strumenti** .

::: moniker-end

::: moniker range=">=vs-2019"

1. In Visual Studio scegliere **Estensioni gestite**dal menu **Estensioni** .

::: moniker-end

2. Fare clic su **Online** e quindi cercare "Test Extension Pack".

3. Fare clic su **Download**. L'estensione e il relativo elenco di estensioni incluse nel pacchetto di estensione verranno quindi pianificati per l'installazione.

4. Di seguito è riportata una visualizzazione di download del pacchetto di estensione di esempio della finestra di dialogo **Gestisci estensioni.** Se si preferisce installare solo alcune delle estensioni incluse nel pacchetto di estensione, è possibile modificare l'elenco delle estensioni in **Pianificato per l'installazione**.

    ![Scarica il pacchetto di estensioni dal Marketplace](media/vside-extensionpack.png)

5. Per completare l'installazione, chiudere tutte le istanze di Visual Studio.To complete the installation, close all instances of Visual Studio.

## <a name="remove-the-extension"></a>Rimuovere l'estensione

Per rimuovere l'estensione dal computer:

::: moniker range="vs-2017"

1. In Visual Studio scegliere **Estensioni e aggiornamenti**dal menu **Strumenti** .

::: moniker-end

::: moniker range=">=vs-2019"

1. In Visual Studio scegliere **Estensioni gestite**dal menu **Estensioni** .

::: moniker-end

2. Selezionare **Test Extension Pack** e quindi fare clic su **Disinstalla**. L'estensione e il relativo elenco di estensioni incluse nel pacchetto di estensione verranno quindi pianificate per la disinstallazione.

3. Per completare la disinstallazione, chiudere tutte le istanze di Visual Studio.To complete the uninstallation, close all instances of Visual Studio.
