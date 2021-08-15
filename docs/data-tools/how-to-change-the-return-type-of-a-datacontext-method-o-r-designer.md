---
title: Modificare il tipo restituito del metodo DataContext
description: Informazioni su come modificare il tipo restituito di un metodo DataContext quando si elimina un stored procedure o una funzione in Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 31a3377dea9bf269f4491bbc20157553ff3012acdc2a0392d68f9f06dc456109
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121264428"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Procedura: Modificare il tipo restituito di un metodo DataContext (Object Relational Designer)
Il tipo restituito di un metodo (creato in base a un stored procedure o a una funzione) varia a seconda della posizione in cui si rilascia il stored procedure o la funzione <xref:System.Data.Linq.DataContext> in **O/R Designer.** Se si rilascia un elemento direttamente in una classe di entità esistente, viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità (se lo schema dei dati restituiti dalla stored procedure o funzione corrisponde alla forma della classe di entità). Se si rilascia un elemento in un'area vuota di **O/R Designer,** viene creato un metodo che restituisce un <xref:System.Data.Linq.DataContext> tipo generato automaticamente. È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e fare clic sulla proprietà **Return Type** nella finestra **Proprietà**.

> [!NOTE]
> Non è possibile ripristinare la restituzione del tipo generato automaticamente da parte dei metodi <xref:System.Data.Linq.DataContext>, che presentano un tipo restituito impostato su una classe di entità, mediante la finestra **Proprietà**. Per ripristinare un metodo per restituire un tipo generato automaticamente, è necessario trascinare nuovamente l'oggetto <xref:System.Data.Linq.DataContext> di database originale in Object Object **Designer.**

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Per modificare il tipo restituito di un metodo DataContext dal tipo generato automaticamente in una classe di entità

1. Selezionare il metodo <xref:System.Data.Linq.DataContext> nel riquadro dei metodi.

2. Selezionare **Return Type** nella finestra **Proprietà** e quindi selezionare una classe di entità disponibile nell'elenco **Return Type**. Se la classe di entità desiderata non è presente nell'elenco, aggiungerla o crearla in **O/R Designer** per aggiungerla all'elenco.

3. Salvare il file *.dbml*.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Per modificare nuovamente il tipo restituito di un metodo DataContext da una classe di entità nel tipo generato automaticamente

1. Selezionare il <xref:System.Data.Linq.DataContext> metodo nel riquadro **Metodi** ed eliminarlo.

2. Trascinare l'oggetto di database **Esplora server** o **Esplora database** in un'area vuota di **O/R Designer.**

3. Salvare il file *.dbml*.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: Creare metodi DataContext di cui viene eseguito il mapping a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
