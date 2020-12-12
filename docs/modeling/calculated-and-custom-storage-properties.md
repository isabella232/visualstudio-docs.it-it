---
title: Proprietà di archiviazione calcolate e personalizzate
description: Informazioni sul modo in cui tutte le proprietà del dominio in un linguaggio specifico di dominio (DSL) possono essere visualizzate all'utente nel diagramma e in Esplora linguaggio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2c50d205745917b3af7de638a17921f4bcdca509
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363549"
---
# <a name="calculated-and-custom-storage-properties"></a>Proprietà di archiviazione calcolate e personalizzate
Tutte le proprietà del dominio in un linguaggio specifico di dominio (DSL) possono essere visualizzate all'utente nel diagramma e in Esplora linguaggio ed è possibile accedervi tramite codice programma. Tuttavia, le proprietà differiscono in base alla modalità di archiviazione dei relativi valori.

## <a name="kinds-of-domain-properties"></a>Tipi di proprietà del dominio
 Nella definizione DSL è possibile impostare il **tipo** di una proprietà di dominio, come elencato nella tabella seguente:

|Tipo di proprietà del dominio|Description|
|-|-|
|**Standard** (impostazione predefinita)|Proprietà di dominio salvata nell' *Archivio* e serializzata in un file.|
|**Calcolate**|Proprietà di dominio di sola lettura che non viene salvata nell'archivio, ma viene calcolata da altri valori.<br /><br /> Ad esempio, `Person.Age` può essere calcolato da `Person.BirthDate` .<br /><br /> È necessario fornire il codice per eseguire il calcolo. In genere, il valore viene calcolato dalle altre proprietà del dominio. Tuttavia, è anche possibile usare le risorse esterne.|
|**Archiviazione personalizzata**|Proprietà di dominio che non viene salvata direttamente nell'archivio, ma che può essere Get e set.<br /><br /> È necessario fornire i metodi che ottengono e impostano il valore.<br /><br /> Ad esempio, `Person.FullAddress` può essere archiviato in `Person.StreetAddress` , `Person.City` e `Person.PostalCode` .<br /><br /> È anche possibile accedere alle risorse esterne, ad esempio per ottenere e impostare i valori da un database.<br /><br /> Il codice non deve impostare i valori nell'archivio quando `Store.InUndoRedoOrRollback` è true. Vedere [transazioni e setter personalizzati](#setters).|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Fornire il codice per una proprietà di archiviazione calcolata o personalizzata
 Se si imposta il tipo di una proprietà di dominio su un archivio calcolato o personalizzato, è necessario fornire i metodi di accesso. Quando si compila la soluzione, una segnalazione errori indica gli elementi necessari.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Per definire una proprietà di archiviazione calcolata o personalizzata

1. In DslDefinition. DSL selezionare la proprietà di dominio nel diagramma o in **DSL Explorer**.

2. Nella finestra **Proprietà** impostare il campo **tipo** su archiviazione **calcolata** o **personalizzata**.

     Assicurarsi di aver impostato anche il **tipo** su quello desiderato.

3. Fare clic su **trasforma tutti i modelli** nella barra degli strumenti di **Esplora soluzioni**.

4. Nel menu **Compila** scegliere **Compila soluzione**.

     Viene visualizzato il messaggio di errore seguente: "*ClasseUtente* non contiene una definizione per Get *Proprietà*".

5. Fare doppio clic sul messaggio di errore.

     Viene aperto Dsl\GeneratedCode\DomainClasses.cs o DomainRelationships.cs. Al di sopra della chiamata al metodo evidenziato, un commento richiede di fornire un'implementazione per Get *Proprietà*().

    > [!NOTE]
    > Questo file viene generato da DslDefinition. DSL. Se si modifica questo file, le modifiche andranno perse la volta successiva che si fa clic su **trasforma tutti i modelli**. Aggiungere invece il metodo richiesto in un file separato.

6. Creare o aprire un file di classe in una cartella separata, ad esempio CustomCoded \\ *YourDomainClass*. cs.

     Verificare che lo spazio dei nomi corrisponda a quello del codice generato.

7. Nel file di classe scrivere un'implementazione parziale della classe di dominio. Nella classe scrivere una definizione per il metodo mancante simile `Get` all'esempio seguente:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. Se si imposta **Kind** sull' **archiviazione personalizzata**, sarà necessario fornire anche un `Set` metodo. Ad esempio:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Il codice non deve impostare i valori nell'archivio quando `Store.InUndoRedoOrRollback` è true. Vedere [transazioni e setter personalizzati](#setters).

9. Compilare ed eseguire la soluzione.

10. Testare la proprietà. Assicurarsi di provare a **annullare** e **ripetere** l'operazione.

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> Transazioni e setter personalizzati
 Nel metodo set della proprietà di archiviazione personalizzata non è necessario aprire una transazione, perché il metodo viene in genere chiamato all'interno di una transazione attiva.

 Tuttavia, il metodo set può essere chiamato anche se l'utente richiama l'annullamento o la ripetizione o se viene eseguito il rollback di una transazione. Quando <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> è true, il metodo set dovrebbe comportarsi come segue:

- Non dovrebbe apportare modifiche nell'archivio, ad esempio l'assegnazione di valori ad altre proprietà del dominio. I valori vengono impostati dal gestore di annullamento.

- Tuttavia, deve aggiornare tutte le risorse esterne, ad esempio il contenuto di un database o di un file, o oggetti all'esterno dell'archivio. In questo modo verranno mantenuti sincronizzati con i valori nell'archivio.

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

 Per ulteriori informazioni sulle transazioni, vedere [esplorazione e aggiornamento di un modello nel codice programma](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Vedi anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Proprietà delle proprietà di dominio](../modeling/properties-of-domain-properties.md)
- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
