---
title: LINQ to SQL classi con ereditarietà a tabella singola
description: In questa procedura dettagliata vengono create LINQ to SQL classi usando l'ereditarietà a tabella singola nel Visual Studio Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ff15209b60fb40200388eac2d9b1d90bb153fcfbba5c204f391c5bc7fbd70343
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346499"
---
# <a name="walkthrough-create-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Procedura dettagliata: Creare LINQ to SQL con ereditarietà a tabella singola (O/R Designer)
Gli [LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) supportano l'ereditarietà a tabella singola, in quanto viene in genere implementata nei sistemi relazionali. Questa procedura dettagliata illustra i passaggi generici descritti nell'argomento [Procedura:](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) Configurare l'ereditarietà tramite Progettazione oggetti e fornisce alcuni dati reali per illustrare l'uso dell'ereditarietà in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] .

Durante questa procedura dettagliata vengono eseguite le attività seguenti:

- Creazione di una tabella di database e aggiunta di dati ad essa.

- Creazione di un'applicazione Windows Form.

- Aggiunta di un file [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] a un progetto.

- Creazione di nuove classi di entità.

- Configurazione delle classi di entità per l'uso dell'ereditarietà.

- Esecuzione di una query sulla classe ereditata.

- Visualizzazione dei dati in un Windows Form.

## <a name="create-a-table-to-inherit-from"></a>Creazione di una tabella da cui ereditare
Per verificare il funzionamento dell'ereditarietà, creare una tabella di piccole dimensioni, usarla come classe di base e quindi creare un oggetto che `Person` `Employee` eredita da essa.

### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Per creare una tabella di base per l'illustrazione dell'ereditarietà

1. In **Esplora server** o **Esplora database** fare clic con il pulsante destro del mouse sul **nodo Tabelle** e scegliere Aggiungi nuova **tabella**.

    > [!NOTE]
    > È possibile usare il database Northwind o qualsiasi altro database a cui sia possibile aggiungere una tabella.

2. In **Progettazione tabelle** aggiungere le colonne seguenti alla tabella:

    |Nome colonna|Tipo di dati|Consenti valori NULL|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**False**|
    |**Tipo**|**int**|**True**|
    |**FirstName**|**nvarchar(200)**|**False**|
    |**LastName**|**nvarchar(200)**|**False**|
    |**Responsabile**|**int**|**True**|

3. Impostare la colonna ID come chiave primaria.

4. Salvare la tabella e denominarla **Person**.

## <a name="add-data-to-the-table"></a>Aggiungere dati alla tabella
Allo scopo di verificare che l'ereditarietà sia configurata correttamente, è necessario aggiungere alcuni dati alla tabella per ogni classe nell'ereditarietà a tabella singola.

### <a name="to-add-data-to-the-table"></a>Per aggiungere dati alla tabella

1. Aprire la tabella nella visualizzazione dati Fare clic con il pulsante destro **del mouse sulla** **tabella** Person Esplora server o **Esplora database** quindi scegliere Mostra **dati tabella.**

2. Copiare i dati riportati di seguito nella tabella È possibile copiarlo e incollarlo nella tabella selezionando l'intera riga nel **riquadro** Risultati.

    |**ID**|**Tipo**|**FirstName**|**LastName**|**Responsabile**|
    |-|-|-|-|-|
    |**1**|**1**|**Anne**|**Wallace**|**NULL**|
    |**2**|**1**|**Carlos**|**Grilo**|**NULL**|
    |**3**|**1**|**Yael**|**Peled**|**NULL**|
    |**4**|**2**|**Gatis**|**Ozolins**|**1**|
    |**5**|**2**|**Andreas**|**Hauser**|**1**|
    |**6**|**2**|**Tiffany**|**Phuvasate**|**1**|
    |**7**|**2**|**Alexey**|**Orekhov**|**2**|
    |**8**|**2**|**Michał**|**Poliszkiewicz**|**2**|
    |**9**|**2**|**Tai**|**Yee**|**2**|
    |**10**|**2**|**Fabricio**|**Noriega**|**3**|
    |**11**|**2**|**Mindy**|**Martin**|**3**|
    |**12**|**2**|**Ken**|**Kwok**|**3**|

## <a name="create-a-new-project"></a>Creare un nuovo progetto
Una volta creata la tabella, creare un nuovo progetto per illustrare la configurazione dell'ereditarietà.

### <a name="to-create-the-new-windows-forms-application"></a>Per creare la nuova applicazione Windows Forms

1. Nel menu **File** in Visual Studio selezionare **Nuovo** > **Progetto**.

2. Espandere **Visual C#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop**.

3. Nel riquadro centrale selezionare il tipo di progetto **Windows'app Forms.**

4. Assegnare al progetto **il nome InheritanceWalkthrough** e quindi scegliere **OK.**

     Il progetto **InheritanceWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Aggiunta di un file di classi LINQ to SQL al progetto

### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Per aggiungere un file LINQ to SQL al progetto

1. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Fare clic sul modello **Classi LINQ to SQL** e quindi fare clic su **Aggiungi**.

     Il file *con estensione dbml* viene aggiunto al progetto e viene aperto **O/R Designer.**

## <a name="create-the-inheritance-by-using-the-or-designer"></a>Creare l'ereditarietà usando Object Relational Designer
Configurare l'ereditarietà trascinando un oggetto **Inheritance** dalla **Casella degli strumenti** nell'area di progettazione.

### <a name="to-create-the-inheritance"></a>Per creare l'ereditarietà

1. In **Esplora server** o **Esplora database** passare alla tabella **Person** creata in precedenza.

2. Trascinare la **tabella Person** nell'area di progettazione **di O/R Designer.**

3. Trascinare una seconda **tabella Person** in **O/R Designer** e modificarne il nome in **Employee**.

4. Eliminare la proprietà **Manager** dall'oggetto **Person**.

5. Eliminare le proprietà **Type**, **ID**, **FirstName** e **LastName** dall'oggetto **Employee** (in altre parole, eliminare tutte le proprietà ad eccezione di **Manager**).

6. Dalla scheda **Object Relational Designer** della **Casella degli strumenti**, creare un oggetto **Inheritance** tra gli oggetti **Person** ed **Employee**. Per eseguire questa operazione, fare clic sull'elemento **Inheritance** nella **Casella degli strumenti** e rilasciare il pulsante del mouse. Fare quindi clic **sull'oggetto Employee** e quindi **sull'oggetto Person** in **O/R Designer.** La freccia sulla linea di ereditarietà punta quindi **all'oggetto Person.**

7. Fare clic sulla linea **Ereditarietà** nell'area di progettazione.

8. Impostare la proprietà **Discriminator Property** su **Type**.

9. Impostare la proprietà **Derived Class Discriminator Value** su **2**.

10. Impostare la proprietà **Base Class Discriminator Value** su **1**.

11. Impostare la proprietà **Inheritance Default** su **Person**.

12. Compilare il progetto.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Eseguire una query sulla classe ereditata e visualizzare i dati nel form
A questo punto si aggiunge codice al modulo che esegue query per una classe specifica nel modello a oggetti.

### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Per creare una query LINQ e visualizzare i risultati nel form

1. Trascinare un oggetto **ListBox** in **Form1**.

2. Fare doppio clic sul form per creare un gestore dell'evento `Form1_Load`.

3. Aggiungere il codice seguente al gestore eventi `Form1_Load` :

    ```vb
    Dim dc As New DataClasses1DataContext
    Dim results = From emp In dc.Persons _
        Where TypeOf emp Is Employee _
        Select emp

    For Each Emp As Employee In results
        ListBox1.Items.Add(Emp.LastName)
    Next
    ```

    ```csharp
    NorthwindDataContext dc = new DataClasses1DataContext();
    var results = from emp in dc.Persons
                  where emp is Employee
                  select emp;

    foreach(Employee Emp in results)
    {
        listBox1.Items.Add(Emp.LastName)
    }
    ```

## <a name="test-the-application"></a>Testare l'applicazione
Eseguire l'applicazione e verificare che i record visualizzati nella casella di riepilogo siano tutti dipendenti (record il cui valore è 2 nella **colonna Tipo).**

### <a name="to-test-the-application"></a>Per testare l'applicazione

1. Premere **F5**.

2. Verificare che nella colonna **Tipo** siano visualizzati solo i record con valore 2.

3. Chiudere il form. Scegliere **Arresta debug** dal menu **Debug**.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di classi LINQ to SQL (Object Relational Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procedura: Generare il modello a oggetti in Visual Basic o C #](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)
