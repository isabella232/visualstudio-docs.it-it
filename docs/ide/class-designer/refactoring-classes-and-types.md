---
title: Rinominare e spostare classi e tipi in Progettazione classi
description: Informazioni su come rinominare e spostare classi e tipi usando Progettazione classi e la finestra Dettagli classe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.ClassDesigner.OverrideMembersDialog
helpviewer_keywords:
- members, overriding
- overriding members
- classes [Visual Studio], refactoring
- type members, overriding
- refactoring, types
- types [Visual Studio], refactoring
- Class Designer [Visual Studio], refactoring classes
- refactoring, classes
ms.assetid: dcf07bb4-fa3b-4224-9dec-566fd924a8ce
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: d217f85d57e4e44e824f708343764a89f3ba2efe
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101947"
---
# <a name="refactor-classes-and-types-in-class-designer"></a>Refactoring di classi e tipi in Progettazione classi

Quando si effettua il refactoring del codice, si modifica la struttura interna di quest'ultimo e il modo in cui i relativi oggetti vengono progettati, rendendo il codice più comprensibile, gestibile ed efficiente senza modificarne il comportamento esterno. Per ridurre le operazioni necessarie e la possibilità di introdurre bug durante il refactoring del codice C# , Visual Basic o C++ nel progetto di Visual Studio, usare Progettazione classi e la finestra Dettagli classe.

> [!NOTE]
> I file di un progetto possono essere di sola lettura perché il progetto è incluso nel controllo del codice sorgente e non è stato estratto, perché si tratta di un progetto a cui si fa riferimento o perché i file sono contrassegnati come di sola lettura su disco. Quando si lavora in un progetto in uno di questi stati, è possibile salvare il lavoro in vari modi a seconda dello stato del progetto. Ciò vale per il refactoring del codice e anche per il codice che viene modificato in altro modo, ad esempio tramite modifica diretta.

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto di supporto|
|----------| - |
|**Refactoring di classi:** è possibile usare le operazioni di refactoring per suddividere una classe in classi parziali o per implementare una classe base astratta.|-   [Procedura: dividere una classe in classi parziali](how-to-split-a-class-into-partial-classes.md)|
|**Uso di interfacce:** in Progettazione classi è possibile implementare un'interfaccia nel diagramma classi connettendola a una classe che fornisce il codice per i metodi di interfaccia.|-   [Procedura: implementare un'interfaccia](how-to-implement-an-interface.md)|
|**Refactoring di tipi, membri dei tipi e parametri:** con Progettazione classi è possibile rinominare i tipi, eseguire l'override dei membri dei tipi oppure spostarli da un tipo all'altro. È anche possibile creare tipi nullable.|-   [Ridenominazione di tipi e membri dei tipi](#rename-types-and-type-members)<br />-   [Spostamento dei membri dei tipi da un tipo a un altro](#move-type-members-from-one-type-to-another)<br />-   [Procedura: Creare un tipo nullable](how-to-create-a-nullable-type.md)|

## <a name="rename-types-and-type-members"></a>Ridenominazione di tipi e membri dei tipi

In Progettazione classi è possibile rinominare un tipo o un membro di un tipo nel diagramma classi o nella finestra **Proprietà**. Nella finestra **Dettagli classe** è possibile modificare il nome di un membro ma non di un tipo. La ridenominazione di un tipo o di un membro di un tipo verrà propagata a tutte le finestre e i percorsi di codice in cui è presente il nome precedente.

### <a name="rename-in-the-class-designer"></a>Modificare un nome in Progettazione classi

1. Nel diagramma classi selezionare il tipo o il membro e selezionare il nome.

     Il nome del membro diventerà modificabile.

2. Digitare il nuovo nome per il tipo o il membro del tipo.

### <a name="rename-in-the-class-details-window"></a>Modificare un nome nella finestra Dettagli classe

1. Per visualizzare la finestra **Dettagli classe**, fare clic con il pulsante destro del mouse sul tipo o sul membro del tipo e quindi scegliere **Dettagli classe**.

     Verrà visualizzata la finestra **Dettagli classe**.

2. Nella colonna **Nome** modificare il nome del membro del tipo.

3. Per spostare lo stato attivo dalla cella, premere **INVIO** oppure fare clic all'esterno della cella.

    > [!NOTE]
    > Nella finestra **Dettagli classe** è possibile modificare il nome di un membro ma non di un tipo.

### <a name="rename-in-the-properties-window"></a>Modificare un nome nella finestra Proprietà

1. Nel diagramma classi o nella finestra **Dettagli classe** fare clic con il pulsante destro del mouse sul tipo o sul membro e quindi scegliere **Proprietà**.

     Verrà visualizzata la finestra **Proprietà** con le proprietà relative al tipo o al membro del tipo.

2. Nella proprietà **Nome** modificare il nome del tipo o del membro del tipo.

     Il nuovo nome verrà propagato a tutte le finestre e i percorsi di codice del progetto corrente in cui è presente il nome precedente.

## <a name="move-type-members-from-one-type-to-another"></a>Spostamento dei membri dei tipi da un tipo a un altro

In **Progettazione classi** è possibile spostare un membro del tipo da un tipo a un altro. Entrambi i tipi devono essere visibili nel diagramma classi corrente.

1. In un tipo visibile nell'area di progettazione fare clic con il pulsante destro del mouse sul membro da spostare in un altro tipo e quindi scegliere **Taglia**.

2. Fare clic con il pulsante destro del mouse sul tipo di destinazione e quindi scegliere **Incolla**.

     La proprietà verrà rimossa dal tipo di origine e visualizzata in quello di destinazione.

## <a name="see-also"></a>Vedi anche

- [Progettazione di classi e tipi](designing-and-viewing-classes-and-types.md)
