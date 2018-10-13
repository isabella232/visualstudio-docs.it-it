---
title: Ereditarietà (O-R Designer) delle classi di dati | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ae36d6aac3ea9a4ff4de73dea57207b6f03abc72
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49180518"
---
# <a name="data-class-inheritance-or-designer"></a>Ereditarietà della classe di dati (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Analogamente ad altri oggetti, le classi [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] possono usare l'ereditarietà ed essere derivate da altre classi. Nel codice è possibile specificare le relazioni di ereditarietà tra oggetti dichiarando che una classe eredita da un'altra. In un database le relazioni di ereditarietà vengono create in diversi modi. [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) supporta il concetto di ereditarietà a tabella singola in quanto viene spesso implementato nei sistemi relazionali.  
  
 Nell'ereditarietà a tabella singola è presente una singola tabella di database che contiene colonne per le classi base e derivate. Insieme ai dati relazionali, una colonna discriminante contiene il valore che determina la classe a cui appartiene uno specifico record. Ad esempio, si consideri una tabella Persons che contiene tutte le persone impiegate in una società, alcune delle quali sono dipendenti mentre altre sono manager. La tabella Persons contiene una colonna denominata Type, che presenta un valore 1 per i manager e un valore 2 per i dipendenti, e che costituisce la colonna discriminante. In questo scenario, è possibile creare una sottoclasse di dipendenti e popolare la classe solo con i record che hanno un valore 2 nella colonna Type.  
  
 Quando si configura l'ereditarietà nelle classi di entità utilizzando la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], trascinare la singola tabella che contiene i dati di ereditarietà nella finestra di progettazione due volte: una volta per ogni classe nella gerarchia di ereditarietà. Dopo aver aggiunto le tabelle nella finestra di progettazione, connetterle con un elemento di ereditarietà dal **Object Relational Designer** casella degli strumenti e quindi impostare le quattro proprietà di ereditarietà nel **proprietà** finestra.  
  
## <a name="inheritance-properties"></a>Proprietà di ereditarietà  
 Nella tabella seguente sono elencate le proprietà di ereditarietà e le rispettive descrizioni:  
  
|Proprietà|Descrizione|  
|--------------|-----------------|  
|Proprietà Discriminator|Proprietà (mappata alla colonna) che determina a quale classe appartiene il record corrente.|  
|Valore discriminante classe base|Valore (nella colonna definita come proprietà Discriminator) che determina che un record fa parte della classe base.|  
|Valore discriminante classe derivata|Valore (nella proprietà definita come proprietà Discriminator) che determina che un record fa parte della classe derivata.|  
|Valore predefinito di ereditarietà|La classe che deve essere popolata se il valore della proprietà viene specificata come la **proprietà Discriminator** corrisponde a uno il **Base Class Discriminator Value** o **classe derivata da Valore discriminante**.|  
  
 La creazione di un modello a oggetti che usa l'ereditarietà e corrisponde ai dati relazionali può generare una certa confusione. Questo argomento fornisce informazioni sui concetti di base e sulle proprietà singole richieste per la configurazione dell'ereditarietà. Negli argomenti seguenti viene fornita una spiegazione più chiara di come configurare l'ereditarietà con [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Procedura: Configurare l'ereditarietà usando O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Viene descritto come configurare le classi di entità che usano l'ereditarietà mediante [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].|  
|[Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Vengono fornite istruzioni dettagliate per la configurazione delle classi di entità che usano l'ereditarietà a tabella singola con [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].|  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [Introduzione](http://msdn.microsoft.com/library/db8a557a-fef8-4f4f-bb91-8cff7250ee25)

