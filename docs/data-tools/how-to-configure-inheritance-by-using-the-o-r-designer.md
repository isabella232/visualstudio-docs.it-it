---
title: Configurare l'ereditarietà usando Object Relational Designer
description: Informazioni su come configurare l'ereditarietà usando Object Relational Designer (O/R Designer), che supporta l'ereditarietà a tabella singola. Creazione di classi di dati ereditate.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: bfec5df4ed32178616f1086b2cd52216cb25c9c0
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631344"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Procedura: Configurare l'ereditarietà usando Object Relational Designer
La **Object Relational Designer** (**Progettazione relazionale** oggetti ) supporta il concetto di ereditarietà a tabella singola, in quanto viene spesso implementata nei sistemi relazionali. Nell'ereditarietà a tabella singola, è presente una singola tabella di database che contiene campi per le informazioni padre e le informazioni figlio. Insieme ai dati relazionali, una colonna discriminatore contiene il valore che determina la classe a cui appartiene un record.

Si consideri ad esempio `Persons` una tabella che contiene tutti gli dipendenti di una società. alcune delle quali sono dipendenti mentre altre sono manager. La tabella contiene una colonna denominata con valore 1 per i responsabili e un valore 2 per i dipendenti. Si tratta `Persons` `EmployeeType` della colonna discriminatore. In questo scenario è possibile creare una sottoclasse di dipendenti e popolarla solo con i record che hanno un valore 2 in `EmployeeType`. È anche possibile rimuovere le colonne non appropriate da ognuna delle classi.

La creazione di un modello a oggetti che usa l'ereditarietà (e corrisponde ai dati relazionali) può generare una certa confusione. Nella procedura riportata di seguito vengono illustrati i passaggi necessari per la configurazione dell'ereditarietà con **Object Relational Designer**. Seguire passaggi generici senza fare riferimento a una tabella e a colonne esistenti potrebbe essere difficile, quindi viene fornita una procedura dettagliata che usa i dati. Per istruzioni dettagliate per la configurazione dell'ereditarietà usando il **O/R Designer**, vedere [procedura dettagliata: creazione di LINQ to SQL classi con ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>Per creare classi di dati ereditate

1. Aprire **O/R Designer** aggiungendo un elemento **LINQ to SQL Classi** a un progetto Visual Basic o C#.

2. Trascinare la tabella che si vuole usare come classe di base in **O/R Designer.**

3. Trascinare una seconda copia della tabella in **O/R Designer** e rinominarla. In tal modo si otterrà la classe derivata o sottoclasse.

4. Fare clic su **Inheritance** nella scheda **Object Relational Designer** della **Casella degli strumenti** e quindi fare clic sulla sottoclasse (ovvero, la tabella rinominata) e connetterla alla classe di base.

    > [!NOTE]
    > Fare clic sull'elemento **Inheritance** nella **Casella degli strumenti** e rilasciare il pulsante del mouse, fare clic sulla seconda copia della classe creata nel passaggio 3 e quindi fare clic sulla prima classe creata nel passaggio 2. La freccia sulla linea di ereditarietà punta alla prima classe.

5. In ogni classe eliminare le proprietà dell'oggetto che non si desidera visualizzare e che non sono usate per le associazioni. Se si tenta di eliminare le proprietà dell'oggetto usate per le associazioni, viene visualizzato un errore: La proprietà non può essere eliminata perché partecipa [ \<property name> all'associazione \<association name> ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Poiché una classe derivata eredita le proprietà definite nella relativa classe di base, non è possibile definire le stesse colonne in ogni classe Le colonne vengono implementate come proprietà. È possibile abilitare la creazione di colonne nella classe derivata impostando il modificatore di ereditarietà sulla proprietà nella classe di base. Per altre informazioni, vedere [Nozioni di base sull'ereditarietà (Visual Basic).](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)

6. Selezionare la linea di ereditarietà in **O/R Designer.**

7. Nella finestra **Proprietà** impostare la proprietà **Discriminator sul** nome della colonna che distingue i record nelle classi.

8. Impostare la proprietà **Derived Class Discriminator Value** sul valore nel database che designa il record come tipo ereditato. Si tratta del valore archiviato nella colonna discriminatore e usato per designare la classe ereditata.

9. Impostare la proprietà **Base Class Discriminator Value** sul valore che designa il record come tipo di base. Si tratta del valore archiviato nella colonna discriminatore e usato per designare la classe di base.

10. È anche possibile impostare eventualmente la proprietà **Inheritance Default** per definire un tipo in una gerarchia di ereditarietà usata durante il caricamento di righe che non corrispondono ad alcun codice di ereditarietà definito. In altre parole, se un record ha un valore nella colonna discriminatore che non corrisponde al valore nelle proprietà **Derived Class Discriminator Value** o Base Class Discriminator **Value,** il record viene caricato nel tipo designato come Valore predefinito di ereditarietà. 

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Nozioni di base sull'ereditarietà (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Ereditarietà](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
