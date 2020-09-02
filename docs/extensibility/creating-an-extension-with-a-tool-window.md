---
title: Creazione di un'estensione con una finestra degli strumenti | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 597b84854dd398abee9dc21090e085273bc94c75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903894"
---
# <a name="create-an-extension-with-a-tool-window"></a>Creare un'estensione con una finestra degli strumenti

Questa procedura illustra come usare il modello di progetto VSIX e il modello di elemento della **finestra degli strumenti personalizzata** per creare un'estensione con una finestra degli strumenti.

## <a name="prerequisites"></a>Prerequisiti

 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Crea una finestra degli strumenti

1. Creare un progetto VSIX denominato **FirstWindow**. È possibile trovare il modello di progetto VSIX nella finestra di dialogo **nuovo progetto** cercando "VSIX".

2. Quando si apre il progetto, aggiungere un modello di elemento della finestra degli strumenti denominato **finestra**. Nella **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi**  >  **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a estensibilità di **Visual C#**  >  **Extensibility** e selezionare **finestra degli strumenti personalizzata**. Nel campo **nome** nella parte inferiore della finestra modificare il nome del file della finestra degli strumenti in *myWindow.cs*.

3. Compilare il progetto e avviare il debug.

   Viene visualizzata l'istanza sperimentale di Visual Studio. Per ulteriori informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).

4. Nell'istanza sperimentale, passare a **Visualizza**  >  **altre finestre**.

   Verrà visualizzata una voce di menu per la **finestra**. quindi farvi clic.

   Verrà visualizzata una finestra degli strumenti con il titolo **finestra** e un pulsante per **fare clic su me!.**
