---
title: Refactoring di classi e tipi (Progettazione classi) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: eaee3dae25f5f2e5544a2521a7bce0201b45a3e2
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441146"
---
# <a name="refactoring-classes-and-types-class-designer"></a>Refactoring di classi e tipi (Progettazione classi)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si effettua il refactoring del codice, si modifica la struttura interna di quest'ultimo e il modo in cui i relativi oggetti vengono progettati, rendendo il codice più comprensibile, gestibile ed efficiente senza modificarne il comportamento esterno. Per ridurre le operazioni necessarie e la possibilità di introdurre bug durante il refactoring del codice Visual C# .NET, Visual Basic .NET o C++ nel progetto di Visual Studio, usare Progettazione classi e la finestra Dettagli classe.  
  
> [!NOTE]
> I file di un progetto possono essere di sola lettura perché il progetto è sotto il controllo del codice sorgente e non è stato estratto, perché si tratta di un progetto a cui si fa riferimento o perché i file sono contrassegnati come di sola lettura sul disco. Quando si lavora in un progetto in uno di questi stati, è possibile salvare il lavoro in vari modi a seconda dello stato del progetto. Ciò vale per il refactoring del codice e anche per il codice che viene modificato in altro modo, ad esempio tramite modifica diretta. Per altre informazioni, vedere [Visualizzare le informazioni di sola lettura (Progettazione classi)](http://msdn.microsoft.com/33e2d3a9-1668-4d10-ae56-fa09b3156e0a).  
  
## <a name="common-tasks"></a>Attività comuni  
  
|Attività|Contenuto di supporto|  
|----------|------------------------|  
|**Refactoring di classi:** è possibile usare le operazioni di refactoring per suddividere una classe in classi parziali o per implementare una classe di base astratta.|-   [Procedura: Dividere una classe in classi parziali (Progettazione classi)](../ide/how-to-split-a-class-into-partial-classes-class-designer.md)|  
|**Uso di interfacce:** In Progettazione classi è possibile implementare un'interfaccia nel diagramma classi connettendola a una classe che fornisce il codice per i metodi di interfaccia.|-   [Procedura: Implementare un'interfaccia (Progettazione classi)](../ide/how-to-implement-an-interface-class-designer.md)|  
|**Refactoring di tipi, membri di tipi e parametri:** con Progettazione classi è possibile rinominare i tipi, eseguire l'override dei membri dei tipi oppure spostarli da un tipo all'altro. È anche possibile creare tipi nullable.|-   [Ridenominazione di tipi e membri dei tipi](../ide/refactoring-classes-and-types-class-designer.md#RenamingTypesAndMembers)<br />-   [Spostamento dei membri dei tipi da un tipo a un altro](../ide/refactoring-classes-and-types-class-designer.md#MovingTypeMembers)<br />-   [Procedura: Creare un tipo nullable (Progettazione classi)](../ide/how-to-create-a-nullable-type-class-designer.md)|  
  
### <a name="RenamingTypesAndMembers"></a> Ridenominazione di tipi e membri dei tipi  
 In Progettazione classi è possibile rinominare un tipo o un membro di un tipo nel diagramma classi o nella finestra Proprietà. Nella finestra Dettagli classe è possibile modificare il nome di un membro ma non di un tipo. La ridenominazione di un tipo o di un membro di un tipo verrà propagata a tutte le finestre e i percorsi di codice in cui è presente il nome precedente.  
  
##### <a name="to-rename-a-name-in-the-class-designer"></a>Per cambiare un nome in Progettazione classi  
  
1. Nel diagramma classi selezionare il tipo o il membro e fare clic sul nome.  
  
     Il nome del membro diventerà modificabile.  
  
2. Digitare il nuovo nome per il tipo o il membro del tipo.  
  
##### <a name="to-rename-a-name-in-the-class-details-window"></a>Per cambiare un nome nella finestra Dettagli classe  
  
1. Per visualizzare la finestra Dettagli classe, fare clic con il pulsante destro del mouse sul tipo o sul membro del tipo, quindi scegliere **Dettagli classe**.  
  
     Verrà visualizzata la finestra Dettagli classe.  
  
2. Nella colonna **Nome** modificare il nome del membro del tipo.  
  
3. Per spostare lo stato attivo dalla cella, premere **INVIO** oppure fare clic all'esterno della cella.  
  
    > [!NOTE]
    > Nella finestra Dettagli classe è possibile modificare il nome di un membro ma non di un tipo.  
  
##### <a name="to-rename-a-name-in-the-properties-window"></a>Per cambiare un nome nella finestra Proprietà  
  
1. Nel diagramma classi o nella finestra Dettagli classe fare clic con il pulsante destro del mouse sul tipo o sul membro, quindi scegliere **Proprietà**.  
  
     Verrà visualizzata la finestra Proprietà con le proprietà relative al tipo o al membro del tipo.  
  
2. Nella proprietà **Nome** modificare il nome del tipo o del membro del tipo.  
  
     Il nuovo nome verrà propagato a tutte le finestre e i percorsi di codice del progetto corrente in cui è presente il nome precedente.  
  
### <a name="MovingTypeMembers"></a> Spostamento dei membri dei tipi da un tipo a un altro  
 In **Progettazione classi**è possibile spostare un membro del tipo da un tipo a un altro, se entrambi sono visibili nel diagramma classi corrente.  
  
##### <a name="to-move-a-type-member-from-one-type-to-another"></a>Per spostare un membro da un tipo a un altro  
  
1. In un tipo visibile nell'area di progettazione fare clic con il pulsante destro del mouse sul membro da spostare in un altro tipo, quindi scegliere **Taglia**.  
  
2. Fare clic con il pulsante destro del mouse sul tipo di destinazione, quindi scegliere **Incolla**.  
  
     La proprietà verrà rimossa dal tipo di origine e visualizzata in quello di destinazione.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Visualizzazione dei tipi e delle relazioni (Progettazione classi)](../ide/viewing-types-and-relationships-class-designer.md)||  
|[Progettazione di classi e tipi (Progettazione classi)](../ide/designing-classes-and-types-class-designer.md)||
