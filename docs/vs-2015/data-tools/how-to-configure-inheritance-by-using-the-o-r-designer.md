---
title: "Procedura: configurare l'ereditarietà tramite O-R Designer | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ccfbd40fd9fd62921ff6f0661f87dca2995ae8fa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529733"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Procedura: configurare l'ereditarietà tramite O/R Designer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [procedura: configurare l'ereditarietà tramite O-R Designer](https://docs.microsoft.com/visualstudio/data-tools/how-to-configure-inheritance-by-using-the-o-r-designer).  
  
  
[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) supporta il concetto di ereditarietà a tabella singola in quanto viene spesso implementato nei sistemi relazionali. Nell'ereditarietà a tabella singola, è presente una singola tabella di database che contiene campi per le informazioni padre e le informazioni figlio. Insieme ai dati relazionali, una colonna discriminatore contiene il valore che determina la classe a cui appartiene un record.  
  
 Ad esempio, si consideri una tabella Persons che contiene tutte le persone impiegate in una società, alcune delle quali sono dipendenti mentre altre sono manager. La tabella Persons contiene una colonna denominata `EmployeeType` con un valore 1 per i manager e un valore 2 per i dipendenti e che costituisce la colonna discriminatore. In questo scenario è possibile creare una sottoclasse di dipendenti e popolarla solo con i record che hanno un valore 2 in `EmployeeType`. È anche possibile rimuovere le colonne non appropriate da ognuna delle classi.  
  
 La creazione di un modello a oggetti che usa l'ereditarietà (e corrisponde ai dati relazionali) può generare una certa confusione. Nella procedura riportata di seguito vengono illustrati i passaggi necessari per la configurazione dell'ereditarietà con Progettazione relazionale oggetti. Poiché potrebbe essere difficile seguire passaggi generici senza fare riferimento a una tabella e a colonne esistenti, viene fornita una procedura dettagliata in cui vengono usati dati effettivi. Per istruzioni dettagliate per la configurazione dell'ereditarietà utilizzando la [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], vedere [questa procedura dettagliata: creazione di classi LINQ to SQL da tramite ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).  
  
### <a name="to-create-inherited-data-classes"></a>Per creare classi di dati ereditate  
  
1.  Aprire il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] mediante l'aggiunta di un **classi LINQ to SQL** elemento a un progetto di Visual Basic o c# esistente.  
  
2.  Trascinare la tabella che si desidera usare come classe di base in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
3.  Trascinare una seconda copia della tabella nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] e rinominarlo. In tal modo si otterrà la classe derivata o sottoclasse.  
  
4.  Fare clic su **ereditarietà** nel **Object Relational Designer** scheda della finestra di **della casella degli strumenti**e quindi selezionare la sottoclasse (la tabella rinominata) e connetterla alla classe di base.  
  
    > [!NOTE]
    >  Fare clic sui **ereditarietà** degli elementi nella **della casella degli strumenti** e rilasciare il pulsante del mouse, scegliere la seconda copia della classe creata nel passaggio 3, quindi la prima classe creata nel passaggio 2. La freccia della linea di ereditarietà punterà alla prima classe.  
  
5.  In ogni classe eliminare le proprietà dell'oggetto che non si desidera visualizzare e che non sono usate per le associazioni. Si riceverà un errore se si prova a eliminare le proprietà dell'oggetto usate per le associazioni: [la proprietà \<nome proprietà > non può essere eliminato perché è inclusa nell'associazione \<nome associazione >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).  
  
    > [!NOTE]
    >  Poiché una classe derivata eredita le proprietà definite nella relativa classe di base, non è possibile definire le stesse colonne in ogni classe (le colonne vengono implementate come proprietà). Per consentire la creazione di colonne nella classe derivata, è possibile impostare il modificatore di ereditarietà sulla proprietà della classe di base. Per altre informazioni, vedere [NOT IN BUILD: override di proprietà e metodi](http://msdn.microsoft.com/en-us/2167e8f5-1225-4b13-9ebd-02591ba90213).  
  
6.  Selezionare la linea di ereditarietà in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
7.  Nel **le proprietà** impostare nella finestra di **Discriminator Property** al nome della colonna che viene usato per distinguere i record nelle classi.  
  
8.  Impostare il **Derived Class Discriminator Value** proprietà sul valore nel database che designa il record come tipo ereditato. (si tratta del valore archiviato nella colonna discriminatore e usato per designare la classe ereditata).  
  
9. Impostare il **Base Class Discriminator Value** proprietà sul valore che designa il record come tipo di base. (si tratta del valore archiviato nella colonna discriminatore e usato per designare la classe di base).  
  
10. Facoltativamente, è possibile impostare anche il **Inheritance Default** proprietà per definire un tipo in una gerarchia di ereditarietà utilizzato durante il caricamento di righe che non corrispondono ad alcun codice di ereditarietà definito. In altre parole, se un record ha un valore nella relativa colonna discriminatore che non corrisponde al valore nel **Derived Class Discriminator Value** oppure **Base Class Discriminator Value** proprietà, il record verrà caricato nel tipo designato come il **Inheritance Default**.  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [PAVE quali sono le novità per lo sviluppo di applicazioni dati in Visual Studio 2012](http://msdn.microsoft.com/en-us/3d50d68f-5f44-4915-842f-6d42fce793f1)   
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)   
 [NOT IN BUILD: Ereditarietà in Visual Basic](http://msdn.microsoft.com/en-us/e5e6e240-ed31-4657-820c-079b7c79313c)   
 [Ereditarietà](http://msdn.microsoft.com/library/81d64ee4-50f9-4d6c-a8dc-257c348d2eea)

