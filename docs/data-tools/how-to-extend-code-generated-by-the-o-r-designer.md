---
title: 'Procedura: Estendere il codice generato da Object Relational Designer'
description: Esaminare come estendere il codice generato da Object Relational Designer (O/R Designer). Aggiungere codice a una classe di entità. Aggiungere codice a un oggetto DataContext.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7d3468bbc3e3a1f1250cf2c679087b9606b87a18
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94434922"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Procedura: Estendere il codice generato da Object Relational Designer
Il codice generato da **O/R Designer** viene rigenerato quando vengono apportate modifiche alle classi di entità e ad altri oggetti nell'area di progettazione. A causa di questa rigenerazione, in genere tutto il codice aggiunto al codice generato viene sovrascritto quando la finestra di progettazione rigenera il codice. La **finestra di progettazione di O/R** consente di generare file di classe parziali in cui è possibile aggiungere codice che non viene sovrascritto. Un esempio di aggiunta di codice personalizzato al codice generato da **O/R Designer** è l'aggiunta della convalida dei dati alle classi LINQ to SQL (Entity). Per altre informazioni, vedere [procedura: aggiungere la convalida alle classi di entità](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Aggiungere codice a una classe di entità

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Per creare una classe parziale e aggiungere codice a una classe di entità

1. Aprire o creare un nuovo file di classi LINQ to SQL (file con **estensione dbml** ) in **Progettazione relazionale di o/R**. (Fare doppio clic sul file **. dbml** in **Esplora soluzioni** o **Esplora database** ).

2. In **Object Relational Designer** fare clic con il pulsante destro del mouse sulla classe per cui si vuole aggiungere la convalida e quindi scegliere **Visualizza codice**.

     Viene aperto l'editor del codice con una classe parziale per la classe di entità selezionata.

3. Aggiungere il codice nella dichiarazione di classe parziale per la classe di entità.

## <a name="add-code-to-a-datacontext"></a>Aggiungere codice a un oggetto DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Per creare una classe parziale e aggiungere codice a un oggetto DataContext

1. Aprire o creare un nuovo file di classi LINQ to SQL (file con **estensione dbml** ) in **Progettazione relazionale di o/R**. (Fare doppio clic sul file **. dbml** in **Esplora soluzioni** o **Esplora database** ).

2. In **Progettazione relazionale** , fare clic con il pulsante destro del mouse su un'area vuota della finestra di progettazione, quindi scegliere **Visualizza codice**.

     Viene aperto l'editor del codice con una classe parziale per l'oggetto DataContext.

3. Aggiungere il codice nella dichiarazione di classe parziale per l'oggetto DataContext.

## <a name="see-also"></a>Vedere anche

- [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
