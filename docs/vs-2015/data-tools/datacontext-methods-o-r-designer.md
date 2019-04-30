---
title: Metodi DataContext (O-R Designer) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c149f4e5-3b61-4c33-892e-3e26d47f3eeb
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c5af5beb71dc2164df38180078cf7489f2da391e
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431145"
---
# <a name="datacontext-methods-or-designer"></a>Metodi DataContext (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DataContext] (assetId:///T:System.Data.Linq.DataContext?qualifyHint=False & autoUpgrade = True) metodi (nel contesto del [strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)) sono metodi del <xref:System.Data.Linq.DataContext> classi che eseguono stored procedure e funzioni in un database.  
  
 La classe <xref:System.Data.Linq.DataContext> rappresenta una classe [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] che funge da canale tra un database SQL Server e le classi di entità [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] con mapping a tale database. La classe <xref:System.Data.Linq.DataContext> contiene le informazioni sulla stringa di connessione e i metodi per la connessione a un database e la modifica dei dati presenti in esso. Per impostazione predefinita, la classe <xref:System.Data.Linq.DataContext> contiene diversi metodi che è possibile chiamare, ad esempio il metodo <xref:System.Data.Linq.DataContext.SubmitChanges%2A> che invia dati aggiornati dalle classi [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] al database. È anche possibile creare metodi <xref:System.Data.Linq.DataContext> aggiuntivi mappati a stored procedure e funzioni. In altre parole, la chiamata a questi metodi personalizzati determinerà l'esecuzione della stored procedure o funzione nel database a cui è stato eseguito il mapping del metodo <xref:System.Data.Linq.DataContext>. È possibile aggiungere nuovi metodi alla classe <xref:System.Data.Linq.DataContext> nello stesso modo in cui si aggiungono per estendere qualsiasi classe. Tuttavia, nelle discussioni sulle <xref:System.Data.Linq.DataContext> metodi nel contesto del [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], è il <xref:System.Data.Linq.DataContext> metodi che eseguono il mapping a stored procedure e funzioni che vengono discussi.  
  
## <a name="methods-pane"></a>Riquadro Metodi  
 I metodi <xref:System.Data.Linq.DataContext> con mapping a stored procedure e funzioni vengono visualizzati nel riquadro dei metodi di [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Il riquadro dei metodi è il riquadro lungo il lato del **entità** riquadro (l'area di progettazione principale). Il riquadro dei metodi sono elencati tutti <xref:System.Data.Linq.DataContext> metodi che è stato creato con il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Per impostazione predefinita, il riquadro dei metodi è vuoto. Trascinare le stored procedure o funzioni da **Esplora Server**/**Esplora Database** nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] creare <xref:System.Data.Linq.DataContext> metodi e popolare il riquadro dei metodi. Per altre informazioni, vedere [Procedura: Creare metodi DataContext mappati a stored procedure e funzioni (Object Relational Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md).  
  
> [!NOTE]
> Aprire e chiudere il riquadro dei metodi facendo clic con il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] e quindi scegliendo **Nascondi riquadro metodi** o **Mostra riquadro metodi**, oppure utilizzare il tasto di scelta rapida CTRL + 1.  
  
## <a name="two-types-of-datacontext-methods"></a>Due tipi di metodi DataContext  
 I metodi DataContext sono metodi con mapping a stored procedure e funzioni nel database. È possibile creare e aggiungere metodi DataContext nel riquadro dei metodi di [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Esistono due tipi distinti di metodi <xref:System.Data.Linq.DataContext>: quelli che restituiscono uno o più set di risultati e quelli che non restituiscono alcun set di risultati:  
  
- Metodi <xref:System.Data.Linq.DataContext> che restituiscono uno o più set di risultati:  
  
     Creare questo tipo di metodo <xref:System.Data.Linq.DataContext> quando l'applicazione deve eseguire stored procedure e funzioni nel database e restituire i risultati. Per altre informazioni, vedere [Procedura: Creare metodi DataContext mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md), System.Data.Linq.ISingleResult\<T >, e <xref:System.Data.Linq.IMultipleResults>.  
  
- Metodi <xref:System.Data.Linq.DataContext> che non restituiscono set di risultati, ad esempio inserimenti, aggiornamenti ed eliminazioni per una classe di entità specifica.  
  
     Creare questo tipo di metodo <xref:System.Data.Linq.DataContext> quando l'applicazione deve eseguire stored procedure invece di usare il comportamento [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] predefinito per salvare i dati modificati tra una classe di entità e il database. Per altre informazioni, vedere [Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).  
  
## <a name="return-types-of-datacontext-methods"></a>Tipi restituiti dei metodi DataContext  
 Quando si trascinano stored procedure e funzioni dal **Esplora Server**/**Esplora Database** nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], il tipo restituito dell'oggetto generato <xref:System.Data.Linq.DataContext> differisce (metodo) a seconda della posizione in cui si rilascia l'elemento. Eliminazione degli elementi direttamente in una classe di entità esistente crea un <xref:System.Data.Linq.DataContext> metodo con il tipo restituito della classe di entità; rilascio degli elementi in un'area vuota del [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] (in dei riquadri) crea un <xref:System.Data.Linq.DataContext> metodo che restituisce un tipo generato automaticamente. Questo tipo creato è dotato di un nome corrispondente a quello della stored procedure o funzione e di proprietà con mapping ai campi restituiti dalla stored procedure o funzione.  
  
> [!NOTE]
> È possibile modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext> dopo averlo aggiunto al riquadro dei metodi. Per controllare o modificare il tipo restituito di un metodo <xref:System.Data.Linq.DataContext>, selezionarlo e controllare la proprietà **Return Type** nella finestra **Proprietà**. Per altre informazioni, vedere [Procedura: Modificare il tipo restituito di un metodo DataContext (Object Relational Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md).  
  
 Gli oggetti trascinati dal database nell'area Progettazione relazionale oggetti vengono denominati automaticamente, in base al nome degli oggetti nel database. Se si trascina più volte lo stesso oggetto, i vari nomi vengono distinti grazie all'aggiunta di un numero alla fine del nuovo nome. Se i nomi degli oggetti di database contengono spazi o caratteri non supportati in Visual Basic o C#, lo spazio o il carattere non valido viene sostituito con un carattere di sottolineatura.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Stored procedure](http://msdn.microsoft.com/library/4d23dd7a-a85f-44ff-a717-af7d0950c0fc)   
 [Procedura: Creare metodi DataContext mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md)   
 [Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)   
 [Procedura dettagliata: Personalizzazione di inserimento, aggiornamento ed eliminazione, il comportamento delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
