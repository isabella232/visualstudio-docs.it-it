---
title: 'Procedura: Estendere il codice generato da Object Relational Designer'
description: Vedere come estendere il codice generato da Object Relational Designer (O/R Designer). Aggiungere codice a una classe di entità. Aggiungere codice a un oggetto DataContext.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7bc1c926108efb6223788caa695bdb4028645252
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631302"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Procedura: Estendere il codice generato da Object Relational Designer
Il codice generato da **O/R Designer** viene rigenerato quando vengono apportate modifiche alle classi di entità e ad altri oggetti nell'area di progettazione. A causa di questa rigenerazione, in genere tutto il codice aggiunto al codice generato viene sovrascritto quando la finestra di progettazione rigenera il codice. Progettazione **O/R** consente di generare file di classe parziali in cui è possibile aggiungere codice non sovrascritto. Un esempio di aggiunta di codice personalizzato al codice generato da **O/R Designer** è l'aggiunta della convalida dei dati LINQ to SQL classi (entità). Per altre informazioni, vedere [Procedura: Aggiungere la convalida alle classi di entità](../data-tools/how-to-add-validation-to-entity-classes.md).

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="add-code-to-an-entity-class"></a>Aggiungere codice a una classe di entità

### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Per creare una classe parziale e aggiungere codice a una classe di entità

1. Aprire o creare un nuovo file LINQ to SQL classes (file **con estensione dbml)** in **O/R Designer.** Fare doppio clic sul file **con estensione dbml** in **Esplora soluzioni** o **Esplora database**.

2. In **Object Relational Designer** fare clic con il pulsante destro del mouse sulla classe per cui si vuole aggiungere la convalida e quindi scegliere **Visualizza codice**.

     Viene aperto l'editor del codice con una classe parziale per la classe di entità selezionata.

3. Aggiungere il codice nella dichiarazione di classe parziale per la classe di entità.

## <a name="add-code-to-a-datacontext"></a>Aggiungere codice a un oggetto DataContext

### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Per creare una classe parziale e aggiungere codice a un oggetto DataContext

1. Aprire o creare un nuovo file LINQ to SQL classes (file **con estensione dbml)** in **O/R Designer.** Fare doppio clic sul file **con estensione dbml** in **Esplora soluzioni** o **Esplora database**.

2. In **Progettazione O/R fare** clic con il pulsante destro del mouse su un'area vuota nella finestra di progettazione e quindi scegliere **Visualizza codice**.

     Viene aperto l'editor del codice con una classe parziale per l'oggetto DataContext.

3. Aggiungere il codice nella dichiarazione di classe parziale per l'oggetto DataContext.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
