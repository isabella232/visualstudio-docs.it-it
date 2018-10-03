---
title: 'Procedura: riempire un set di dati | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- TableAdapter.GetData
- TableAdapter.Fill
- datasets [Visual Basic], filling
- DataTable objects, loading
- data [Visual Basic], loading into datasets
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: c2bba5c7bcdf1453129c6c3677e750c0e5599bac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528726"
---
# <a name="how-to-fill-a-dataset-with-data"></a>Procedura: riempire un set di dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La frase "riempire un set di dati con dati" si intende il caricamento dei dati nei singoli <xref:System.Data.DataTable> gli oggetti che costituiscono il set di dati. Riempire le tabelle di dati tramite l'esecuzione di query TableAdapter o tramite l'adattatore dati di esecuzione (ad esempio, <xref:System.Data.SqlClient.SqlDataAdapter>) comandi.  
  
 Se si devono utilizzare schede di dati o oggetti TableAdapter dipende da come è stato creato il set di dati. Se è stato usato gli strumenti di progettazione nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ad esempio il [configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f), il set di dati contiene oggetti TableAdapter. Per altre informazioni su oggetti TableAdapter, vedere [panoramica degli oggetti TableAdapter](../data-tools/tableadapter-overview.md). Se è stato creato il set di dati a livello di codice, è necessario in genere creare adattatori di dati per caricare dati nelle tabelle di dati.  
  
> [!NOTE]
>  Quando si trascinano elementi dal [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) in un form, il codice per inserire dati nella tabella di dati viene aggiunto automaticamente al `Form_Load` gestore dell'evento. Aprire il form nell'editor del codice per visualizzare la sintassi esatta per riempire le tabelle specifiche. Se non vuoi compilare la tabella quando il form viene caricato, è possibile spostare il codice in un altro metodo oppure rimuoverlo completamente.  
  
## <a name="filling-a-dataset-using-a-tableadapter"></a>La compilazione di un set di dati mediante un TableAdapter  
 È possibile chiamare una query del TableAdapter per caricare i dati nelle tabelle di dati in un set di dati. Passare il <xref:System.Data.DataTable> vuoi compilare per la query TableAdapter. Se la query accetta parametri, passarle anche al metodo. Se il set di dati contiene più tabelle, si avranno TableAdapter separato per ogni tabella e ogni tabella dovrà essere compilata separatamente.  
  
> [!NOTE]
>  Per impostazione predefinita, ogni volta che si esegue una query TableAdapter, i dati nella tabella viene cancellati prima i risultati della query viene caricata nella tabella. È possibile mantenere i dati esistenti nella tabella e aggiungere i risultati tramite l'impostazione dell'oggetto TableAdapter `ClearBeforeFill` proprietà `false`.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-tableadapter"></a>Per riempire un set di dati mediante un TableAdapter  
  
1.  Aprire il form o un componente di **Editor di codice**.  
  
2.  Aggiungere codice in un punto qualsiasi all'interno dell'applicazione in cui è necessario caricare una tabella di dati con i dati. Se la query non accetta parametri, passare il <xref:System.Data.DataTable> da riempire. Il codice dovrebbe essere simile al seguente:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#4)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#4)]  
  
3.  Se la query accetta parametri, passare il <xref:System.Data.DataTable> vuoi fill e i parametri previsti dalla query. A seconda dei parametri effettivi nella query, il codice avrebbe un aspetto simile agli esempi seguenti:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#5)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#5)]  
  
## <a name="filling-a-dataset-using-a-dataadapter"></a>La compilazione di un set di dati utilizzando un DataAdapter  
 Chiamare l'adattatore dati di `Fill` (metodo). In questo modo, l'adapter eseguire l'istruzione SQL o stored procedure fa riferimento nella relativa `SelectCommand` proprietà e inserire i risultati in una tabella nel set di dati. Se il set di dati contiene più tabelle, si devono disporre di schede di dati separato per ogni tabella e ogni tabella dovrà essere compilata separatamente.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-dataadapter"></a>Per riempire un set di dati con i dati usando un oggetto DataAdapter  
  
-   Chiamare il <xref:System.Data.Common.DataAdapter.Fill%2A> metodo del <xref:System.Data.Common.DataAdapter>, passando il <xref:System.Data.DataSet> o <xref:System.Data.DataTable> per caricare i dati. Ad esempio:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#6)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#6)]  
  
     In genere è necessario fornire il nome del <xref:System.Data.DataTable> per caricare i dati. Se si passa il nome di un <xref:System.Data.DataSet> invece di una tabella di dati specifico, un <xref:System.Data.DataTable> denominata `Table1` viene aggiunto al set di dati e caricato con i risultati dal database (invece di caricare i dati in un oggetto esistente <xref:System.Data.DataTable> nel set di dati). Per altre informazioni, vedere [popolamento di un set di dati da un oggetto DataAdapter](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
## <a name="see-also"></a>Vedere anche  
 [Compilare i set di dati usando oggetti TableAdapter](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica dei dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Salvataggio di dati](../data-tools/saving-data.md)