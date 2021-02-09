---
title: Configurare l'ereditarietà usando Object Relational Designer
description: Informazioni su come configurare l'ereditarietà usando il Object Relational Designer (O/R Designer), che supporta l'ereditarietà a tabella singola. Classi di dati ereditate create.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: e594af12-e777-434a-bc08-7dd2dac84cdc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: fee2c42e6ec84280f4090a8ae1dfea83a81ee369
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866827"
---
# <a name="how-to-configure-inheritance-by-using-the-or-designer"></a>Procedura: Configurare l'ereditarietà usando Object Relational Designer
Il **Object Relational Designer** (**O/R Designer**) supporta il concetto di ereditarietà a tabella singola poiché viene spesso implementato nei sistemi relazionali. Nell'ereditarietà a tabella singola, è presente una singola tabella di database che contiene campi per le informazioni padre e le informazioni figlio. Insieme ai dati relazionali, una colonna discriminatore contiene il valore che determina la classe a cui appartiene un record.

Si consideri, ad esempio, una `Persons` tabella che contiene tutti i dipendenti di una società. alcune delle quali sono dipendenti mentre altre sono manager. La `Persons` tabella contiene una colonna denominata `EmployeeType` con un valore pari a 1 per i Manager e un valore pari a 2 per i dipendenti. si tratta della colonna discriminatore. In questo scenario è possibile creare una sottoclasse di dipendenti e popolarla solo con i record che hanno un valore 2 in `EmployeeType`. È anche possibile rimuovere le colonne non appropriate da ognuna delle classi.

La creazione di un modello a oggetti che usa l'ereditarietà (e corrisponde ai dati relazionali) può generare una certa confusione. Nella procedura riportata di seguito vengono illustrati i passaggi necessari per la configurazione dell'ereditarietà con **Object Relational Designer**. I passaggi generici seguenti senza fare riferimento a una tabella e a colonne esistenti potrebbero essere difficili, quindi viene fornita una procedura dettagliata che usa i dati. Per istruzioni dettagliate per la configurazione dell'ereditarietà usando il **O/R Designer**, vedere [procedura dettagliata: creazione di LINQ to SQL classi con ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md).

## <a name="to-create-inherited-data-classes"></a>Per creare classi di dati ereditate

1. Aprire la **finestra di progettazione relazionale** oggetti aggiungendo un **LINQ to SQL elemento classi** a un progetto Visual Basic o C# esistente.

2. Trascinare la tabella che si vuole usare come classe di base in **Progettazione relazionale di O/R**.

3. Trascinare una seconda copia della tabella nella finestra di **progettazione di O/R** e rinominarla. In tal modo si otterrà la classe derivata o sottoclasse.

4. Fare clic su **Inheritance** nella scheda **Object Relational Designer** della **Casella degli strumenti** e quindi fare clic sulla sottoclasse (ovvero, la tabella rinominata) e connetterla alla classe di base.

    > [!NOTE]
    > Fare clic sull'elemento **Inheritance** nella **Casella degli strumenti** e rilasciare il pulsante del mouse, fare clic sulla seconda copia della classe creata nel passaggio 3 e quindi fare clic sulla prima classe creata nel passaggio 2. La freccia sulla linea di ereditarietà punta alla prima classe.

5. In ogni classe eliminare le proprietà dell'oggetto che non si desidera visualizzare e che non sono usate per le associazioni. Viene visualizzato un errore se si tenta di eliminare le proprietà dell'oggetto usate per [le associazioni: la proprietà \<property name> non può essere eliminata perché partecipa \<association name> all'associazione ](../data-tools/the-property-property-name-cannot-be-deleted-because-it-is-participating-in-the-association-association-name.md).

    > [!NOTE]
    > Poiché una classe derivata eredita le proprietà definite nella relativa classe di base, non è possibile definire le stesse colonne in ogni classe (Le colonne vengono implementate come proprietà). È possibile abilitare la creazione di colonne nella classe derivata impostando il modificatore di ereditarietà sulla proprietà nella classe di base. Per ulteriori informazioni, vedere [nozioni fondamentali sull'ereditarietà (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics).

6. Selezionare la linea di ereditarietà in **Progettazione relazionale di O/R**.

7. Nella finestra **Proprietà** impostare la **proprietà Discriminator** sul nome della colonna che distingue i record nelle classi.

8. Impostare la proprietà **Derived Class Discriminator Value** sul valore nel database che designa il record come tipo ereditato. Si tratta del valore archiviato nella colonna discriminatore e usato per designare la classe ereditata.

9. Impostare la proprietà **Base Class Discriminator Value** sul valore che designa il record come tipo di base. Si tratta del valore archiviato nella colonna discriminatore e usato per designare la classe base.

10. È anche possibile impostare eventualmente la proprietà **Inheritance Default** per definire un tipo in una gerarchia di ereditarietà usata durante il caricamento di righe che non corrispondono ad alcun codice di ereditarietà definito. In altre parole, se un record include un valore nella relativa colonna discriminatore che non corrisponde al valore nelle proprietà del valore **discriminatore della classe derivata** o del **valore del discriminatore della classe base** , il record viene caricato nel tipo designato come **valore predefinito di ereditarietà**.

## <a name="see-also"></a>Vedi anche

- [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (Object Relational Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Nozioni fondamentali sull'ereditarietà (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)
- [Ereditarietà](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)
