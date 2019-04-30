---
title: 'Procedura dettagliata: Creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (Object Relational Designer)'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7bb6562c0eb74f537efb25be031e9c9be46d64b6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63402685"
---
# <a name="walkthrough-create-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Procedura dettagliata: Creare classi LINQ to SQL tramite ereditarietà a tabella singola (O/R Designer)
Il [gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) supporta l'ereditarietà a tabella singola come viene in genere implementato nei sistemi relazionali. Questa procedura dettagliata espande i passaggi generici specificati nel [come: Configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) argomento e vengono forniti alcuni dati reali per illustrare l'uso dell'ereditarietà nel [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

 Durante questa procedura dettagliata, si eseguono le attività seguenti:

- Creazione di una tabella di database e aggiunta di dati ad essa.

- Creazione di un'applicazione Windows Form.

- Aggiunta di un file [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] a un progetto.

- Creazione di nuove classi di entità.

- Configurazione delle classi di entità per l'uso dell'ereditarietà.

- Esecuzione di una query sulla classe ereditata.

- Visualizzazione dei dati in un Windows Form.

## <a name="create-a-table-to-inherit-from"></a>Creazione di una tabella da cui ereditare
 Per visualizzarne il funzionamento dell'ereditarietà, creare un piccolo `Person` tabelle, usarlo come una classe di base e quindi creare un `Employee` oggetto che eredita da esso.

### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Per creare una tabella di base per l'illustrazione dell'ereditarietà

1. In **Esplora Server** oppure **Esplora Database**, fare doppio clic il **tabelle** nodo e fare clic su **Aggiungi nuova tabella**.

    > [!NOTE]
    > È possibile usare il database Northwind o qualsiasi altro database a cui sia possibile aggiungere una tabella.

2. In **Progettazione tabelle** aggiungere le colonne seguenti alla tabella:

    |Nome colonna|Tipo di dati|Ammetti Null|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**False**|
    |**Type**|**int**|**True**|
    |**FirstName**|**nvarchar(200)**|**False**|
    |**LastName**|**nvarchar(200)**|**False**|
    |**Manager**|**int**|**True**|

3. Impostare la colonna ID come chiave primaria.

4. Salvare la tabella e denominarla **Person**.

## <a name="add-data-to-the-table"></a>Aggiungere dati alla tabella
 Allo scopo di verificare che l'ereditarietà sia configurata correttamente, è necessario aggiungere alcuni dati alla tabella per ogni classe nell'ereditarietà a tabella singola.

### <a name="to-add-data-to-the-table"></a>Per aggiungere dati alla tabella

1. Aprire la tabella nella visualizzazione dati (Fare doppio clic sui **Person** nella tabella **Esplora Server** oppure **Esplora Database** e fare clic su **Mostra dati tabella**.)

2. Copiare i dati riportati di seguito nella tabella (È possibile copiarlo e incollarlo nella tabella selezionando l'intera riga nel **risultati** riquadro.)

    ||||||
    |-|-|-|-|-|
    |**ID**|**Type**|**FirstName**|**LastName**|**Manager**|
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

### <a name="to-create-the-new-windows-forms-application"></a>Per creare la nuova applicazione Windows Form

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual c#** oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Windows Desktop**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **InheritanceWalkthrough**, quindi scegliere **OK**.

     Il progetto **InheritanceWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Aggiunta di un file di classi LINQ to SQL al progetto

### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Per aggiungere un file LINQ to SQL al progetto

1. Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Fare clic sul modello **Classi LINQ to SQL** e quindi fare clic su **Aggiungi**.

     Il *dbml* file viene aggiunto al progetto e il **O/R Designer** apre.

## <a name="create-the-inheritance-by-using-the-or-designer"></a>Creare l'ereditarietà usando Object Relational Designer
 Configurare l'ereditarietà trascinando un oggetto **Inheritance** dalla **Casella degli strumenti** nell'area di progettazione.

### <a name="to-create-the-inheritance"></a>Per creare l'ereditarietà

1. Nella **Esplora Server** oppure **Esplora Database**, passare al **persona** tabella creata in precedenza.

2. Trascinare il **Person** tabella le **O/R Designer** nell'area di progettazione.

3. Trascinare una seconda **Person** tabella le **O/R Designer** e modificarne il nome in **dipendente**.

4. Eliminare la proprietà **Manager** dall'oggetto **Person**.

5. Eliminare le proprietà **Type**, **ID**, **FirstName** e **LastName** dall'oggetto **Employee** (in altre parole, eliminare tutte le proprietà ad eccezione di **Manager**).

6. Dalla scheda **Object Relational Designer** della **Casella degli strumenti**, creare un oggetto **Inheritance** tra gli oggetti **Person** ed **Employee**. Per eseguire questa operazione, fare clic sull'elemento **Inheritance** nella **Casella degli strumenti** e rilasciare il pulsante del mouse. Successivamente, fare clic il **dipendente** oggetto e quindi la **persona** dell'oggetto nel **O/R Designer**. La freccia della linea di ereditarietà fa quindi riferimento per la **persona** oggetto.

7. Fare clic sulla linea **Ereditarietà** nell'area di progettazione.

8. Impostare la proprietà **Discriminator Property** su **Type**.

9. Impostare la proprietà **Derived Class Discriminator Value** su **2**.

10. Impostare la proprietà **Base Class Discriminator Value** su **1**.

11. Impostare la proprietà **Inheritance Default** su **Person**.

12. Compilare il progetto.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Eseguire una query sulla classe ereditata e visualizzare i dati nel form
 È ora possibile aggiungere codice al form che esegue una query per una classe specifica nel modello a oggetti.

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
 Eseguire l'applicazione e verificare che i record visualizzati nella casella di riepilogo rappresentino tutti i dipendenti (record che presentano il valore 2 nella rispettiva colonna **Type**).

### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione

1. Premere **F5**.

2. Verificare che siano visualizzati solo i record che presentano il valore 2 nella rispettiva colonna **Type**.

3. Chiudere il form. Scegliere **Termina debug** dal menu **Debug**.

## <a name="see-also"></a>Vedere anche

- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura dettagliata: Creazione di LINQ alle classi di SQL (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Procedura: Generare il modello a oggetti in Visual Basic oC#](/dotnet/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp)