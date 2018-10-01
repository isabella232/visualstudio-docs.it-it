---
title: 'Procedura: creare metodi DataContext mappati a stored procedure e funzioni (O-R Designer) | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e7ca32f1-50b3-48af-ad92-ceafd749296a
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 62d250946e634627c16dbd3b56fce370c11e1f3f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527149"
---
# <a name="how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-or-designer"></a>Procedura: creare metodi DataContext mappati a stored procedure e funzioni (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: metodi creare DataContext mappati a stored procedure e funzioni (O-R Designer)](https://docs.microsoft.com/visualstudio/data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer).  
  
  
È possibile aggiungere stored procedure e funzioni per i [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] come <xref:System.Data.Linq.DataContext> metodi. La chiamata al metodo e passando i parametri obbligatori viene eseguita la stored procedure o funzione nel database e restituisce i dati nel tipo restituito del <xref:System.Data.Linq.DataContext> (metodo). Per informazioni dettagliate sui <xref:System.Data.Linq.DataContext> metodi, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).  
  
> [!NOTE]
>  Le stored procedure possono essere usate anche per eseguire l'override del comportamento in fase di esecuzione [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] predefinito che esegue i comandi di inserimento, aggiornamento ed eliminazione durante il salvataggio delle modifiche dalle classi di entità in un database. Per altre informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="creating-datacontext-methods"></a>Creazione di metodi DataContext  
 È possibile creare <xref:System.Data.Linq.DataContext> metodi trascinando stored procedure o funzioni da **Esplora Server/Esplora Database** nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
> [!NOTE]
>  Il tipo restituito del metodo <xref:System.Data.Linq.DataContext> generato varia a seconda della posizione in cui si rilascia la stored procedure o funzione in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Il rilascio degli elementi direttamente in una classe di entità esistente crea un metodo <xref:System.Data.Linq.DataContext> con il tipo restituito della classe di entità, mentre il rilascio degli elementi in un'area vuota di [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] crea un metodo <xref:System.Data.Linq.DataContext> che restituisce un tipo generato automaticamente. È possibile modificare il tipo restituito di un <xref:System.Data.Linq.DataContext> metodo dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di una <xref:System.Data.Linq.DataContext> metodo, selezionarlo e controllare il **Return Type** proprietà nel **proprietà** finestra. Per altre informazioni, vedere [procedura: modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-datacontext-methods-that-return-automatically-generated-types"></a>Per creare metodi DataContext che restituiscono tipi generati automaticamente  
  
1.  Nelle **Esplora Server**/**Esplora Database**, espandere il **Stored Procedures** nodo del database di cui si sta lavorando.  
  
2.  Individuare la stored procedure desiderata e trascinarla in un'area vuota di [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Il <xref:System.Data.Linq.DataContext> metodo viene creato con un tipo restituito generato automaticamente e visualizzato nei **metodi** riquadro.  
  
#### <a name="to-create-datacontext-methods-that-have-the-return-type-of-an-entity-class"></a>Per creare metodi DataContext con il tipo restituito di una classe di entità  
  
1.  Nelle **Esplora Server**/**Esplora Database**, espandere il **Stored Procedures** nodo del database di cui si sta lavorando.  
  
2.  Individuare la stored procedure desiderata e trascinarla in una classe di entità esistente di [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
     Il <xref:System.Data.Linq.DataContext> metodo viene creato con il tipo restituito della classe di entità selezionato e viene visualizzato nei **metodi** riquadro.  
  
> [!NOTE]
>  Per informazioni su come modificare il tipo restituito predefinito esistente <xref:System.Data.Linq.DataContext> metodi, vedere [procedura: modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Introduzione a LINQ in Visual Basic](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)   
 [Procedura: Scrivere query LINQ in C#](http://msdn.microsoft.com/library/45e47fcc-cfa1-4b72-b161-d038ae87bd23)

