---
title: Creazione di applicazioni dati | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data access [Visual Studio], creating applications
- applications [Visual Studio], data
- data [Visual Studio]
- data [Visual Studio], creating applications
ms.assetid: ab334d5f-4f49-4346-bce0-3325d6130b3e
caps.latest.revision: 41
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4e5354d167dd6d3a1bef9beeb3dcaaaf24871bab
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49291317"
---
# <a name="creating-data-applications"></a>Creazione di applicazioni dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio sono disponibili molti strumenti in fase di progettazione che consentono di creare applicazioni che accedono ai dati. In questa introduzione vengono forniti i cenni preliminari sui processi di base coinvolti nella creazione di applicazioni che utilizzano dati. Le informazioni qui fornite, in cui sono deliberatamente evitati molti dettagli, vanno intese come fonte generale di informazione e come punto di partenza per le numerose pagine della Guida associate alla creazione di un'applicazione dati.  
  
 Quando si sviluppano applicazioni che richiedono l'accesso ai dati in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], possono presentarsi diverse esigenze. In alcuni casi, può essere necessario visualizzare i dati in un form. In altri casi, può invece essere necessario individuare un metodo per condividere le informazioni con altri processi o applicazioni.  
  
 A prescindere dall'utilizzo che viene fatto dei dati, è necessario comprendere alcuni concetti fondamentali. È possibile che non sorga mai la necessità di conoscere alcuni dettagli della gestione dei dati, ad esempio si può ignorare come si crea un database a livello di codice, ma è molto utile conoscere i concetti base relativi ai dati, nonché gli strumenti dei dati (procedure guidate e finestre di progettazione) disponibili in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Un'applicazione dati tipica utilizza la maggior parte dei processi illustrati nel diagramma seguente:  
  
 ![Rappresentazione grafica del ciclo dei dati](../data-tools/media/datacyclegraphicinfo.gif "datacyclegraphicinfo")  
Il ciclo dei dati  
  
 Quando si crea un'applicazione, è necessario pensare all'attività che si intende eseguire. Per un supporto nella ricerca degli strumenti di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e degli oggetti disponibili, utilizzare le sezioni illustrate di seguito.  
  
> [!NOTE]
>  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornisce procedure guidate per semplificare diversi processi illustrati nel diagramma precedente. Ad esempio, in esecuzione la **configurazione guidata origine dati** fornisce all'applicazione le informazioni necessarie per connettersi ai dati, creare un dataset tipizzato per ricevere i dati e inserire i dati nell'applicazione.  
  
 Per visualizzare rapidamente la modalità [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] possono essere utili per lo sviluppo di applicazioni dati, vedere [questa procedura dettagliata: creazione di un'applicazione dati semplice](http://msdn.microsoft.com/library/c5d0968c-d86f-4ae9-a2e1-871f208a3bb3).  
  
## <a name="connecting-to-data"></a>Connessione ai dati  
 Per portare i dati all'interno dell'applicazione e rinviare le modifiche all'origine dati, è necessario stabilire una sorta di comunicazione bidirezionale. Questa comunicazione bidirezionale viene generalmente gestita dagli oggetti del modello dati.  
  
 Ad esempio, `TableAdapter` consente di connettere le applicazioni che utilizzano i dataset a un database e <xref:System.Data.Objects.ObjectContext> di connettere le entità in Entity Framework a un database. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornisce diversi strumenti di supporto che possono essere utilizzati dall'applicazione per la creazione di connessioni. Per altre informazioni sulla connessione ai dati dell'applicazione, vedere [sulla connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md).  
  
 Per informazioni su come usare i set di dati per connettere l'applicazione ai dati in un database, vedere [procedura dettagliata: connessione ai dati in un Database (Windows Form)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c).  
  
## <a name="preparing-your-application-to-receive-data"></a>Preparazione dell'applicazione al ricevimento di dati  
 Se l'applicazione utilizza un modello di dati disconnesso, è necessario archiviare temporaneamente i dati dell'applicazione mentre la si utilizza. In Visual Studio sono disponibili strumenti che consentono di creare gli oggetti utilizzati dall'applicazione per archiviare temporaneamente i dati: dataset, entità e oggetti [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)].  
  
> [!NOTE]
>  Di solito, in un'applicazione che utilizza un modello di dati disconnesso si procede effettuando la connessione a un database, eseguendo una query per il passaggio di dati nell'applicazione, effettuando la disconnessione dal database e infine modificando i dati offline prima di riconnettere e aggiornare il database.  
  
 Per altre informazioni sulla creazione di dataset tipizzati nell'applicazione, vedere [Preparing Your Application to Receive Data](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad). Per altre informazioni sull'utilizzo dei dataset nelle applicazioni a più livelli, vedere [separare DataSet e TableAdapter in progetti diversi](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md).  
  
 Per informazioni su come creare un set di dati, completare le procedure descritte in [procedura dettagliata: creazione di un set di dati con Progettazione Dataset](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md).  
  
 Per informazioni su come creare [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] oggetti, completare le procedure descritte in [questa procedura dettagliata: creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
## <a name="fetching-data-into-your-application"></a>Recupero di dati nell'applicazione  
 A prescindere dal fatto che nell'applicazione venga utilizzato o meno un modello di dati, è necessario essere in grado di recuperare dati all'interno di questa. Per passare dati nell'applicazione, si eseguono query o stored procedure in un database Le applicazioni che archiviano i dati nei dataset eseguono query e stored procedure utilizzando `TableAdapter`s, mentre le applicazioni che archiviano i dati nelle entità eseguono query utilizzando [LINQ to Entities](http://msdn.microsoft.com/library/641f9b68-9046-47a1-abb0-1c8eaeda0e2d) o tramite la connessione di entità direttamente alle stored procedure. Per altre informazioni sulla creazione e modifica delle query che utilizzano TableAdapter, vedere [procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md) e [procedura: modificare query TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md).  
  
 Per altre informazioni sul caricamento dei dati in set di dati e sull'esecuzione di query e stored procedure, vedere [recupero di dati in Your Application](../data-tools/fetching-data-into-your-application.md).  
  
 Per informazioni su come caricare i dati in un set di dati, completare le procedure descritte in [procedura dettagliata: visualizzazione dei dati in un Form Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md) ed esaminare il codice nel gestore dell'evento form load.  
  
 Per informazioni su come caricare dati in [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] oggetti, completare le procedure descritte in [questa procedura dettagliata: creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).  
  
 Per informazioni su come creare ed eseguire una query SQL, vedere [procedura: creare ed eseguire un'istruzione SQL che restituisce righe](http://msdn.microsoft.com/library/14637fc5-d42a-4cca-97ac-54c181ec3eed).  
  
 Per informazioni su come eseguire una stored procedure, vedere [procedura: eseguire una Stored Procedure che restituisce righe](http://msdn.microsoft.com/library/db3d7021-d3ef-4db8-b12a-b6146570355d).  
  
## <a name="displaying-data-on-forms"></a>Visualizzazione di dati nei form  
 Dopo avere inserito dati nell'applicazione, generalmente questi verranno visualizzati in un form per consentire agli utenti di visualizzarli o modificarli. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] fornisce il [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992), in cui è possibile trascinare elementi su form per creare automaticamente controlli associati a dati che visualizzano dati. Per altre informazioni sul data binding e la visualizzazione dei dati agli utenti, vedere [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 Per informazioni su come presentare i dati agli utenti, completare le procedure dettagliate seguenti (prestando particolare attenzione al processo di trascinamento di elementi dal **Zdroje dat** finestra):  
  
-   [Procedura dettagliata: Visualizzazione dei dati in un Form Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).  
  
-   [Associare controlli WPF a un servizio di dati WCF](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)  
  
-   [Procedura dettagliata: Associazione di controlli Silverlight a un servizio dati WCF](http://msdn.microsoft.com/library/f3f08661-7d91-4185-8ed6-912d524d4c6b)  
  
## <a name="editing-data-in-your-application"></a>Modifica di dati nell'applicazione  
 Dopo che i dati sono stati presentati agli utenti, è probabile che questi ultimi apporteranno delle variazioni aggiungendo nuovi record o modificando quelli esistenti prima di rinviarli al database.  
  
 Per altre informazioni sull'utilizzo dei dati una volta che viene caricato in set di dati, vedere [modifica dei dati nell'applicazione](../data-tools/editing-data-in-your-application.md).  
  
## <a name="validating-data"></a>Convalida dei dati  
 Dopo aver apportato modifiche ai dati, solitamente si effettuano delle verifiche prima di consentire che i valori modificati vengano accettati nel dataset o scritti nel database. *Convalida* è il nome del processo per verificare che i nuovi valori sono accettabili per i requisiti dell'applicazione. È possibile aggiungere una logica per il controllo dei valori nell'applicazione mentre sono in corso le modifiche. In Visual Studio sono disponibili strumenti che consentono di aggiungere codice per la convalida dei dati durante la modifica di colonna e righe. Per altre informazioni, vedere [convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e).  
  
 Per informazioni su come aggiungere la convalida dei dati all'applicazione, vedere [procedura dettagliata: aggiunta di convalida a un set di dati](http://msdn.microsoft.com/library/09351fab-d670-45e3-b53a-a944eff717e7).  
  
 Per informazioni su come aggiungere la convalida a un set di dati separata in un'applicazione a più livelli, vedere [aggiungere la convalida a un set di dati a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
## <a name="saving-data"></a>Salvataggio di dati  
 Dopo aver apportato le modifiche nell'applicazione e averle convalidate, generalmente si procede al relativo rinvio al database. Le applicazioni che archiviano i dati nei dataset utilizzano generalmente un TableAdapterManager per salvare i dati. Per altre informazioni, vedere [Panoramica di TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650). Usano le applicazioni Entity Framework il <xref:System.Data.Objects.ObjectContext.SaveChanges%2A> metodo per salvare i dati.  
  
 Per altre informazioni sull'invio di dati aggiornati in un database, vedere [salvataggio di dati](../data-tools/saving-data.md).  
  
 Per informazioni su come inviare i dati aggiornati da un set di dati a un database, completare le procedure descritte in [procedura dettagliata: salvataggio di dati dalle tabelle dati correlate (aggiornamento gerarchico)](http://msdn.microsoft.com/library/50601bd7-a488-480c-9910-3c6570fa3a1b).  
  
## <a name="related-topics"></a>Argomenti correlati  
 [Panoramica delle applicazioni dati in Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)  
 Vengono forniti collegamenti ad argomenti relativi alla creazione di applicazioni per la gestione dei dati.  
  
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)  
 Vengono forniti collegamenti ad argomenti che illustrano come usare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per connettere l'applicazione ai dati e creare origini dati per le applicazioni.  
  
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)  
 Vengono forniti collegamenti ad argomenti che illustrano l'utilizzo di modelli dati nell'applicazione, inclusi dataset ed Entity Data Model.  
  
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)  
 Vengono forniti collegamenti ad argomenti che descrivono come caricare dati nell'applicazione.  
  
 [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
 Vengono forniti collegamenti ad argomenti in cui viene spiegato come associare a origini dati controlli Windows Form, controlli WPF e controlli Silverlight.  
  
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)  
 Vengono forniti collegamenti ad argomenti che descrivono come modificare i dati nell'applicazione.  
  
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)  
 Vengono forniti collegamenti ad argomenti in cui viene descritto come aggiungere la convalida alle modifiche dei dati.  
  
 [Salvataggio di dati](../data-tools/saving-data.md)  
 Vengono forniti collegamenti ad argomenti che illustrano come inviare dati aggiornati dall'applicazione a un database o come salvarli in altri formati come XML.  
  
 [Strumenti per l'uso delle origini dati in Visual Studio](http://msdn.microsoft.com/library/1e584c75-900a-49a0-a82a-d19172ef2eb3)  
 Vengono forniti collegamenti ad argomenti relativi agli strumenti che è possibile usare per lavorare con le origini dati in Visual Studio, ad esempio la **Zdroje dat** finestra e ADO.NET Entity Data Model Designer.