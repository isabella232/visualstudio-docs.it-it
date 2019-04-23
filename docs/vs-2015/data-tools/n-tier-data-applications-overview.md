---
title: Panoramica delle applicazioni dati a più livelli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 532781a2e816120dabfe2bec61059955cd0c82a6
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658123"
---
# <a name="n-tier-data-applications-overview"></a>Cenni preliminari sull'applicazione dati a più livelli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N-applicazioni dati a livelli * sono applicazioni di dati che sono separate in più *livelli*. Noto anche come "applicazioni multilivello" e "applicazioni distribuite", le applicazioni a più livelli diversi in livelli discreti che vengono distribuite tra il client e server di elaborazione. Quando si sviluppano applicazioni che accedono ai dati, si deve avere una netta separazione tra i vari livelli che costituiscono l'applicazione.  
  
 Una tipica applicazione a più livelli include un livello di presentazione, un livello intermedio e un livello dati. Il modo più semplice per separare i vari livelli in un'applicazione a più livelli è possibile creare progetti discreti per ogni livello che si desidera includere nell'applicazione. Ad esempio, il livello di presentazione può essere un'applicazione Windows Forms, mentre la logica di accesso ai dati potrebbe essere una libreria di classi che si trova nel livello intermedio. Inoltre, il livello di presentazione può comunicare con la logica di accesso ai dati nel livello intermedio tramite un servizio, ad esempio un servizio. La separazione dei componenti dell'applicazione in livelli aumenta la gestibilità e la manutenibilità dell'applicazione, Ciò avviene mediante l'adozione semplificata di nuove tecnologie che possono essere applicati a un singolo livello senza la necessità di riprogettare l'intera soluzione. Inoltre, le applicazioni a più livelli in genere archiviano informazioni riservate nel livello intermedio, che mantiene isolamento dal livello di presentazione.  
  
 Visual Studio contiene diverse funzionalità per aiutare gli sviluppatori di creare applicazioni a più livelli:  
  
-   La finestra di progettazione set di dati fornisce una **DataSetProject** proprietà che consente di separare il set di dati (il livello di entità di dati) e `TableAdapter`s (livello di accesso ai dati) in progetti discreti.  
  
-   Il [strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornisce le impostazioni per generare le classi DataContext e di dati in diversi spazi dei nomi. In questo modo la separazione logica dei livelli di entità di data e l'accesso ai dati.  
  
-   [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) fornisce il <xref:System.Data.Linq.Table%601.Attach%2A> metodo che consente di raggruppare la proprietà DataContext da livelli diversi in un'applicazione. Per altre informazioni, vedere [a più livelli e le applicazioni Remote con LINQ to SQL](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598).  
  
## <a name="presentation-tier"></a>Livello di presentazione  
 Il *livello di presentazione* è il livello in cui gli utenti interagiscono con un'applicazione. Spesso contiene la logica dell'applicazione aggiuntivi anche. Componenti del livello presentazione tipici includono quanto segue:  
  
- Data binding, componenti, ad esempio la <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
- Oggetto rappresentazioni dei dati, ad esempio [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) le classi di entità per l'uso al livello presentazione.  
  
  Il livello di presentazione accede in genere il livello intermedio con un riferimento al servizio (ad esempio, un [servizi di Windows Communication Foundation e WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) applicazione). Il livello di presentazione non accede direttamente al livello dati. Il livello di presentazione comunica con il livello dati tramite il componente di accesso ai dati nel livello intermedio.  
  
## <a name="middle-tier"></a>Livello intermedio  
 Il *livello intermedio* viene usato il livello di presentazione e i dati di livello consente di comunicare tra loro. I componenti di livello intermedio tipici includono quanto segue:  
  
- Logica di business, ad esempio la convalida di regole e dati business.  
  
- Componenti di accesso ai dati e per la logica, come il seguente:  
  
  -   [Gli oggetti TableAdapter](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) e [DataAdapter e DataReader](http://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74).  
  
  -   Oggetto rappresentazioni dei dati, ad esempio [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) le classi di entità.  
  
  -   Servizi di applicazione comuni, ad esempio autenticazione, autorizzazione e la personalizzazione.  
  
  La figura seguente mostra le funzionalità e le tecnologie disponibili in Visual Studio e in cui che potrebbe essere appropriato per il livello intermedio di un'applicazione a più livelli.  
  
  ![Componenti di livello intermedio](../data-tools/media/ntiermid.png "NtierMid")  
  Livello intermedio  
  
  Il livello intermedio in genere si connette al livello dati tramite una connessione dati. Questa connessione dati viene in genere archiviata nel componente di accesso di dati.  
  
## <a name="data-tier"></a>Livello dati  
 Il *livello dati* è fondamentalmente il server che archivia i dati di un'applicazione (ad esempio, un server che esegue [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]).  
  
 La figura seguente mostra le funzionalità e le tecnologie disponibili in Visual Studio e in cui che potrebbe essere appropriato per il livello di dati di un'applicazione a più livelli.  
  
 ![I componenti livello dati](../data-tools/media/ntierdatatier.png "ntierdatatier")  
Livello dati  
  
 Il livello dati non sono accessibili direttamente dal client al livello presentazione. Al contrario, il componente di accesso ai dati nel livello intermedio viene utilizzato per la comunicazione tra i livelli di dati e di presentazione.  
  
## <a name="help-for-n-tier-development"></a>Guida per lo sviluppo a N livelli  
 Gli argomenti seguenti forniscono informazioni sull'utilizzo delle applicazioni a più livelli:  
  
 [Separare set di dati e TableAdapter in progetti diversi](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)  
  
 [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)  
  
 [Procedura dettagliata: Aggiunta della convalida a un'applicazione dati a più livelli](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265)  
  
 [Applicazioni a più livelli e remote con LINQ to SQL](http://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)  
  
## <a name="see-also"></a>Vedere anche  
 <xref:System.Data.Linq.ITable.Attach%2A>   
 [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)   
 [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)   
 [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
