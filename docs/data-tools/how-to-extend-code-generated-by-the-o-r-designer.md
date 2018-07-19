---
title: 'Procedura: estendere il codice generato da O-R Designer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9da4dca31043104c58122c2eed7aa55ae44ef07e
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089789"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Procedura: estendere il codice generato da O/R Designer
Codice generato per il **O/R Designer** viene rigenerato quando vengono apportate modifiche alle classi di entità e altri oggetti nell'area di progettazione. A causa di questa rigenerazione, in genere tutto il codice aggiunto al codice generato viene sovrascritto quando la finestra di progettazione rigenera il codice. Il **O/R Designer** offre la possibilità di generare file di classe parziale in cui è possibile aggiungere il codice che non vengano sovrascritti. Un esempio di aggiunta di codice personalizzato al codice generato per il **O/R Designer** viene aggiunta la convalida dei dati a LINQ alle classi di SQL (entity). Per altre informazioni, vedere [procedura: aggiungere la convalida a classi di entità](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Aggiungere codice a una classe di entità

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Per creare una classe parziale e aggiungere codice a una classe di entità

1.  Aprire o creare un nuovo file LINQ to SQL classi (**dbml** file) nella **O/R Designer**. (Fare doppio clic sul **dbml** del file in **Esplora soluzioni** oppure **Esplora Database**.)

2.  Nel **O/R Designer**, fare doppio clic su della classe per cui si desidera aggiungere la convalida e quindi fare clic su **Visualizza codice**.

     Viene aperto l'editor del codice con una classe parziale per la classe di entità selezionata.

3.  Aggiungere il codice nella dichiarazione di classe parziale per la classe di entità.

## <a name="add-code-to-a-datacontext"></a>Aggiungere codice a un oggetto DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Per creare una classe parziale e aggiungere codice a un oggetto DataContext

1.  Aprire o creare un nuovo file LINQ to SQL classi (**dbml** file) nella **O/R Designer**. (Fare doppio clic sul **dbml** del file in **Esplora soluzioni** oppure **Esplora Database**.)

2.  Nel **O/R Designer**, fare doppio clic su un'area vuota della finestra di progettazione e quindi fare clic su **Visualizza codice**.

     Viene aperto l'editor del codice con una classe parziale per l'oggetto DataContext.

3.  Aggiungere il codice nella dichiarazione di classe parziale per l'oggetto DataContext.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di LINQ alle classi di SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)