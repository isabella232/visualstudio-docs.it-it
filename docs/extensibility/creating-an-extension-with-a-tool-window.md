---
title: Creazione di un'estensione con una finestra degli strumenti | Microsoft Docs
description: Informazioni su come usare il modello di progetto VSIX e il modello di elemento della finestra degli strumenti personalizzata per creare un'estensione con una finestra degli strumenti.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f956aa520bca79a84fe203093c225cfeb8389ba1
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089199"
---
# <a name="create-an-extension-with-a-tool-window"></a>Creare un'estensione con una finestra degli strumenti

Questa procedura illustra come usare il modello di progetto VSIX e il modello di elemento della **finestra degli strumenti personalizzata** per creare un'estensione con una finestra degli strumenti.

## <a name="prerequisites"></a>Prerequisiti

 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

### <a name="create-a-tool-window"></a>Crea una finestra degli strumenti

1. Creare un progetto VSIX denominato **FirstWindow**. È possibile trovare il modello di progetto VSIX nella finestra di dialogo **nuovo progetto** cercando "VSIX".

2. Quando si apre il progetto, aggiungere un modello di elemento della finestra degli strumenti denominato **finestra**. Nella **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi**  >  **nuovo elemento**. Nella finestra di dialogo **Aggiungi nuovo elemento** passare a estensibilità di **Visual C#**  >   e selezionare **finestra degli strumenti personalizzata**. Nel campo **nome** nella parte inferiore della finestra modificare il nome del file della finestra degli strumenti in *finestra. cs*.

3. Compilare il progetto e avviare il debug.

   Viene visualizzata l'istanza sperimentale di Visual Studio. Per ulteriori informazioni sull'istanza sperimentale, vedere [l'istanza sperimentale](../extensibility/the-experimental-instance.md).

4. Nell'istanza sperimentale, passare a **Visualizza**  >  **altre finestre**.

   Verrà visualizzata una voce di menu per la **finestra**. quindi farvi clic.

   Verrà visualizzata una finestra degli strumenti con il titolo **finestra** e un pulsante per **fare clic su me!.**
