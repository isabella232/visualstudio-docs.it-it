---
title: 'Procedura: Modificare il tipo restituito di un metodo DataContext (O-R Designer) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: be57c5d8a298f37f9cffc7cc4b363651efbc9c2b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59665649"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Procedura: Modificare il tipo restituito di un metodo DataContext (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> (creato in base a una stored procedure o funzione) varia a seconda della posizione in cui si rilascia la stored procedure o funzione in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Se si rilascia un elemento direttamente in una classe di entità esistente, viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità (se lo schema dei dati restituiti dalla stored procedure o funzione corrisponde alla forma della classe di entità). Se invece si rilascia un elemento in un'area vuota di [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], viene creato un metodo <xref:System.Data.Linq.DataContext> che restituisce un tipo generato automaticamente. È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e fare clic sulla proprietà **Return Type** nella finestra **Proprietà**.  
  
> [!NOTE]
>  Non è possibile ripristinare la restituzione del tipo generato automaticamente da parte dei metodi <xref:System.Data.Linq.DataContext>, che presentano un tipo restituito impostato su una classe di entità, mediante la finestra **Proprietà**. Per ripristinare la restituzione di un tipo generato automaticamente da parte di un metodo <xref:System.Data.Linq.DataContext>, è necessario trascinare nuovamente l'oggetto di database originale in Progettazione relazionale oggetti.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Per modificare il tipo restituito di un metodo DataContext dal tipo generato automaticamente in una classe di entità  
  
1.  Selezionare il metodo <xref:System.Data.Linq.DataContext> nel riquadro dei metodi.  
  
2.  Selezionare **Return Type** nella finestra **Proprietà** e quindi selezionare una classe di entità disponibile nell'elenco **Return Type**. Se la classe di entità desiderata non è presente nell'elenco, aggiungerla o crearla nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] per aggiungerlo all'elenco.  
  
3.  Salvare il file .dbml.  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-an-entity-class-back-to-the-auto-generated-type"></a>Per modificare nuovamente il tipo restituito di un metodo DataContext da una classe di entità nel tipo generato automaticamente  
  
1.  Selezionare il metodo <xref:System.Data.Linq.DataContext> nel riquadro dei metodi ed eliminarlo.  
  
2.  Trascinare l'oggetto di database dalla **Esplora Server**/**Esplora Database** in un'area vuota della finestra di Progettazione relazionale oggetti.  
  
3.  Salvare il file .dbml.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura: Creare metodi DataContext di cui viene eseguito il mapping a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)
