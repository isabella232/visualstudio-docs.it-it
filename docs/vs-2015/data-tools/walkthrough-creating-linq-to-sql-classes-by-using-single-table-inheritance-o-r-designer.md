---
title: "Procedura dettagliata: creazione di classi di LINQ to SQL usando l'ereditarietà a tabella singola (O-R Designer) | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 63bc6328-e0df-4655-9ce3-5ff74dbf69a4
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9cf95bd2095d9713d498ddccf68fd1e81e1b1e64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85535707"
---
# <a name="walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-or-designer"></a>Procedura dettagliata: creazione di classi LINQ to SQL tramite ereditarietà a una sola tabella (O/R Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gli [strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) supportano l'ereditarietà a tabella singola poiché viene in genere implementata nei sistemi relazionali. Questa procedura dettagliata illustra i passaggi generici forniti nell'argomento [How to: Configure ereditarietà by using the o/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) e fornisce alcuni dati reali per illustrare l'uso dell'ereditarietà in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 In particolare, verranno illustrate le attività seguenti:

- Creazione di una tabella di database e aggiunta di dati ad essa.

- Creazione di un'applicazione Windows Form.

- Aggiunta di un file [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] a un progetto.

- Creazione di nuove classi di entità.

- Configurazione delle classi di entità per l'uso dell'ereditarietà.

- Esecuzione di una query sulla classe ereditata.

- Visualizzazione dei dati in un Windows Form.

## <a name="create-a-table-to-inherit-from"></a>Creazione di una tabella da cui ereditare
 Per verificare il funzionamento dell'ereditarietà, verrà creata una piccola tabella Person, usata come classe di base, e verrà creato quindi un oggetto Employee che eredita dalla tabella.

#### <a name="to-create-a-base-table-to-demonstrate-inheritance"></a>Per creare una tabella di base per l'illustrazione dell'ereditarietà

1. In **Esplora server** / **Esplora database**fare clic con il pulsante destro del mouse sul nodo **tabelle** e scegliere **Aggiungi nuova tabella**.

    > [!NOTE]
    > È possibile usare il database Northwind o qualsiasi altro database a cui sia possibile aggiungere una tabella.

2. In Progettazione tabelle aggiungere le seguenti colonne alla tabella:

    |Nome colonna|Tipo di dati|Consenti valori NULL|
    |-----------------|---------------|-----------------|
    |**ID**|**int**|**False**|
    |**Tipo**|**int**|**True**|
    |**FirstName**|**nvarchar(200)**|**False**|
    |**LastName**|**nvarchar(200)**|**False**|
    |**Responsabile**|**int**|**True**|

3. Impostare la colonna ID come chiave primaria.

4. Salvare la tabella e denominarla **Person**.

## <a name="add-data-to-the-table"></a>Aggiunta di dati alla tabella
 Allo scopo di verificare che l'ereditarietà sia configurata correttamente, è necessario aggiungere alcuni dati alla tabella per ogni classe nell'ereditarietà a tabella singola.

#### <a name="to-add-data-to-the-table"></a>Per aggiungere dati alla tabella

1. Aprire la tabella nella visualizzazione dati (Fare clic con il pulsante destro del mouse sulla tabella **Person** in **Esplora server** / **Esplora database** e fare clic su **Mostra dati tabella**.)

2. Copiare i dati riportati di seguito nella tabella È possibile copiarlo e incollarlo nella tabella selezionando l'intera riga nel riquadro risultati.

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

## <a name="create-a-new-project"></a>Creazione di un nuovo progetto
 Una volta creata la tabella, creare un nuovo progetto per illustrare la configurazione dell'ereditarietà.

#### <a name="to-create-the-new-windows-application"></a>Per creare la nuova applicazione Windows

1. Creare un nuovo progetto dal menu **file** .

2. Denominare il progetto **InheritanceWalkthrough**.

    > [!NOTE]
    > [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] è supportato nei progetti Visual Basic e C#. Creare il nuovo progetto in uno di questi linguaggi

3. Fare clic sul modello **applicazione Windows Forms** , quindi fare clic su **OK**. Per ulteriori informazioni, vedere [applicazioni client](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

4. Il progetto InheritanceWalkthrough viene creato e aggiunto a **Esplora soluzioni**.

## <a name="add-a-linq-to-sql-classes-file-to-the-project"></a>Aggiunta di un file di classi LINQ to SQL al progetto

#### <a name="to-add-a-linq-to-sql-file-to-the-project"></a>Per aggiungere un file LINQ to SQL al progetto

1. Dal menu **Progetto** fare clic su **Aggiungi nuovo elemento**.

2. Fare clic sul modello **Classi LINQ to SQL** e quindi fare clic su **Aggiungi**.

     Il file .dbml viene aggiunto al progetto e viene aperto [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

## <a name="create-the-inheritance-by-using-the-or-designer"></a>Creazione dell'ereditarietà usando Progettazione relazionale oggetti
 Configurare l'ereditarietà trascinando un oggetto **Inheritance** dalla **Casella degli strumenti** nell'area di progettazione.

#### <a name="to-create-the-inheritance"></a>Per creare l'ereditarietà

1. In **Esplora server** / **Esplora database**passare alla tabella **Person** creata in precedenza.

2. Trascinare la tabella **Person** nell' [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] area di progettazione.

3. Trascinare una seconda tabella **Person** [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] in e modificarne il nome in **Employee**.

4. Eliminare la proprietà **Manager** dall'oggetto **Person**.

5. Eliminare le proprietà **Type**, **ID**, **FirstName** e **LastName** dall'oggetto **Employee** (in altre parole, eliminare tutte le proprietà ad eccezione di **Manager**).

6. Dalla scheda **Object Relational Designer** della **Casella degli strumenti**, creare un oggetto **Inheritance** tra gli oggetti **Person** ed **Employee**. Per eseguire questa operazione, fare clic sull'elemento **Inheritance** nella **Casella degli strumenti** e rilasciare il pulsante del mouse. Quindi, fare clic sull'oggetto **Employee** e quindi sull'oggetto **Person** in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . La freccia sulla linea di ereditarietà punterà all'oggetto **Person** .

7. Fare clic sulla linea **Ereditarietà** nell'area di progettazione.

8. Impostare la proprietà **Discriminator Property** su **Type**.

9. Impostare la proprietà **Derived Class Discriminator Value** su **2**.

10. Impostare la proprietà **Base Class Discriminator Value** su **1**.

11. Impostare la proprietà **Inheritance Default** su **Person**.

12. Compilare il progetto.

## <a name="query-the-inherited-class-and-display-the-data-on-the-form"></a>Esecuzione di una query sulla classe ereditata e visualizzazione dei dati nel form
 A questo punto si aggiungerà codice al form che esegue una query per una classe specifica nel modello a oggetti.

#### <a name="to-create-a-linq-query-and-display-the-results-on-the-form"></a>Per creare una query LINQ e visualizzare i risultati nel form

1. Trascinare un **controllo ListBox** in Form1.

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
 Eseguire l'applicazione e verificare che i record visualizzati nella casella di riepilogo rappresentino tutti i dipendenti (record che presentano il valore 2 nella rispettiva colonna Type).

#### <a name="to-test-the-application"></a>Per testare l'applicazione

1. Premere F5.

2. Verificare che siano visualizzati solo i record che presentano il valore 2 nella rispettiva colonna Type.

3. Chiudere il form. Scegliere **Interrompi debug**dal menu **debug** .

## <a name="see-also"></a>Vedere anche
 [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [procedura: aggiungere classi LINQ to SQL a un progetto (o-r designer)](https://msdn.microsoft.com/library/7bb184ab-ec54-4cda-b706-604b2b4a3ed6) [procedura dettagliata: creazione di classi LINQ to SQL (o-r designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (o/r designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [procedura: generare il modello a oggetti in Visual Basic o C#](https://msdn.microsoft.com/library/a0c73b33-5650-420c-b9dc-f49310c201ee)
