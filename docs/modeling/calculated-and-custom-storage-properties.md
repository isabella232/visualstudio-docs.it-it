---
title: Proprietà di archiviazione calcolate e personalizzate
description: Informazioni su come tutte le proprietà di dominio in un linguaggio specifico di dominio (DSL) possono essere visualizzate all'utente nel diagramma e in Esplora linguaggi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain properties
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f98dca6759b9e4a77e71139b6d9ec9b394d99b04
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385422"
---
# <a name="calculated-and-custom-storage-properties"></a>Proprietà di archiviazione calcolate e personalizzate
Tutte le proprietà di dominio in un linguaggio specifico di dominio (DSL) possono essere visualizzate all'utente nel diagramma e in Esplora linguaggi ed è possibile accedervi tramite codice programma. Tuttavia, le proprietà differiscono per il modo in cui vengono archiviati i relativi valori.

## <a name="kinds-of-domain-properties"></a>Tipi di proprietà di dominio
 Nella definizione DSL è possibile impostare la **proprietà Tipo** di un dominio, come indicato nella tabella seguente:

|Tipo di proprietà di dominio|Descrizione|
|-|-|
|**Standard** (impostazione predefinita)|Proprietà di dominio salvata nell'archivio *e* serializzata in un file.|
|**Calcolate**|Proprietà di dominio di sola lettura che non viene salvata nell'archivio, ma viene calcolata da altri valori.<br /><br /> Ad esempio, `Person.Age` può essere calcolato da `Person.BirthDate` .<br /><br /> È necessario fornire il codice che esegue il calcolo. In genere, il valore viene calcolato da altre proprietà di dominio. Tuttavia, è anche possibile usare risorse esterne.|
|**Archiviazione personalizzata**|Proprietà di dominio che non viene salvata direttamente nell'archivio, ma che può essere sia get che set.<br /><br /> È necessario fornire i metodi che ottengono e impostano il valore.<br /><br /> Ad esempio, `Person.FullAddress` può essere archiviato in , e `Person.StreetAddress` `Person.City` `Person.PostalCode` .<br /><br /> È anche possibile accedere a risorse esterne, ad esempio per ottenere e impostare valori da un database.<br /><br /> Il codice non deve impostare valori nell'archivio quando `Store.InUndoRedoOrRollback` è true. Vedere [Transazioni e setter personalizzati.](#setters)|

## <a name="providing-the-code-for-a-calculated-or-custom-storage-property"></a>Specifica del codice per una proprietà di archiviazione calcolata o personalizzata
 Se si imposta la proprietà Kind of a domain su Calculated o Custom Storage, è necessario fornire metodi di accesso. Quando si compila la soluzione, viene visualizzato un report degli errori che segnala ciò che è necessario.

#### <a name="to-define-a-calculated-or-custom-storage-property"></a>Per definire una proprietà di archiviazione calcolata o personalizzata

1. In DslDefinition.dsl selezionare la proprietà domain nel diagramma o in **DSL Explorer.**

2. Nella finestra **Proprietà** impostare il campo **Kind** su **Calculated** o **Custom Storage.**

     Assicurarsi di aver impostato anche il **tipo** su quello desiderato.

3. Fare **clic su Trasforma tutti i** modelli sulla barra degli strumenti **Esplora soluzioni**.

4. Nel menu **Compila** scegliere **Compila soluzione**.

     Viene visualizzato il messaggio di errore seguente: "*YourClass* does not contain a definition for Get *YourProperty*".

5. Fare doppio clic sul messaggio di errore.

     Si apre Dsl\GeneratedCode\DomainClasses.cs o DomainRelationships.cs. Sopra la chiamata al metodo evidenziata, un commento richiede di fornire un'implementazione per Get *YourProperty*().

    > [!NOTE]
    > Questo file viene generato da DslDefinition.dsl. Se si modifica questo file, le modifiche andranno perse la volta successiva che si fa clic **su Trasforma tutti i modelli**. Aggiungere invece il metodo richiesto in un file separato.

6. Creare o aprire un file di classe in una cartella separata, ad esempio CustomCode \\ *YourDomainClass*.cs.

     Assicurarsi che lo spazio dei nomi sia lo stesso del codice generato.

7. Nel file di classe scrivere un'implementazione parziale della classe di dominio. Nella classe scrivere una definizione per il metodo `Get` mancante simile all'esempio seguente:

    ```
    namespace Company.FamilyTree
    {  public partial class Person
       {  int GetAgeValue()
          { return System.DateTime.Today.Year - this.BirthYear; }
    }  }
    ```

8. Se si imposta **Kind** **su Custom Storage**, sarà necessario fornire anche un metodo `Set` . Ad esempio:

    ```
    void SetAgeValue(int value)
    { if (!Store.InUndoRedoOrRollback)
        this.BirthYear =
            System.DateTime.Today.Year - value; }
    ```

     Il codice non deve impostare valori nell'archivio quando `Store.InUndoRedoOrRollback` è true. Vedere [Transazioni e setter personalizzati.](#setters)

9. Compilare ed eseguire la soluzione.

10. Testare la proprietà . Assicurarsi di provare Annulla **e** **Ripeti**.

## <a name="transactions-and-custom-setters"></a><a name="setters"></a> Transazioni e setter personalizzati
 Nel metodo Set della proprietà di archiviazione personalizzata non è necessario aprire una transazione, perché il metodo viene in genere chiamato all'interno di una transazione attiva.

 Tuttavia, il metodo Set può essere chiamato anche se l'utente richiama Undo o Redo o se viene eseguito il rollback di una transazione. Quando <xref:Microsoft.VisualStudio.Modeling.Store.InUndoRedoOrRollback%2A> è true, il metodo Set dovrebbe comportarsi come segue:

- Non deve apportare modifiche nell'archivio, ad esempio l'assegnazione di valori ad altre proprietà di dominio. Il gestore di annullamento ne imposta i valori.

- Tuttavia, deve aggiornare tutte le risorse esterne, ad esempio il contenuto del database o del file, o gli oggetti all'esterno dell'archivio. In questo modo si avrà la certezza che siano mantenuti sincronizzati con i valori nell'archivio.

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

 Per altre informazioni sulle transazioni, vedere [Esplorazione e aggiornamento di un modello nel codice programma.](../modeling/navigating-and-updating-a-model-in-program-code.md)

## <a name="see-also"></a>Vedi anche

- [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Proprietà delle proprietà di dominio](../modeling/properties-of-domain-properties.md)
- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
