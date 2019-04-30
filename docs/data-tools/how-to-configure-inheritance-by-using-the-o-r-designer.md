---
title: "Procedura: Configurare l'ereditarietà usando Object Relational Designer"
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 8927e6140792c12f42f1822afd0e715881384f1c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402810"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Procedura: Configurare l'ereditarietà usando Object Relational Designer
Il **Object Relational Designer** (**O/R Designer**) supporta il concetto di ereditarietà a tabella singola come viene spesso implementato nei sistemi relazionali. Nell'ereditarietà a tabella singola, è presente una singola tabella di database che contiene campi per le informazioni padre e le informazioni figlio. Insieme ai dati relazionali, una colonna discriminatore contiene il valore che determina la classe a cui appartiene un record.

Si consideri, ad esempio, un `Persons` tabella che contiene tutte le persone impiegate in una società. alcune delle quali sono dipendenti mentre altre sono manager. Il `Persons` tabella contiene una colonna denominata `EmployeeType` che presenta un valore pari a 1 per i responsabili e il valore 2 per i dipendenti, ovvero la colonna discriminatore. In questo scenario è possibile creare una sottoclasse di dipendenti e popolarla solo con i record che hanno un valore 2 in `EmployeeType`. È anche possibile rimuovere le colonne non appropriate da ognuna delle classi.

La creazione di un modello a oggetti che usa l'ereditarietà (e corrisponde ai dati relazionali) può generare una certa confusione. Nella procedura riportata di seguito vengono illustrati i passaggi necessari per la configurazione dell'ereditarietà con **Object Relational Designer**. Seguire passaggi generici senza fare riferimento a una tabella esistente e le colonne potrebbe essere difficile, pertanto viene fornita una procedura dettagliata che usa i dati. Per istruzioni dettagliate per la configurazione dell'ereditarietà utilizzando la **O/R Designer**, vedere [procedura dettagliata: Creazione di LINQ alle classi SQL tramite ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>Per creare classi di dati ereditate

1. Aprire il **O/R Designer** mediante l'aggiunta di un **classi LINQ to SQL** elemento a un progetto di Visual Basic o c# esistente.

2. Trascinare la tabella da usare come classe di base nel **O/R Designer**.

3. Trascinare una seconda copia della tabella nel **O/R Designer** e rinominarlo. In tal modo si otterrà la classe derivata o sottoclasse.

4. Fare clic su **Inheritance** nella scheda **Object Relational Designer** della **Casella degli strumenti** e quindi fare clic sulla sottoclasse (ovvero, la tabella rinominata) e connetterla alla classe di base.

    > [!NOTE]
    > Fare clic sull'elemento **Inheritance** nella **Casella degli strumenti** e rilasciare il pulsante del mouse, fare clic sulla seconda copia della classe creata nel passaggio 3 e quindi fare clic sulla prima classe creata nel passaggio 2. La freccia della linea di ereditarietà punta alla prima classe.

5. In ogni classe eliminare le proprietà dell'oggetto che non si desidera visualizzare e che non sono usate per le associazioni. Viene visualizzato un errore se si prova a eliminare le proprietà dell'oggetto usate per le associazioni: [La proprietà \<nome proprietà > non può essere eliminato perché è inclusa nell'associazione \<nome associazione >](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Poiché una classe derivata eredita le proprietà definite nella relativa classe di base, non è possibile definire le stesse colonne in ogni classe (le colonne vengono implementate come proprietà). Per consentire la creazione di colonne nella classe derivata, è possibile impostare il modificatore di ereditarietà sulla proprietà della classe di base. Per altre informazioni, vedere [nozioni fondamentali sull'ereditarietà (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6. Selezionare la linea di ereditarietà nel **O/R Designer**.

7. Nel **le proprietà** impostare nella finestra di **Discriminator Property** al nome della colonna che distingue i record nelle classi.

8. Impostare la proprietà **Derived Class Discriminator Value** sul valore nel database che designa il record come tipo ereditato. (Questo è il valore viene archiviato nella colonna discriminatore e usato per designare la classe ereditata).

9. Impostare la proprietà **Base Class Discriminator Value** sul valore che designa il record come tipo di base. (Questo è il valore viene archiviato nella colonna discriminatore e usato per designare la classe di base).

10. È anche possibile impostare eventualmente la proprietà **Inheritance Default** per definire un tipo in una gerarchia di ereditarietà usata durante il caricamento di righe che non corrispondono ad alcun codice di ereditarietà definito. In altre parole, se un record ha un valore nella relativa colonna discriminatore che non corrisponde al valore nel **Derived Class Discriminator Value** oppure **Base Class Discriminator Value** proprietà, il record Carica nel tipo designato come il **Inheritance Default**.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di LINQ alle classi di SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Nozioni fondamentali sull'ereditarietà (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Ereditarietà](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)