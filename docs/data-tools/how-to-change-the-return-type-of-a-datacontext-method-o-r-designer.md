---
title: 'Procedura: Modificare il tipo restituito di un metodo DataContext (Object Relational Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 77d7b98367e343f90827429ad50be91527f7f303
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939437"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Procedura: Modificare il tipo restituito di un metodo DataContext (Object Relational Designer)
Il tipo restituito di una <xref:System.Data.Linq.DataContext> metodo (creato in una stored procedure o funzione di base) è diverso a seconda di dove si rilascia la stored procedure o funzione nel **O/R Designer**. Se si rilascia un elemento direttamente in una classe di entità esistente, viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità (se lo schema dei dati restituiti dalla stored procedure o funzione corrisponde alla forma della classe di entità). Se si rilascia un elemento in un'area vuota del **O/R Designer**, un <xref:System.Data.Linq.DataContext> metodo che restituisce un tipo generato automaticamente è stato creato. È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e fare clic sulla proprietà **Return Type** nella finestra **Proprietà**.

> [!NOTE]
>  Non è possibile ripristinare la restituzione del tipo generato automaticamente da parte dei metodi <xref:System.Data.Linq.DataContext>, che presentano un tipo restituito impostato su una classe di entità, mediante la finestra **Proprietà**. Per ripristinare la restituzione di un tipo generato automaticamente da parte di un metodo <xref:System.Data.Linq.DataContext>, è necessario trascinare nuovamente l'oggetto di database originale in **Object Relational Designer**.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Per modificare il tipo restituito di un metodo DataContext dal tipo generato automaticamente in una classe di entità

1.  Selezionare il metodo <xref:System.Data.Linq.DataContext> nel riquadro dei metodi.

2.  Selezionare **Return Type** nella finestra **Proprietà** e quindi selezionare una classe di entità disponibile nell'elenco **Return Type**. Se la classe di entità desiderata non è presente nell'elenco, aggiungerla o crearla nel **O/R Designer** per aggiungerlo all'elenco.

3.  Salvare il file *.dbml*.

## <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Per modificare nuovamente il tipo restituito di un metodo DataContext da una classe di entità nel tipo generato automaticamente

1.  Selezionare il metodo <xref:System.Data.Linq.DataContext> nel riquadro **Metodi** ed eliminarlo.

2.  Trascinare l'oggetto di database dalla **Esplora Server** oppure **Esplora Database** in un'area vuota del **O/R Designer**.

3.  Salvare il file *.dbml*.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Metodi DataContext (Object Relational Designer)](../data-tools/datacontext-methods-o-r-designer.md)
- [Procedura: Creare metodi DataContext di cui viene eseguito il mapping a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)