---
title: 'Procedura: Estendere il codice generato da Object Relational Designer'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6ff7dfc9a83028b866f7601b9b41c685262356ac
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55909604"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Procedura: Estendere il codice generato da Object Relational Designer
Codice generato per il **O/R Designer** viene rigenerato quando vengono apportate modifiche alle classi di entità e altri oggetti nell'area di progettazione. A causa di questa rigenerazione, in genere tutto il codice aggiunto al codice generato viene sovrascritto quando la finestra di progettazione rigenera il codice. Il **O/R Designer** offre la possibilità di generare file di classe parziale in cui è possibile aggiungere il codice che non vengano sovrascritti. Un esempio di aggiunta di codice personalizzato al codice generato per il **O/R Designer** viene aggiunta la convalida dei dati a LINQ alle classi di SQL (entity). Per altre informazioni, vedere [procedura: aggiungere la convalida a classi di entità](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Aggiungere codice a una classe di entità

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Per creare una classe parziale e aggiungere codice a una classe di entità

1.  Aprire o creare un nuovo file LINQ to SQL classi (**dbml** file) nella **O/R Designer**. (Fare doppio clic sul **dbml** del file in **Esplora soluzioni** oppure **Esplora Database**.)

2.  In **Object Relational Designer** fare clic con il pulsante destro del mouse sulla classe per cui si vuole aggiungere la convalida e quindi scegliere **Visualizza codice**.

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
- [Procedura dettagliata: Creazione di classi LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)