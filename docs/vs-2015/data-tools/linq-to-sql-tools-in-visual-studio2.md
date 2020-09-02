---
title: Strumenti di LINQ to SQL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 470cfabd54fa5f2b92001a635477c60d45fac538
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651509"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Strumenti di LINQ to SQL in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

LINQ to SQL è stata la prima tecnologia di mapping relazionale a oggetti rilasciata da Microsoft. Funziona bene negli scenari di base e continua a essere supportato in Visual Studio, ma non è più in fase di sviluppo attivo. Usare LINQ to SQL quando si gestisce un'applicazione legacy che lo sta già usando o in applicazioni semplici che usano SQL Server e non richiedono il mapping a più tabelle. In generale, le nuove applicazioni devono usare il Entity Framework quando è necessario un livello di mapper relazionale a oggetti.

 In Visual Studio è possibile creare LINQ to SQL classi che rappresentano le tabelle SQL utilizzando [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Dispone di due aree distinte nella relativa area di progettazione: il riquadro entità a sinistra e il riquadro dei metodi a destra. Il riquadro delle entità rappresenta l'area di progettazione principale in cui vengono visualizzate le classi di entità, le associazioni e le gerarchie di ereditarietà. Il riquadro dei metodi rappresenta invece l'area di progettazione in cui vengono visualizzati i metodi <xref:System.Data.Linq.DataContext> con mapping a stored procedure e funzioni.

 [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)]( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ) Fornisce un'area di progettazione visiva per la creazione di [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) le classi di entità e le associazioni (relazioni) basate sugli oggetti in un database. In altre parole, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] viene usato per creare un modello a oggetti in un'applicazione con mapping agli oggetti in un database e genera inoltre un oggetto <xref:System.Data.Linq.DataContext> fortemente tipizzato, usato per inviare e ricevere dati tra le classi di entità e il database. In [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] è disponibile anche una funzionalità per eseguire il mapping di stored procedure e funzioni ai metodi <xref:System.Data.Linq.DataContext> per la restituzione di dati e il popolamento delle classi di entità. Infine, in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] viene fornita la possibilità di progettare relazioni di ereditarietà tra le classi di entità.

## <a name="opening-the-or-designer"></a>Apertura di Progettazione relazionale oggetti
 Per aggiungere un modello di entità LINQ to SQL al progetto, scegliere **progetto &#124; Aggiungi nuovo elemento** e quindi scegliere  **LINQ to SQL classi** dall'elenco di elementi del progetto:

 ![Classi LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "Classi LINQ to SQL raddata")

 Visual Studio crea un file con estensione dbml e lo aggiunge alla soluzione. Si tratta del file di mapping XML e dei file di codice correlati.

 ![Classi LINQ to SQL in Esplora soluzioni](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "classi LINQ to SQL raddata in Esplora soluzioni")

 Quando si seleziona il file con estensione dbml, Visual Studio Mostra l'area della finestra di progettazione O/R che consente di creare visivamente il modello. Nella figura seguente viene illustrata la finestra di progettazione dopo che le tabelle Customers e Orders di Northwind sono state trascinate da Esplora server. Si noti la relazione tra le tabelle.

 ![Finestra di progettazione di LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL Designer")

> [!IMPORTANT]
> [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]È un mapper relazionale a oggetti semplice perché supporta solo relazioni di mapping 1:1. In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database. Il mapping complesso, ad esempio il mapping di una classe di entità a una tabella unita in join, non è supportato. usare il Entity Framework per il mapping complesso. Inoltre, la finestra di progettazione rappresenta un generatore di codice unidirezionale: pertanto, nel file di codice vengono riflesse solo le modifiche apportate all'area di progettazione. Le modifiche manuali apportate al file di codice non vengono riflesse in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Tutte le modifiche apportate manualmente nel file di codice vengono sovrascritte durante il salvataggio della finestra di progettazione e il codice viene rigenerato. Per informazioni su come aggiungere codice utente ed estendere le classi generate da [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , vedere [procedura: estendere il codice generato da O/R Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="creating-and-configuring-the-datacontext"></a>Creazione e configurazione dell'oggetto DataContext
 Dopo l'aggiunta di un elemento **classi LINQ to SQL** a un progetto e l'apertura di [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , l'area di progettazione vuota rappresenta un oggetto vuoto <xref:System.Data.Linq.DataContext> pronto per la configurazione. <xref:System.Data.Linq.DataContext>viene configurato con le informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione. Pertanto, l'oggetto <xref:System.Data.Linq.DataContext> viene configurato usando le informazioni di connessione del primo elemento rilasciato nell'area di progettazione. Per ulteriori informazioni sulla <xref:System.Data.Linq.DataContext> classe, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Creazione di classi di entità con mapping a tabelle e visualizzazioni di database
 È possibile creare classi di entità di cui è stato eseguito il mapping a tabelle e viste trascinando le tabelle e le viste di database da **Esplora server** / **Esplora database** su [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Come indicato nella sezione precedente, l'oggetto <xref:System.Data.Linq.DataContext> viene configurato con le informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione. Se a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] viene aggiunto un elemento successivo che usa una connessione diversa, è possibile modificare la connessione per l'oggetto <xref:System.Data.Linq.DataContext>. Per altre informazioni, vedere [procedura: creare LINQ to SQL classi mappate a tabelle e viste (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Creazione di metodi DataContext che chiamano stored procedure e funzioni
 È possibile creare <xref:System.Data.Linq.DataContext> metodi che chiamano le stored procedure e le funzioni (a cui è stato eseguito il mapping) trascinandoli da **Esplora server** / **Esplora database** su [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] . Le stored procedure e le funzioni vengono aggiunte a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] come metodi dell'oggetto <xref:System.Data.Linq.DataContext>.

> [!NOTE]
> Quando si trascinano stored procedure e funzioni da **Esplora server** / **Esplora database** su [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , il tipo restituito del <xref:System.Data.Linq.DataContext> metodo generato varia a seconda della posizione in cui si rilascia l'elemento. Per altre informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurazione di un oggetto DataContext in modo che utilizzi stored procedure per salvare i dati tra le classi di entità e un database
 Come indicato in precedenza, è possibile creare metodi <xref:System.Data.Linq.DataContext> che chiamano stored procedure e funzioni. Inoltre, è anche possibile assegnare stored procedure utilizzabili per il comportamento in fase di esecuzione [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] predefinito che esegue i comandi di inserimento, aggiornamento ed eliminazione. Per altre informazioni, vedere [procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Ereditarietà e Progettazione relazionale oggetti
 Analogamente ad altri oggetti, le classi [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] possono usare l'ereditarietà ed essere derivate da altre classi. In un database le relazioni di ereditarietà vengono create in diversi modi. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] supporta il concetto di ereditarietà a tabella singola come viene spesso implementato nei sistemi relazionali. Per altre informazioni, vedere [procedura: configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Query [LINQ to SQL]
 Le classi di entità create da [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] sono progettate per essere utilizzate con [LINQ (Language-Integrated Query)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). Per ulteriori informazioni, vedere [procedura: eseguire una query per ottenere informazioni](https://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separazione del codice delle classi di entità e DataContext generate in diversi spazi dei nomi
 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]Fornisce le proprietà dello **spazio dei** nomi del contesto e **dello spazio dei nomi dell'entità** in <xref:System.Data.Linq.DataContext> . Queste proprietà determinano lo spazio dei nomi in cui viene generato il codice delle classi di entità e <xref:System.Data.Linq.DataContext>. Per impostazione predefinita, tali proprietà sono vuote e le classi di entità e <xref:System.Data.Linq.DataContext> vengono generate nello spazio dei nomi dell'applicazione. Per generare il codice in uno spazio dei nomi diverso da quello dell'applicazione, immettere un valore nelle proprietà **Context Namespace** e/o **Entity Namespace**.

## <a name="in-this-section"></a>Contenuto della sezione
 [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) Vengono illustrati <xref:System.Data.Linq.DataContext> i metodi e le modalità di creazione.

 [Ereditarietà delle classi di dati (O/R Designer)](../data-tools/data-class-inheritance-o-r-designer.md) Viene descritto il concetto di ereditarietà a tabella singola e il modo in cui viene implementato in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Procedura: creare classi di LINQ to SQL mappate a tabelle e viste (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) Viene descritto come creare classi di entità di cui è stato eseguito il mapping a tabelle e viste in un database.

 [Procedura: creare un'associazione (relazione) tra classi di LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) Viene descritto come creare una relazione tra [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] le classi di entità.

 [Procedura: creare metodi DataContext mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) Viene descritto come creare <xref:System.Data.Linq.DataContext> metodi che eseguono stored procedure o funzioni quando vengono chiamati.

 [Procedura: assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) Viene descritto come configurare un oggetto <xref:System.Data.Linq.DataContext> per l'utilizzo di stored procedure quando si salvano i dati dalle classi di entità in un database.

 [Procedura: modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) Viene descritto come impostare il tipo restituito di un <xref:System.Data.Linq.DataContext> metodo in modo che sia il tipo di una classe di entità o di un tipo generato automaticamente creato da O/R Designer.

 [Procedura: aggiungere la convalida a classi di entità](../data-tools/how-to-add-validation-to-entity-classes.md) Viene descritto come generare metodi parziali che consentono l'aggiunta di codice durante le modifiche alle proprietà e gli aggiornamenti delle classi di entità.

 [Procedura: attivare e disattivare la pluralità (O/R Designer)](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) Viene descritto come attivare e disattivare la ridenominazione automatica delle classi aggiunte a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Procedura: configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) Viene descritto come configurare le classi di entità usando l'ereditarietà a tabella singola con [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Procedura: estendere il codice generato da O/R Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) Viene descritto come e quando aggiungere codice che non verrà sovrascritto quando le modifiche apportate agli oggetti in Progettazione relazionale oggetti rigenerano il codice.

 [Procedura dettagliata: creazione di classi di LINQ to SQL usando l'ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) Vengono fornite istruzioni dettagliate per la configurazione delle classi di entità mediante l'ereditarietà a tabella singola con [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

 [Procedura dettagliata: personalizzazione del comportamento di inserimento, aggiornamento ed eliminazione delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) Vengono fornite istruzioni dettagliate per la configurazione di un oggetto <xref:System.Data.Linq.DataContext> per l'utilizzo di stored procedure quando si salvano i dati dalle classi di entità in un database.

## <a name="reference-content"></a>Contenuto di riferimento
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>Vedere anche
 [Domande frequenti](https://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) su [Visual Studio Data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
