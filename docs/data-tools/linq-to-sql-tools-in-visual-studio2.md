---
title: Panoramica di O/R Designer
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4105a93d4ad459c8bc1cb3a7a20b37c69f311c12
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55931637"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Strumenti di LINQ to SQL in Visual Studio

LINQ to SQL è la prima tecnologia di mapping relazionale a oggetti rilasciata da Microsoft. Funziona bene in scenari di base e continua a essere supportato in Visual Studio, ma non è più in fase di sviluppo. Usare LINQ to SQL per la manutenzione di un'applicazione legacy che è già in uso o in semplici applicazioni che usano SQL Server e non richiedono il mapping a più tabelle. In generale, le nuove applicazioni devono usare Entity Framework quando è necessario un livello di mapper relazionale a oggetti.

In Visual Studio creare classi LINQ to SQL che rappresentano le tabelle SQL utilizzando la **Object Relational Designer** (**O/R Designer**).

Il **O/R Designer** dispone di due aree distinte nell'area di progettazione: il riquadro delle entità a sinistra e il riquadro dei metodi a destra. Il riquadro delle entità rappresenta l'area di progettazione principale in cui vengono visualizzate le classi di entità, le associazioni e le gerarchie di ereditarietà. Il riquadro dei metodi rappresenta invece l'area di progettazione in cui vengono visualizzati i metodi <xref:System.Data.Linq.DataContext> con mapping a stored procedure e funzioni.

Il **O/R Designer** fornisce una superficie di progettazione visiva per la creazione [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) classi di entità e associazioni (relazioni) basate sugli oggetti in un database. In altre parole, il **O/R Designer** crea un modello a oggetti in un'applicazione che esegue il mapping agli oggetti in un database. Viene inoltre generato l'oggetto fortemente tipizzato <xref:System.Data.Linq.DataContext> che invia e riceve i dati tra le classi di entità e il database. Il **O/R Designer** inoltre fornisce la funzionalità per eseguire il mapping di stored procedure e funzioni ai <xref:System.Data.Linq.DataContext> metodi per la restituzione di dati e il popolamento delle classi di entità. Infine, il **O/R Designer** offre la possibilità di progettare relazioni di ereditarietà tra classi di entità.

## <a name="open-the-or-designer"></a>Aprire la finestra di Progettazione relazionale oggetti

Per aggiungere un LINQ al modello di entity SQL per il progetto, scegliere **Project** > **Aggiungi nuovo elemento**, quindi selezionare **classi LINQ to SQL** dall'elenco di elementi di progetto:

![Classi LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio crea una *dbml* file e lo aggiunge alla soluzione. Questo è il file di mapping XML e i relativi file di codice correlate.

![Classi LINQ to SQL in Esplora soluzioni](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Quando si seleziona il *dbml* nel file, Visual Studio visualizza il **O/R Designer** nell'area che ti permette di creare visivamente il modello. La figura seguente mostra la finestra di progettazione dopo Northwind `Customers` e `Orders` le tabelle che sono state trascinate dal **Esplora Server**. Si noti la relazione tra le tabelle.

![Finestra di progettazione di LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> Il **O/R Designer** è un mapper relazionale a oggetti semplice, perché supporta solo le relazioni di mapping 1:1. In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database. Mapping complesso, quale il mapping di una classe di entità a una tabella unita in join, non è supportato. utilizzo di Entity Framework per il mapping complesso. Inoltre, la finestra di progettazione rappresenta un generatore di codice unidirezionale: pertanto, nel file di codice vengono riflesse solo le modifiche apportate all'area di progettazione. Le modifiche manuali al file di codice non vengono riflesse nel **O/R Designer**. Tutte le modifiche apportate manualmente nel file di codice vengono sovrascritte durante il salvataggio della finestra di progettazione e il codice viene rigenerato. Per informazioni su come aggiungere il codice utente ed estendere le classi generate per il **O/R Designer**, vedere [come: Estendere il codice generato da Object Relational Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Creare e configurare l'oggetto DataContext

Dopo aver aggiunto un **classi LINQ to SQL** elemento a un progetto e aprire il **O/R Designer**, l'area di progettazione vuota rappresenta un oggetto vuoto <xref:System.Data.Linq.DataContext> pronto per la configurazione. L'oggetto <xref:System.Data.Linq.DataContext> è configurato con le informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione. Pertanto, l'oggetto <xref:System.Data.Linq.DataContext> viene configurato usando le informazioni di connessione del primo elemento rilasciato nell'area di progettazione. Per altre informazioni sul <xref:System.Data.Linq.DataContext> classe, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Creare classi di entità con mapping a viste e tabelle di database

È possibile creare classi di entità con mappate alle tabelle e viste trascinando le tabelle di database e le viste da **Esplora Server** oppure **Esplora Database** nel **O/R Designer**. Come indicato nella sezione precedente, l'oggetto <xref:System.Data.Linq.DataContext> viene configurato con le informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione. Se viene aggiunto un elemento successive che usa una connessione diversa per il **O/R Designer**, è possibile modificare la connessione per il <xref:System.Data.Linq.DataContext>. Per altre informazioni, vedere [procedura: creare classi LINQ to SQL mappate a tabelle e visualizzazioni (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Creare metodi DataContext che chiamano le stored procedure e funzioni

È possibile creare <xref:System.Data.Linq.DataContext> metodi che chiamano (viene eseguito il mapping a) stored procedure e funzioni trascinandole da **Esplora Server** oppure **Esplora Database** nel **O/R Designer** . Stored procedure e funzioni vengono aggiunte per il **O/R Designer** come metodi del <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Quando si trascinano stored procedure e funzioni dal **Esplora Server** oppure **Esplora Database** nel **O/R Designer**, il tipo restituito dell'oggetto generato <xref:System.Data.Linq.DataContext> metodo varia a seconda di dove si rilascia l'elemento. Per altre informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurare un oggetto DataContext per utilizzare le stored procedure per salvare i dati tra le classi di entità e un database

Come indicato in precedenza, è possibile creare metodi <xref:System.Data.Linq.DataContext> che chiamano stored procedure e funzioni. Inoltre, è anche possibile assegnare stored procedure utilizzate per l'impostazione predefinita, LINQ al comportamento di runtime SQL, che esegue inserimenti, aggiornamenti ed eliminazioni. Per altre informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Ereditarietà e Object Relational Designer

Analogamente ad altri oggetti, classi LINQ to SQL può usare l'ereditarietà ed essere derivate da altre classi. In un database le relazioni di ereditarietà vengono create in diversi modi. Il **O/R Designer** supporta il concetto di ereditarietà a tabella singola come viene spesso implementato nei sistemi relazionali. Per altre informazioni, vedere [procedura: configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Query LINQ to SQL

Le classi di entità create per il **O/R Designer** progettate per l'utilizzo con [Language-Integrated query (LINQ)](/dotnet/csharp/linq/). Per altre informazioni, vedere [procedura: cercare informazioni](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information).

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separare il codice della classe entità e DataContext generato in diversi spazi dei nomi

Il **O/R Designer** fornisce il **Namespace contesto** e **Entity Namespace** proprietà il <xref:System.Data.Linq.DataContext>. Queste proprietà determinano lo spazio dei nomi in cui viene generato il codice delle classi di entità e <xref:System.Data.Linq.DataContext>. Per impostazione predefinita, tali proprietà sono vuote e le classi di entità e <xref:System.Data.Linq.DataContext> vengono generate nello spazio dei nomi dell'applicazione. Per generare il codice in uno spazio dei nomi diverso da quello dell'applicazione, immettere un valore nelle proprietà **Context Namespace** e/o **Entity Namespace**.

## <a name="reference-content"></a>Contenuto di riferimento

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Vedere anche

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Domande frequenti (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)