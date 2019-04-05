---
title: Le proprietà di archiviazione calcolate e personalizzate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
ms.assetid: 42b785f9-2b0f-4f13-a6b4-246e5e0d477a
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e934d071a8b26db29f2b9450939fc895efa1e5d4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964828"
---
# <a name="calculated-and-custom-storage-properties"></a>Proprietà di archiviazione calcolate e personalizzate
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tutte le proprietà di dominio in un linguaggio specifico di dominio (DSL) possono essere visualizzate all'utente nel diagramma e nella finestra di esplorazione del linguaggio e sono accessibili da codice programma. Tuttavia, le proprietà differiscono in modo che i relativi valori vengono archiviati.  
  
## <a name="kinds-of-domain-properties"></a>Tipi di proprietà di dominio  
 Nella definizione DSL, è possibile impostare il **tipo** della proprietà del dominio, come indicato nella tabella seguente:  
  
|Tipo di proprietà del dominio|Descrizione|  
|--------------------------|-----------------|  
|**Standard** (predefinito)|Proprietà di dominio che viene salvata nel *archiviare* e serializzato nel file.|  
|**Calcolata**|Proprietà di dominio di sola lettura che non viene salvata nell'archivio, ma viene calcolata da altri valori.<br /><br /> Ad esempio, `Person.Age` può essere calcolata dalla `Person.BirthDate`.<br /><br /> È necessario fornire il codice che esegue il calcolo. In genere, si calcola il valore da altre proprietà di dominio. Tuttavia, è possibile utilizzare anche le risorse esterne.|  
|**Archiviazione personalizzata**|Proprietà di dominio che non viene salvata direttamente nell'archivio, ma può essere sia get che set.<br /><br /> È necessario fornire i metodi che ottenere e impostare il valore.<br /><br /> Ad esempio, `Person.FullAddress` possono essere archiviati in `Person.StreetAddress`, `Person.City`, e `Person.PostalCode`.<br /><br /> È anche possibile accedere alle risorse esterne, ad esempio per ottenere e impostare i valori da un database.<br /><br /> Il codice non necessario impostare i valori nell'archivio quando `Store.InUndoRedoOrRollback` è true. Visualizzare [transazioni e setter personalizzato](#setters).|  
  
## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Fornire il codice per una proprietà calcolata o personalizzati nell'archivio  
 Se si imposta il tipo della proprietà del dominio su Calculated o archiviazione personalizzata, è necessario fornire i metodi di accesso. Quando si compila la soluzione, un report degli errori indicherà quali sono i requisiti.  
  
#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Per definire un valore calcolato o una proprietà di archiviazione personalizzati  
  
1.  In Dsldefinition, selezionare la proprietà di dominio nel diagramma o nel **DSL Explorer**.  
  
2.  Nel **delle proprietà** impostare nella finestra di **tipo** campo **Calculated** o **archiviazione personalizzata**.  
  
     Assicurarsi di aver impostato anche relativi **tipo** nel modo desiderato.  
  
3.  Fare clic su **Trasforma tutti i modelli** nella barra degli strumenti **Esplora soluzioni**.  
  
4.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
     Viene visualizzato il messaggio seguente: "*ClasseUtente* non contiene una definizione per Get*proprietà*."  
  
5.  Fare doppio clic sul messaggio di errore.  
  
     Dsl\generatedcode\domainclasses.cs. o DomainRelationships.cs viene aperto. Sopra la chiamata al metodo evidenziato un commento viene richiesto di fornire un'implementazione di Get*proprietà*().  
  
    > [!NOTE]
    >  Questo file viene generato da Dsldefinition. Se si modifica questo file, le modifiche andranno perse la volta successiva che si fa clic su **Trasforma tutti i modelli**. Al contrario, aggiungere il metodo richiesto in un file separato.  
  
6.  Creare o aprire un file di classe in una cartella distinta, ad esempio Customcoded\\*YourDomainClass*. cs.  
  
     Assicurarsi che lo spazio dei nomi è uguale a quello del codice generato.  
  
7.  Nel file di classe, scrivere un'implementazione parziale della classe di dominio. Nella classe, scrivere una definizione di parametro mancante `Get` metodo simile al seguente:  
  
    ```  
    namespace Company.FamilyTree  
    {  public partial class Person  
       {  int GetAgeValue()  
          { return System.DateTime.Today.Year - this.BirthYear; }  
    }  }  
    ```  
  
8.  Se si imposta **genere** al **archiviazione personalizzata**, sarà inoltre necessario fornire un `Set` (metodo). Ad esempio:  
  
    ```  
    void SetAgeValue(int value)  
    { if (!Store.InUndoRedoOrRollback)  
        this.BirthYear =   
            System.DateTime.Today.Year - value; }  
    ```  
  
     Il codice non necessario impostare i valori nell'archivio quando `Store.InUndoRedoOrRollback` è true. Visualizzare [transazioni e setter personalizzato](#setters).  
  
9. Compilare ed eseguire la soluzione.  
  
10. Testare la proprietà. Assicurarsi che provi **Undo** e **Ripeti**.  
  
##  <a name="setters"></a> Le transazioni e setter personalizzato  
 Nel metodo Set di proprietà di archiviazione personalizzati, non è necessario aprire una transazione, poiché il metodo viene chiamato in genere all'interno di una transazione attiva.  
  
 Il metodo Set, tuttavia, potrebbe essere chiamato anche se l'utente richiama l'annullamento o ripristino o se una transazione è in fase di rollback. Quando si <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> è true, il metodo Set deve comportarsi come indicato di seguito:  
  
- Consigliabile non apportare modifiche nell'archivio, ad esempio l'assegnazione di valori di altre proprietà di dominio. La gestione degli annullamenti imposterà i relativi valori.  
  
- Tuttavia, è necessario aggiornare eventuali risorse esterne, ad esempio database di contenuto del file o oggetti all'esterno dell'archivio. Questo garantirà che si trovano in synchronism con i valori nell'archivio.  
  
  Ad esempio:  
  
```  
void SetAgeValue(int value)  
{   
  // If we are in Undo, no changes to Store objects:  
  if (!this.Store.InUndoRedoOrRollback)  
  {   
    this.BirthYear = System.DateTime.Today.Year - value;   
  }  
  // But always update external objects:  
  System.IO.File.WriteAllText(AgeFile, value);  
}  
```  
  
 Per altre informazioni sulle transazioni, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Proprietà delle proprietà di dominio](../modeling/properties-of-domain-properties.md)   
 [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
