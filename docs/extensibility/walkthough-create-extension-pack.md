---
title: Creare un pacchetto di estensione
description: Informazioni su come creare un pacchetto di estensione con il modello di elemento del pacchetto di estensione
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
ms.openlocfilehash: b5a0021061aefceafc2b048a3e231d9c0300db7b
ms.sourcegitcommit: 2a201c93ed526b0f7e5848657500f1111b08ac2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2020
ms.locfileid: "89742921"
---
# <a name="walkthrough-create-an-extension-pack"></a>Procedura dettagliata: Creare un pacchetto di estensione

Un pacchetto di estensione è un set di estensioni che possono essere installate insieme. I pacchetti di estensione consentono di condividere facilmente le estensioni preferite con altri utenti o di raggruppare un set di estensioni per uno scenario specifico.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, Visual Studio SDK è incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

La funzionalità pacchetto di estensione è disponibile a partire da Visual Studio 15,8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Creare un'estensione con un modello di elemento del pacchetto di estensione

Il modello di elemento del pacchetto di estensione crea un pacchetto di estensione con un set di estensioni che possono essere installate insieme.

1. Nella finestra di dialogo **nuovo progetto** cercare "VSIX" e selezionare **progetto VSIX**. Per **nome progetto**, digitare "Test Extension Pack". Selezionare **Create** (Crea).

2. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi**  >  **nuovo elemento**. Passare al nodo **estensibilità** di Visual C# e selezionare **pacchetto di estensione**. Lasciare il nome file predefinito (ExtensionPack1.cs).

3. Viene aggiunto il file ExtensionPack1. vsext che contiene il codice seguente

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

4. Il vsixid dell'estensione da includere nel pacchetto di estensione si trova nel [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Trovare l'estensione che si vuole includere e fare clic su **Copy ID (copia ID**). È possibile aggiornare il **vsixId** esistente nel file precedente o aggiungere un'altra estensione all'elenco.

    ![Copiare VsixId da Marketplace](media/vsixid-marketplace.png)

5. Compilare il progetto e caricare l'estensione nel Marketplace. Vedere [pubblicazione di un'estensione di Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Un pacchetto di estensione può installare solo le estensioni disponibili nella [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o nella [raccolta privata](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Installare il pacchetto di estensione dal Visual Studio Marketplace

Ora che l'estensione è pubblicata, installarla in Visual Studio ed eseguirne il test.

::: moniker range="vs-2017"

1. In Visual Studio scegliere **estensioni e aggiornamenti**dal menu **strumenti** .

::: moniker-end

::: moniker range=">=vs-2019"

1. In Visual Studio scegliere **estensioni gestite**dal menu **estensioni** .

::: moniker-end

2. Fare clic su **online** e quindi cercare "Test Extension Pack".

3. Fare clic su **Download**. L'estensione e l'elenco delle estensioni incluse nel pacchetto di estensione verranno quindi pianificate per l'installazione.

4. Di seguito è riportata una visualizzazione di download del pacchetto di estensione di esempio della finestra di dialogo **Gestisci estensioni** . Se si preferisce installare solo alcune estensioni incluse nel pacchetto di estensione, è possibile modificare l'elenco di estensioni in **pianificato per l'installazione**.

    ![Scaricare il pacchetto di estensione dal Marketplace](media/vside-extensionpack.png)

5. Per completare l'installazione, chiudere tutte le istanze di Visual Studio.

## <a name="remove-the-extension"></a>Rimuovere l'estensione

Per rimuovere l'estensione dal computer:

::: moniker range="vs-2017"

1. In Visual Studio scegliere **estensioni e aggiornamenti**dal menu **strumenti** .

::: moniker-end

::: moniker range=">=vs-2019"

1. In Visual Studio scegliere **estensioni gestite**dal menu **estensioni** .

::: moniker-end

2. Selezionare **Test Extension Pack** e quindi fare clic su **Disinstalla**. L'estensione e l'elenco delle estensioni incluse nel pacchetto di estensione verranno quindi pianificate per la disinstallazione.

3. Per completare la disinstallazione, chiudere tutte le istanze di Visual Studio.
