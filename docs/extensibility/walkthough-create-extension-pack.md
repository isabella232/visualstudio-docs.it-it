---
title: Creare un pacchetto di estensione
description: Informazioni su come creare un pacchetto di estensioni con il modello di elemento del pacchetto di estensione
ms.custom: SEO-VS-2020
ms.date: 07/27/2018
ms.topic: tutorial
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 5388EEBA-211D-4114-8CD9-70C899919F7E
author: leslierichardson95
ms.author: lerich
manager: Meng
ms.workload:
- vssdk
ms.openlocfilehash: a84647eef6fa81f55a02689b1adb584c21fd3565a22662e1e9d19b9f1bacb18f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121335082"
---
# <a name="walkthrough-create-an-extension-pack"></a>Procedura dettagliata: Creare un pacchetto di estensione

Un pacchetto di estensioni è un set di estensioni che possono essere installate insieme. I pacchetti di estensione consentono di condividere facilmente le estensioni preferite con altri utenti o di aggregare insieme un set di estensioni per uno scenario specifico.

## <a name="prerequisites"></a>Prerequisiti

A partire Visual Studio 2015, Visual Studio SDK è incluso come funzionalità facoltativa nella Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installazione di Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

La funzionalità Extension Pack è disponibile a partire da Visual Studio 15.8 Preview 2.

## <a name="create-an-extension-with-an-extension-pack-item-template"></a>Creare un'estensione con un modello di elemento del pacchetto di estensioni

Il modello di elemento Extension Pack crea un pacchetto di estensioni con un set di estensioni che possono essere installate insieme.

1. Nella finestra **di dialogo Project** nuovo progetto cercare "vsix" e selezionare **VSIX Project**. Per **Project ,** digitare "Test Extension Pack". Selezionare **Crea**.

2. Nella finestra di **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento.** Passare al nodo **Estendibilità** di Visual C# e selezionare **Extension Pack (Pacchetto estensione).** Lasciare il nome file predefinito (ExtensionPack1.cs).

3. Viene aggiunto il file ExtensionPack1.vsext che contiene il codice seguente

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

4. Il vsixid dell'estensione da includere nel pacchetto di estensione è disponibile in [Visual Studio Marketplace.](https://marketplace.visualstudio.com/) Trovare l'estensione che si vuole includere e fare clic su **Copy ID (Copia ID).** È possibile aggiornare il **vsixId esistente** nel file precedente o aggiungere un'altra estensione all'elenco.

    ![Copiare VsixId da Marketplace](media/vsixid-marketplace.png)

5. Compilare il progetto e caricare l'estensione nel Marketplace. Vedere [Pubblicazione di un'estensione Visual Studio.](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)

> [!NOTE]
> Un pacchetto di estensione può installare solo le estensioni disponibili in [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o nella [raccolta privata.](../extensibility/how-to-create-an-atom-feed-for-a-private-gallery.md)

## <a name="install-the-extension-pack-from-the-visual-studio-marketplace"></a>Installare il pacchetto di estensione da Visual Studio Marketplace

Ora che l'estensione è pubblicata, installarla in Visual Studio e testarla.

::: moniker range="vs-2017"

1. In Visual Studio scegliere Estensioni e aggiornamenti **dal** menu **Strumenti**.

::: moniker-end

::: moniker range=">=vs-2019"

1. In Visual Studio scegliere Estensioni **gestite** dal menu **Estensioni**.

::: moniker-end

2. Fare **clic su Online** e quindi cercare "Test Extension Pack".

3. Fare clic su **Download**. L'estensione e il relativo elenco di estensioni incluse nel pacchetto di estensioni verranno quindi pianificati per l'installazione.

4. Di seguito è riportata una visualizzazione di download del pacchetto di estensione di esempio della **finestra di dialogo Gestisci** estensioni. Se si preferisce installare solo alcune delle estensioni incluse nel pacchetto di estensioni, è possibile modificare l'elenco delle estensioni in **Installazione pianificata.**

    ![Scaricare extension pack da Marketplace](media/vside-extensionpack.png)

5. Per completare l'installazione, chiudere tutte le istanze di Visual Studio.

## <a name="remove-the-extension"></a>Rimuovere l'estensione

Per rimuovere l'estensione dal computer:

::: moniker range="vs-2017"

1. In Visual Studio scegliere Estensioni e aggiornamenti **dal** menu **Strumenti**.

::: moniker-end

::: moniker range=">=vs-2019"

1. In Visual Studio scegliere Estensioni **gestite** dal menu **Estensioni**.

::: moniker-end

2. Selezionare **Test Extension Pack e quindi** fare clic su **Disinstalla.** L'estensione e il relativo elenco di estensioni incluse nel pacchetto di estensioni verranno quindi pianificati per la disinstallazione.

3. Per completare la disinstallazione, chiudere tutte le istanze di Visual Studio.
