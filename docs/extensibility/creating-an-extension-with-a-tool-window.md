---
title: Creazione di un'estensione con una finestra degli strumenti | Microsoft Docs
description: Informazioni su come usare il modello di progetto VSIX e il modello di elemento Finestra degli strumenti personalizzata per creare un'estensione con una finestra degli strumenti.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
ms.assetid: 585b0a3a-f85b-4f92-81bb-9ca499bb8a89
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: cde02a72f180fa497c599c661f12c4d279a3e1ba
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627683"
---
# <a name="create-an-extension-with-a-tool-window"></a>Creare un'estensione con una finestra degli strumenti

In questa procedura si apprenderà come usare il modello di progetto VSIX e il modello di elemento **Finestra** degli strumenti personalizzata per creare un'estensione con una finestra degli strumenti.

## <a name="prerequisites"></a>Prerequisiti

 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

### <a name="create-a-tool-window"></a>Creare una finestra degli strumenti

1. Creare un progetto VSIX denominato **FirstWindow**. È possibile trovare il modello di progetto VSIX nella finestra **di dialogo Nuovo Project** ricerca di "vsix".

2. Quando si apre il progetto, aggiungere un modello di elemento della finestra degli strumenti denominato **MyWindow**. Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento**. Nella finestra **di dialogo Aggiungi nuovo** elemento passare a **Estendibilità di Visual C#**  >   e selezionare Finestra degli **strumenti personalizzata**. Nel campo **Nome** nella parte inferiore della finestra modificare il nome del file della finestra degli strumenti in *MyWindow.cs*.

3. Compilare il progetto e avviare il debug.

   Viene visualizzata l'istanza sperimentale di Visual Studio. Per altre informazioni sull'istanza sperimentale, vedere [Istanza sperimentale](../extensibility/the-experimental-instance.md).

4. Nell'istanza sperimentale passare **a Visualizza**  >  **altri Windows**.

   Verrà visualizzata una voce di menu per **MyWindow**. quindi farvi clic.

   Verrà visualizzata una finestra degli strumenti con il titolo **MyWindow** e un pulsante che dice **Click Me!.**
