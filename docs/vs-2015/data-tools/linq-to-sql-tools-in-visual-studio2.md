---
title: Strumenti LINQ to SQL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 45e477c0-5c6b-41f9-b2d0-2808fb4f6537
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 44e12e616e453dcdc0390e8a6eb5b2065a51a6bb
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59656934"
---
# <a name="linq-to-sql-tools-in-visual-studio"></a>Strumenti LINQ to SQL in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

LINQ to SQL è la prima tecnologia di mapping relazionale a oggetti rilasciata da Microsoft. Funziona bene in scenari di base e continua a essere supportato in Visual Studio, ma non è più in fase di sviluppo. Usare LINQ to SQL per la manutenzione di un'applicazione legacy che è già in uso o in semplici applicazioni che usano SQL Server e non richiedono il mapping a più tabelle. In generale, le nuove applicazioni devono usare Entity Framework quando è necessario un livello di mapper relazionale a oggetti.

 In Visual Studio creare classi LINQ to SQL che rappresentano le tabelle SQL utilizzando il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 Il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] dispone di due aree distinte nell'area di progettazione: il riquadro delle entità a sinistra e il riquadro dei metodi a destra. Il riquadro delle entità rappresenta l'area di progettazione principale in cui vengono visualizzate le classi di entità, le associazioni e le gerarchie di ereditarietà. Il riquadro dei metodi rappresenta invece l'area di progettazione in cui vengono visualizzati i metodi <xref:System.Data.Linq.DataContext> con mapping a stored procedure e funzioni.

 Il [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) fornisce una superficie di progettazione visiva per la creazione [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) classi di entità e associazioni (relazioni) basate sugli oggetti in un database. In altre parole, [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] viene usato per creare un modello a oggetti in un'applicazione con mapping agli oggetti in un database e genera inoltre un oggetto <xref:System.Data.Linq.DataContext> fortemente tipizzato, usato per inviare e ricevere dati tra le classi di entità e il database. In [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] è disponibile anche una funzionalità per eseguire il mapping di stored procedure e funzioni ai metodi <xref:System.Data.Linq.DataContext> per la restituzione di dati e il popolamento delle classi di entità. Infine, in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] viene fornita la possibilità di progettare relazioni di ereditarietà tra le classi di entità.

## <a name="opening-the-or-designer"></a>Apertura di Progettazione relazionale oggetti
 Per aggiungere un LINQ al modello di entity SQL per il progetto, scegliere **progetto &#124; Aggiungi nuovo elemento** e quindi scegliere **classi LINQ to SQL** dall'elenco di elementi di progetto:

 ![Classi LINQ to SQL](../data-tools/media/raddata-linq-to-sql-classes.png "raddata classi LINQ to SQL")

 Visual Studio crea un file con estensione dbml e lo aggiunge alla soluzione. Questo è il file di mapping XML e i relativi file di codice correlate.

 ![Le classi LINQ to SQL in Esplora soluzioni](../data-tools/media/raddata-linq-to-sql-classes-in-solution-explorer.png "classi raddata LINQ to SQL in Esplora soluzioni")

 Quando si seleziona il file. dbml, Visual Studio visualizza l'area di Progettazione relazionale oggetti che consente di creare visivamente il modello. La figura seguente mostra la finestra di progettazione dopo le tabelle Northwind Customers e Orders che sono state trascinate da Esplora Server. Si noti la relazione tra le tabelle.

 ![Progettazione LINQ to SQL](../data-tools/media/raddata-linq-to-sql-designer.png "raddata LINQ to SQL Designer")

> [!IMPORTANT]
>  Il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] è un mapper relazionale a oggetti semplice, perché supporta solo le relazioni di mapping 1:1. In altre parole, una classe di entità può presentare solo una relazione di mapping 1:1 con una tabella o visualizzazione di database. Mapping complesso, quale il mapping di una classe di entità a una tabella unita in join, non è supportato. utilizzo di Entity Framework per il mapping complesso. Inoltre, la finestra di progettazione rappresenta un generatore di codice unidirezionale: pertanto, nel file di codice vengono riflesse solo le modifiche apportate all'area di progettazione. Le modifiche manuali apportate al file di codice non vengono riflesse in [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Tutte le modifiche apportate manualmente nel file di codice vengono sovrascritte durante il salvataggio della finestra di progettazione e il codice viene rigenerato. Per informazioni su come aggiungere il codice utente ed estendere le classi generate per il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], vedere [come: Estendere il codice generato da O/R Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md).

## <a name="creating-and-configuring-the-datacontext"></a>Creazione e configurazione dell'oggetto DataContext
 Dopo aver aggiunto un **classi LINQ to SQL** elemento a un progetto e aprire il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], l'area di progettazione vuota rappresenta un oggetto vuoto <xref:System.Data.Linq.DataContext> pronto per la configurazione. il <xref:System.Data.Linq.DataContext> è configurato con le informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione... Pertanto, l'oggetto <xref:System.Data.Linq.DataContext> viene configurato usando le informazioni di connessione del primo elemento rilasciato nell'area di progettazione. Per altre informazioni sul <xref:System.Data.Linq.DataContext> classe, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="creating-entity-classes-that-map-to-database-tables-and-views"></a>Creazione di classi di entità con mapping a tabelle e visualizzazioni di database
 È possibile creare classi di entità con mappate alle tabelle e viste trascinando le tabelle di database e le viste da **Esplora Server**/**Database Explorer** nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Come indicato nella sezione precedente, l'oggetto <xref:System.Data.Linq.DataContext> viene configurato con le informazioni di connessione fornite dal primo elemento trascinato nell'area di progettazione. Se a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] viene aggiunto un elemento successivo che usa una connessione diversa, è possibile modificare la connessione per l'oggetto <xref:System.Data.Linq.DataContext>. Per altre informazioni, vedere [Procedura: Creare classi LINQ to SQL mappate a tabelle e viste (Object Relational Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="creating-datacontext-methods-that-call-stored-procedures-and-functions"></a>Creazione di metodi DataContext che chiamano stored procedure e funzioni
 È possibile creare <xref:System.Data.Linq.DataContext> metodi che chiamano (viene eseguito il mapping a) stored procedure e funzioni trascinandole da **Esplora Server**/**Esplora Database** nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. Le stored procedure e le funzioni vengono aggiunte a [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] come metodi dell'oggetto <xref:System.Data.Linq.DataContext>.

> [!NOTE]
>  Quando si trascinano stored procedure e funzioni dal **Esplora Server**/**Esplora Database** nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], il tipo restituito dell'oggetto generato <xref:System.Data.Linq.DataContext> differisce (metodo) a seconda della posizione in cui si rilascia l'elemento. Per altre informazioni, vedere [metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md).

## <a name="configuring-a-datacontext-to-use-stored-procedures-to-save-data-between-entity-classes-and-a-database"></a>Configurazione di un oggetto DataContext in modo che utilizzi stored procedure per salvare i dati tra le classi di entità e un database
 Come indicato in precedenza, è possibile creare metodi <xref:System.Data.Linq.DataContext> che chiamano stored procedure e funzioni. Inoltre, è anche possibile assegnare stored procedure utilizzabili per il comportamento in fase di esecuzione [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] predefinito che esegue i comandi di inserimento, aggiornamento ed eliminazione. Per altre informazioni, vedere [Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (Object Relational Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md).

## <a name="inheritance-and-the-or-designer"></a>Ereditarietà e Progettazione relazionale oggetti
 Analogamente ad altri oggetti, le classi [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] possono usare l'ereditarietà ed essere derivate da altre classi. In un database le relazioni di ereditarietà vengono create in diversi modi. [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] supporta il concetto di ereditarietà a tabella singola come viene spesso implementato nei sistemi relazionali. Per altre informazioni, vedere [Procedura: Configurare l'ereditarietà usando Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md).

## <a name="linq-to-sql-queries"></a>Query [LINQ to SQL]
 Le classi di entità create per il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] progettate per l'utilizzo con [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d). Per altre informazioni, vedere [Procedura: Richiedere informazioni](http://msdn.microsoft.com/library/e538d288-2070-40ca-9da6-4fbc68cd6ad0).

## <a name="separating-the-generated-datacontext-and-entity-class-code-into-different-namespaces"></a>Separazione del codice delle classi di entità e DataContext generate in diversi spazi dei nomi
 Il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] fornisce il **contesto Namespace** e **Entity Namespace** proprietà il <xref:System.Data.Linq.DataContext>. Queste proprietà determinano lo spazio dei nomi in cui viene generato il codice delle classi di entità e <xref:System.Data.Linq.DataContext>. Per impostazione predefinita, tali proprietà sono vuote e le classi di entità e <xref:System.Data.Linq.DataContext> vengono generate nello spazio dei nomi dell'applicazione. Per generare il codice in uno spazio dei nomi diverso da quello dell'applicazione, immettere un valore nelle proprietà **Context Namespace** e/o **Entity Namespace**.

## <a name="in-this-section"></a>Contenuto della sezione
 [Metodi DataContext (O/R Designer)](../data-tools/datacontext-methods-o-r-designer.md) spiega cosa <xref:System.Data.Linq.DataContext> metodi sono e come crearli.

 [Ereditarietà (O/R Designer) delle classi di dati](../data-tools/data-class-inheritance-o-r-designer.md) descrive il concetto di ereditarietà a tabella singola e come implementarlo nel [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Procedura: Creare classi SQL mappate a tabelle e visualizzazioni (O/R Designer) LINQ to](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md) viene descritto come creare classi di entità che vengono eseguito il mapping a tabelle e visualizzazioni in un database.

 [Procedura: Creare un'associazione (relazione) tra classi LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) descrive come creare una relazione tra [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] le classi di entità.

 [Procedura: Creare metodi DataContext mappati a stored procedure e funzioni (O/R Designer)](../data-tools/how-to-create-datacontext-methods-mapped-to-stored-procedures-and-functions-o-r-designer.md) descrive come creare <xref:System.Data.Linq.DataContext> metodi che eseguono stored procedure o funzioni quando vengono chiamati.

 [Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md) descrive come configurare un <xref:System.Data.Linq.DataContext> per utilizzare le stored procedure durante il salvataggio dei dati dall'entità classi nuovamente in un database.

 [Procedura: Modificare il tipo restituito di un metodo DataContext (O/R Designer)](../data-tools/how-to-change-the-return-type-of-a-datacontext-method-o-r-designer.md) descrive come impostare il tipo restituito di un <xref:System.Data.Linq.DataContext> metodo il tipo di una classe di entità o un tipo generato automaticamente creata da Progettazione relazionale oggetti.

 [Procedura: Aggiungere la convalida a classi di entità](../data-tools/how-to-add-validation-to-entity-classes.md) viene descritto come generare metodi parziali che consentano l'aggiunta di codice durante le modifiche alle proprietà e gli aggiornamenti delle classi di entità.

 [Procedura: Attivare e disattivare (O/R Designer) la pluralizzazione](../data-tools/how-to-turn-pluralization-on-and-off-o-r-designer.md) viene descritto come attivare e disattivare la ridenominazione automatica delle classi che vengono aggiunti al [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Procedura: Configurare l'ereditarietà tramite O/R Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) descrive come configurare le classi di entità con ereditarietà a tabella singola con il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Procedura: Estendere il codice generato da O/R Designer](../data-tools/how-to-extend-code-generated-by-the-o-r-designer.md) viene descritto come e dove aggiungere il codice che non verrà sovrascritto quando le modifiche agli oggetti nella finestra di Progettazione relazionale oggetti rigenerare codice.

 [Procedura dettagliata: Creazione di classi LINQ to SQL da tramite ereditarietà a tabella singola (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) vengono fornite istruzioni dettagliate per la configurazione di classi di entità con ereditarietà a tabella singola con il [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

 [Procedura dettagliata: Personalizzazione di inserimento, aggiornamento ed eliminazione, il comportamento delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md) vengono fornite istruzioni dettagliate per la configurazione di un <xref:System.Data.Linq.DataContext> per utilizzare le stored procedure durante il salvataggio dei dati dall'entità classi nuovamente in un database.

## <a name="reference-content"></a>Contenuto di riferimento
 <xref:System.Linq>

 <xref:System.Data.Linq>

## <a name="see-also"></a>Vedere anche
 [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md) [Frequently Asked Questions](http://msdn.microsoft.com/library/252ed666-0679-4eea-b71b-2f14117ef443) [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [l'accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
