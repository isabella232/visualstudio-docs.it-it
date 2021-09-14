---
title: LINQ to SQL Panoramica di O/R Designer
description: Panoramica degli strumenti LINQ to SQL in Visual Studio. Informazioni sull'Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d79562c02aa5c7d8081a0a4f8b200d73ba9ec96b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631289"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Strumenti di LINQ to SQL in Visual Studio

LINQ to SQL è stata la prima tecnologia di mapping relazionale a oggetti rilasciata da Microsoft. Funziona bene negli scenari di base e continua a essere supportato in Visual Studio, ma non è più in fase di sviluppo attivo. Usare LINQ to SQL quando si mantiene un'applicazione legacy che la usa già o in applicazioni semplici che usano SQL Server e non richiedono il mapping a più tabelle. In generale, le nuove applicazioni devono usare il Entity Framework quando è necessario un livello di mapper relazionale a oggetti.

## <a name="install-the-linq-to-sql-tools"></a>Installare gli LINQ to SQL seguenti

In Visual Studio creare classi LINQ to SQL che rappresentano SQL tabelle usando Object Relational Designer **(** **O/R Designer**). La finestra di progettazione O/R è l'interfaccia utente per la modifica di file con estensione dbml. La modifica di file con estensione dbml con un'area di progettazione richiede gli strumenti LINQ to SQL che non sono installati per impostazione predefinita come parte dei carichi di lavoro di Visual Studio.

Per installare gli strumenti LINQ to SQL, avviare il programma di installazione di  Visual Studio, scegliere **Modifica,** selezionare la scheda Singoli componenti e quindi selezionare strumenti LINQ to SQL nella categoria Strumenti di **codice.** 

## <a name="what-is-the-or-designer"></a>Informazioni su O/R Designer

**O/R Designer** ha due aree distinte nell'area di progettazione: il riquadro delle entità a sinistra e il riquadro dei metodi a destra. Il riquadro delle entità rappresenta l'area di progettazione principale in cui vengono visualizzate le classi di entità, le associazioni e le gerarchie di ereditarietà. Il riquadro dei metodi rappresenta invece l'area di progettazione in cui vengono visualizzati i metodi <xref:System.Data.Linq.DataContext> con mapping a stored procedure e funzioni.

**O/R Designer offre** un'area di progettazione visiva per la [creazione](/dotnet/framework/data/adonet/sql/linq/index) LINQ to SQL classi di entità e associazioni (relazioni) basate su oggetti in un database. In altre parole, **O/R Designer** crea un modello a oggetti in un'applicazione che esegue il mapping agli oggetti di un database. Genera anche un fortemente tipizzato che <xref:System.Data.Linq.DataContext> invia e riceve dati tra le classi di entità e il database. **O/R Designer fornisce anche** funzionalità per eseguire il mapping di stored procedure e funzioni a metodi per la restituzione di dati e <xref:System.Data.Linq.DataContext> il popolamento delle classi di entità. Infine, **O/R Designer offre** la possibilità di progettare relazioni di ereditarietà tra le classi di entità.

## <a name="open-the-or-designer"></a>Aprire la finestra di progettazione di O/R

Per aggiungere un LINQ to SQL di entità al progetto, scegliere Project Aggiungi nuovo elemento e quindi selezionare classi LINQ to SQL  >   **dall'elenco** di elementi del progetto:

![Classi LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png)

Visual Studio crea un file *con estensione dbml* e lo aggiunge alla soluzione. Si tratta del file di mapping XML e dei relativi file di codice correlati.

![LINQ to SQL classi in Esplora soluzioni](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png)

Quando si seleziona il file *con estensione dbml,* Visual Studio l'area **di Progettazione O/R** che consente di creare visivamente il modello. La figura seguente illustra la finestra di progettazione dopo che northwind e le tabelle sono `Customers` `Orders` state trascinate da **Esplora server**. Si noti la relazione tra le tabelle.

![Finestra di progettazione di LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png)

> [!IMPORTANT]
> **O/R Designer è** un semplice mapper relazionale di oggetti perché supporta solo relazioni di mapping 1:1. In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database. Il mapping complesso, ad esempio il mapping di una classe di entità a una tabella unita in join, non è supportato. usare il Entity Framework per il mapping complesso. Inoltre, la finestra di progettazione rappresenta un generatore di codice unidirezionale: pertanto, nel file di codice vengono riflesse solo le modifiche apportate all'area di progettazione. Le modifiche manuali al file di codice non vengono riflesse in **O/R Designer.** Tutte le modifiche apportate manualmente nel file di codice vengono sovrascritte durante il salvataggio della finestra di progettazione e il codice viene rigenerato. Per informazioni su come aggiungere il codice utente ed estendere le classi generate per il **O/R Designer**, vedere [come: Estendere il codice generato da Object Relational Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="create-and-configure-the-datacontext"></a>Creare e configurare DataContext

Dopo aver aggiunto un **LINQ to SQL classi** a un progetto e aver aperto **O/R Designer,** l'area di progettazione vuota rappresenta un elemento vuoto pronto <xref:System.Data.Linq.DataContext> per la configurazione. L'oggetto <xref:System.Data.Linq.DataContext> è configurato con le informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione. Pertanto, l'oggetto <xref:System.Data.Linq.DataContext> viene configurato usando le informazioni di connessione del primo elemento rilasciato nell'area di progettazione. Per altre informazioni sulla <xref:System.Data.Linq.DataContext> classe , vedere Metodi [DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="create-entity-classes-that-map-to-database-tables-and-views"></a>Creare classi di entità mappate a tabelle e viste di database

È possibile creare classi di entità mappate a tabelle e viste trascinando tabelle e viste di database **da** Esplora server **o Esplora database** in **O/R Designer.** Come indicato nella sezione precedente, l'oggetto <xref:System.Data.Linq.DataContext> viene configurato con le informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione. Se a **O/R Designer** viene aggiunto un elemento successivo che usa una connessione diversa, è possibile modificare la connessione per <xref:System.Data.Linq.DataContext> . Per altre informazioni, vedere Procedura: Creare classi LINQ to SQL mappate a tabelle e viste [(O/R Designer).](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)

## <a name="create-datacontext-methods-that-call-stored-procedures-and-functions"></a>Creare metodi DataContext che chiamano stored procedure e funzioni

È possibile creare metodi che chiamano stored procedure e funzioni (di cui è stato eseguito il mapping) trascinandole da Esplora server o <xref:System.Data.Linq.DataContext> **Esplora database** in **O/R Designer.**  Le stored procedure e le funzioni vengono aggiunte a **O/R Designer** come metodi di <xref:System.Data.Linq.DataContext> .

> [!NOTE]
> Quando si trascinano stored procedure e funzioni da **Esplora server** o **Esplora database in** **O/R Designer,** il tipo restituito del metodo generato varia a seconda della posizione in cui si rilascia l'elemento. <xref:System.Data.Linq.DataContext> Per altre informazioni, vedere [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configure-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurare un Oggetto DataContext per l'uso di stored procedure per salvare i dati tra classi di entità e un database

Come indicato in precedenza, è possibile creare metodi <xref:System.Data.Linq.DataContext> che chiamano stored procedure e funzioni. È anche possibile assegnare stored procedure usate per il comportamento LINQ to SQL di esecuzione, che esegue inserimenti, aggiornamenti ed eliminazioni. Per altre informazioni, vedere Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed [eliminazioni (O/R Designer).](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)

## <a name="inheritance-and-the-or-designer"></a>Ereditarietà e Object Relational Designer

Analogamente ad altri oggetti, LINQ to SQL classi possono usare l'ereditarietà ed essere derivate da altre classi. In un database le relazioni di ereditarietà vengono create in diversi modi. **O/R Designer** supporta il concetto di ereditarietà a tabella singola perché viene spesso implementata nei sistemi relazionali. Per altre informazioni, vedere [Procedura: Configurare l'ereditarietà tramite O/R Designer.](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)

## <a name="linq-to-sql-queries"></a>Query LINQ to SQL

Le classi di entità create da **O/R Designer** sono progettate per l'uso con [LINQ (Language-Integrated Query).](/dotnet/csharp/linq/) Per altre informazioni, vedere [Procedura: Eseguire query per informazioni.](/dotnet/framework/data/adonet/sql/linq/how-to-query-for-information)

## <a name="separate-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separare il dataContext generato e il codice della classe di entità in spazi dei nomi diversi

**O/R Designer fornisce** le proprietà Dello spazio dei nomi **del** contesto e Spazio **dei nomi** entità in <xref:System.Data.Linq.DataContext> . Queste proprietà determinano lo spazio dei nomi in cui viene generato il codice delle classi di entità e <xref:System.Data.Linq.DataContext>. Per impostazione predefinita, tali proprietà sono vuote e le classi di entità e <xref:System.Data.Linq.DataContext> vengono generate nello spazio dei nomi dell'applicazione. Per generare il codice in uno spazio dei nomi diverso da quello dell'applicazione, immettere un valore nelle proprietà **Context Namespace** e/o **Entity Namespace**.

## <a name="reference-content"></a>Contenuto di riferimento

- <xref:System.Linq>
- <xref:System.Data.Linq>

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/index)
- [Domande frequenti (.NET Framework)](/dotnet/framework/data/adonet/sql/linq/frequently-asked-questions)
