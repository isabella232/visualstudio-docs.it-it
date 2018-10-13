---
title: "Procedura: creare un'associazione (relazione) tra classi LINQ to SQL (O-R Designer) | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 5c739fcf11cec7eb841b99e58b01ada32cfdfd49
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209365"
---
# <a name="how-to-create-an-association-relationship-between-linq-to-sql-classes-or-designer"></a>Procedura: creare un'associazione (relazione) tra classi LINQ to SQL (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Le associazioni tra classi di entità in [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] sono analoghe alle relazioni tra tabelle in un database. È possibile creare associazioni tra classi di entità usando il **Editor di associazione** nella finestra di dialogo.  
  
 È necessario selezionare una classe padre e una classe figlio quando si usa la **Editor di associazione** finestra di dialogo per creare un'associazione. La classe padre è la classe di entità che contiene la chiave primaria, mentre la classe figlio è la classe di entità che contiene la chiave esterna. Ad esempio, se vengono create classi di entità con mapping alle tabelle Customers e Orders di Northwind, la classe Customer rappresenta la classe padre e la classe Order rappresenta la classe figlio.  
  
> [!NOTE]
>  Quando si trascinano tabelle da **Esplora Server**/**Database Explorer** nel [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), le associazioni vengono create automaticamente in base alle esistente relazioni di chiave esterna nel database.  
  
 Dopo aver creato un'associazione, quando si seleziona l'associazione nella finestra di Progettazione relazionale oggetti, esistono alcune proprietà configurabili nel **proprietà** finestra. (l'associazione rappresenta la linea tra le classi correlate). Nella tabella seguente vengono descritte le proprietà di un'associazione.  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|**cardinalità**|Controlla se l'associazione è uno-a-molti o uno-a-uno.|  
|**Proprietà figlio**|Specifica se creare una proprietà nella chiave esterna dell'associazione nell'elemento padre, che è una raccolta o un riferimento a record figlio. Ad esempio, nell'associazione tra Customer e Order, se il **proprietà figlio** è impostata su **True**, viene creata una proprietà denominata Orders nella classe padre.|  
|**Proprietà padre**|Proprietà nella classe figlio che fa riferimento alla classe padre associata. Ad esempio, nell'associazione tra Customer e Order, proprietà denominata Customer che fa riferimento al cliente associato per un ordine creato nella classe Order.|  
|**Proprietà partecipanti**|Visualizza le proprietà dell'associazione e fornisce un' **puntini di sospensione** pulsante (...) che si apre nuovamente il **Editor di associazione** nella finestra di dialogo.|  
|**univoco**|Specifica se le colonne esterne di destinazione presentano un vincolo di univocità.|  
  
### <a name="to-create-an-association-between-entity-classes"></a>Per creare un'associazione tra classi di entità  
  
1.  Fare doppio clic la classe di entità che rappresenta la classe padre nell'associazione, scegliere **Add**, quindi fare clic su **Association**.  
  
2.  Verificare che i valori corretti **classe padre** sia selezionato nel **Editor di associazione** nella finestra di dialogo.  
  
3.  Selezionare il **classe figlio** nella casella combinata.  
  
4.  Selezionare il **le proprietà di associazione** che mettono in relazione le classi. In genere, questa operazione consente di eseguire il mapping alla relazione di chiave esterna definita nel database. Ad esempio, nell'associazione Customers e Orders, il **le proprietà di associazione** rappresentano il valore CustomerID per ogni classe.  
  
5.  Fare clic su **OK** per creare l'associazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura: rappresentare le chiavi primarie](http://msdn.microsoft.com/library/63c65289-6539-42b2-8493-891c232018fa)

