---
title: 'Procedura: modificare il tipo restituito di un metodo DataContext (O-R Designer) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c5b66bff-6dbb-43c0-bffa-317133ca5b9e
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4c944d951fe7139a59dbc0e9c4e00ae342420871
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531287"
---
# <a name="how-to-change-the-return-type-of-a-datacontext-method-or-designer"></a>Procedura: modificare il tipo restituito di un metodo DataContext (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: modificare il tipo restituito di un metodo DataContext (O-R Designer)](https://docs.microsoft.com/visualstudio/data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer).  
  
  
Il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> (creato in base a una stored procedure o funzione) varia a seconda della posizione in cui si rilascia la stored procedure o funzione in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Se si rilascia un elemento direttamente in una classe di entità esistente, viene creato un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità (se lo schema dei dati restituiti dalla stored procedure o funzione corrisponde alla forma della classe di entità). Se invece si rilascia un elemento in un'area vuota di [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], viene creato un metodo <xref:System.Data.Linq.DataContext> che restituisce un tipo generato automaticamente. È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di una <xref:System.Data.Linq.DataContext> metodo, selezionarla e fare clic sul **Return Type** proprietà nel **proprietà** finestra.  
  
> [!NOTE]
>  Non è possibile ripristinare <xref:System.Data.Linq.DataContext> metodi che hanno un tipo restituito impostato su una classe di entità per restituire il tipo generato automaticamente usando il **proprietà** finestra. Per ripristinare la restituzione di un tipo generato automaticamente da parte di un metodo <xref:System.Data.Linq.DataContext>, è necessario trascinare nuovamente l'oggetto di database originale in Progettazione relazionale oggetti.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-change-the-return-type-of-a-datacontext-method-from-the-auto-generated-type-to-an-entity-class"></a>Per modificare il tipo restituito di un metodo DataContext dal tipo generato automaticamente in una classe di entità  
  
1.  Selezionare il metodo <xref:System.Data.Linq.DataContext> nel riquadro dei metodi.  
  
2.  Selezionare **Return Type** nel **delle proprietà** classe finestra e quindi selezionare un'entità disponibile nel **Return Type** elenco. Se la classe di entità desiderata non è presente nell'elenco, aggiungerla o crearla nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] per aggiungerlo all'elenco.  
  
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

