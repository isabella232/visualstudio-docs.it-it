---
title: Creazione di un'estensione con una finestra degli strumenti Documenti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17f72cf130c5ff0f2d6d03ca8c460aa98ea39111
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739549"
---
# <a name="create-an-extension-with-a-tool-window"></a>Creare un'estensione con una finestra degli strumentiCreate an extension with a tool window

In questa procedura viene illustrato come utilizzare il modello di progetto VSIX e il modello di elemento Finestra degli strumenti **personalizzata** per creare un'estensione con una finestra degli strumenti.

## <a name="prerequisites"></a>Prerequisiti

 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="create-a-tool-window"></a>Creare una finestra degli strumenti

1. Creare un progetto VSIX denominato **FirstWindow**. È possibile trovare il modello di progetto VSIX nella finestra di dialogo **Nuovo progetto** cercando "vsix".

2. Quando si apre il progetto, aggiungere un modello di elemento della finestra degli strumenti denominato **MyWindow**. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** > **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a**Estensibilità** **di Visual C,** > quindi selezionare **Finestra degli strumenti personalizzata**. Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file della finestra degli strumenti *in MyWindow.cs*.

3. Compilare il progetto e avviare il debug.

   Viene visualizzata l'istanza sperimentale di Visual Studio.The experimental instance of Visual Studio appears. Per ulteriori informazioni sull'istanza sperimentale, vedere [Istanza sperimentale](../extensibility/the-experimental-instance.md).

4. Nell'istanza sperimentale, passare a **Visualizza** > **altre finestre**.

   Verrà visualizzata una voce di menu per **MyWindow**. quindi farvi clic.

   Verrà visualizzata una finestra degli strumenti con il titolo **MyWindow** e un pulsante che indica **Click Me!.**
