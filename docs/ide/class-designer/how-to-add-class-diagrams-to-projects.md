---
title: Aggiungere diagrammi classi ai progetti (Progettazione classi)
description: Informazioni su come progettare, modificare ed eseguire il refactoring di classi e altri tipi, aggiungere un diagramma classi al progetto C#, Visual Basic o C++.
ms.custom: SEO-VS-2020
ms.date: 05/08/2018
ms.topic: how-to
helpviewer_keywords:
- class diagrams, creating
- Class Designer [Visual Studio], opening
ms.assetid: 0eac1b54-2711-4e4b-9654-a0c429c08c8f
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 539c3f9bbd59de6bc1df1bf60f39d96b1b1f439b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069508"
---
# <a name="how-to-add-class-diagrams-to-projects"></a>Procedura: Aggiungere diagrammi classi ai progetti

Aggiungere un diagramma di classi al progetto C#, Visual Basic o C++ per progettare, modificare ed effettuare il refactoring di classi e altri tipi. Per visualizzare diverse parti del codice in un progetto, aggiungere più diagrammi di classi al progetto.

Non è possibile creare diagrammi di classi da progetti che condividono codice tra più app. Per creare diagrammi classi UML, vedere [Creare diagrammi e progetti di modellazione UML](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

## <a name="install-the-class-designer-component"></a>Installare il componente Progettazione classi

Se non è stato installato il componente **Progettazione classi**, seguire questa procedura per installarlo.

1. Aprire il **Programma di installazione di Visual Studio** dal menu Start di Windows o selezionando **Strumenti** > **Ottieni strumenti e funzionalità** dalla barra dei menu in Visual Studio.

   Il **Programma di installazione di Visual Studio** si apre.

1. Selezionare la scheda **Singoli componenti** e quindi scorrere verso il basso fino alla categoria **Strumenti per il codice**.

1. Selezionare **Progettazione classi** e quindi **Modifica**.

   ![Componente Progettazione classi nel Programma di installazione di Visual Studio](media/class-designer-component.png)

   Viene avviata l'installazione del componente **Progettazione classi**.

## <a name="add-a-blank-class-diagram-to-a-project"></a>Aggiungere un diagramma classi vuoto a un progetto

1. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e quindi scegliere **Aggiungi** > **Nuovo elemento**. In caso contrario, **premere CTRL** + **MAIUSC** + **A.**

   Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo elemento.

2. Espandere **Elementi comuni**  >  **Generale** e quindi selezionare Diagramma classi **dall'elenco** dei modelli. Per i progetti Visual C++ consultare la categoria **Utilità** per trovare il modello **Diagramma classi**.

   > [!NOTE]
   > Se il modello **Diagramma classi** non viene visualizzato, [seguire i passaggi](#install-the-class-designer-component) per installare il componente **Progettazione classi** per Visual Studio.

   Il diagramma classi viene aperto in Progettazione classi e appare come file con estensione *CD* in **Esplora soluzioni**. È possibile trascinare forme e linee nel diagramma da **Casella degli strumenti**.

Per aggiungere più diagrammi classi, ripetere questa procedura.

## <a name="add-a-class-diagram-based-on-existing-types"></a>Aggiungere un diagramma classi basato su tipi esistenti

In **Esplora soluzioni** aprire il menu di scelta rapida di un file di classe (clic con il pulsante destro del mouse) e quindi scegliere **Visualizza diagramma classi**.

-oppure-

In **Visualizzazione classi** aprire il menu di scelta rapida del tipo o dello spazio dei nomi e quindi scegliere **Visualizza diagramma classi**.

> [!TIP]
> Se **Visualizzazione classi** non è aperto, aprire **Visualizzazione classi** **dal** menu Visualizza.

## <a name="to-display-the-contents-of-a-complete-project-in-a-class-diagram"></a>Per visualizzare il contenuto di un progetto completo in un diagramma classi

In **Esplora soluzioni** o Visualizzazione classi fare clic con il pulsante destro del mouse sul progetto e scegliere Visualizza **,** quindi scegliere Visualizza **diagramma classi.**

Verrà creato un diagramma classi compilato automaticamente.

> [!NOTE]
> Progettazione classi non è disponibile nei progetti .NET Core.

## <a name="see-also"></a>Vedi anche

- [Procedura: Creare tipi utilizzando Progettazione classi](how-to-create-types.md)
- [Procedura: Visualizzare i tipi esistenti](how-to-view-existing-types.md)
- [Progettare e visualizzare classi e tipi](designing-and-viewing-classes-and-types.md)
