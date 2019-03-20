---
title: Creare un pacchetto di estensione con il modello di elemento di estensione Pack | Microsoft Docs
ms.date: 07/27/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: gregvanl
ms.author: gregvanl
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: 7899a096bb2a56e93ea55a4ba0a17cde272bd615
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58193705"
---
# <a name="walkthrough-create-an-extension-pack"></a>Procedura dettagliata: Creare un pacchetto di estensione

Un pacchetto di estensione è un set di estensioni che possono essere installati insieme. Pacchetti di estensione consentono di condividere le estensioni preferite con altri utenti o un set di estensioni insieme per uno scenario specifico del bundle con facilità.

## <a name="prerequisites"></a>Prerequisiti

A partire da Visual Studio 2015, Visual Studio SDK è incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

La funzionalità di estensione Pack è disponibile a partire da Visual Studio 15.8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Creare un'estensione con un modello di elemento di pacchetto di estensioni

Il modello di elemento Extension Pack crea un pacchetto di estensione con set di estensioni che possono essere installati insieme.

1. Nel **nuovo progetto** finestra di dialogo, cercare "vsix" e selezionare **progetto VSIX**. Per la **nome progetto**, digitare "Pacchetto di estensioni di Test". Scegliere **Crea**.

2. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Add** > **nuovo elemento**. Passare a Visual c# **estendibilità** nodo e selezionare **Extension Pack**. Lasciare il nome file predefinito (ExtensionPack1.cs).

3. Aggiunta di file ExtensionPack1.vsext che contiene il codice seguente

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

4. Vsixid di estensione da includere nel pacchetto di estensione è reperibile nella [Visual Studio Marketplace](https://marketplace.visualstudio.com/). Trovare l'estensione che si desidera includere e fare clic su **ID copia**. È possibile aggiornare quello esistente **vsixId** nell'esempio precedente di file o aggiungere un'altra estensione all'elenco.

    ![Copiare VsixId da Marketplace](media/vsixid-marketplace.png)

5. Compilare il progetto e caricare un'estensione nel Marketplace. Visualizzare [pubblicazione di un'estensione di Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

> [!NOTE]
> Un pacchetto di estensione può essere installata solo le estensioni che sono disponibili nel [Visual Studio Marketplace](https://marketplace.visualstudio.com/) oppure [raccolta privata](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md).

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Installare il pacchetto di estensioni da Visual Studio Marketplace

Ora che la pubblicazione dell'estensione, installarlo in Visual Studio e testarlo.

::: moniker range="vs-2017"

1. In Visual Studio sul **degli strumenti** menu, fare clic su **estensioni e aggiornamenti**.

::: moniker-end

::: moniker range=">=vs-2019"

1. In Visual Studio sul **estensioni** menu, fare clic su **estensioni gestite**.

::: moniker-end

2. Fare clic su **Online** e quindi cercare "Pacchetto di estensioni di Test".

3. Scegliere **Download**. L'estensione e all'elenco delle estensioni incluse nel pacchetto di estensione verrà pianificate per l'installazione.

4. Ecco una visualizzazione di download Extension Pack di esempio il **gestire le estensioni** finestra di dialogo. Se si preferisce installare solo alcune delle estensioni incluse nel pacchetto di estensione, è possibile modificare l'elenco delle estensioni in **pianificati per installare**.

    ![Scaricare il pacchetto di estensione dal Marketplace](media/vside-extensionpack.png)

5. Per completare l'installazione, chiudere tutte le istanze di Visual Studio.

## <a name="remove-the-extension"></a>Rimuovere l'estensione.

Per rimuovere l'estensione dal computer:

::: moniker range="vs-2017"

1. In Visual Studio sul **degli strumenti** menu, fare clic su **estensioni e aggiornamenti**.

::: moniker-end

::: moniker range=">=vs-2019"

1. In Visual Studio sul **estensioni** menu, fare clic su **estensioni gestite**.

::: moniker-end

2. Selezionare **pacchetto di estensioni di Test** e quindi fare clic su **Disinstalla**. L'estensione e all'elenco delle estensioni incluse nel pacchetto di estensione verrà pianificate per la disinstallazione.

3. Per completare la disinstallazione, chiudere tutte le istanze di Visual Studio.
