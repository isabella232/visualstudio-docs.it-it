---
title: Cenni preliminari sull'applicazione dati a più livelli
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 995328205e99117f68050833853ada76f06eb4c8
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67821894"
---
# <a name="n-tier-data-applications-overview"></a>Panoramica delle applicazioni dati a più livelli
*A più livelli* le applicazioni di dati sono le applicazioni di dati che sono separate in più *livelli*. Noto anche come "applicazioni multilivello" e "applicazioni distribuite", le applicazioni a più livelli diversi in livelli discreti che vengono distribuite tra il client e server di elaborazione. Quando si sviluppano applicazioni che accedono ai dati, si deve avere una netta separazione tra i vari livelli che costituiscono l'applicazione.

Una tipica applicazione a più livelli include un livello di presentazione, un livello intermedio e un livello dati. Il modo più semplice per separare i vari livelli in un'applicazione a più livelli è possibile creare progetti discreti per ogni livello che si desidera includere nell'applicazione. Ad esempio, il livello di presentazione può essere un'applicazione Windows Forms, mentre la logica di accesso ai dati potrebbe essere una libreria di classi che si trova nel livello intermedio. Inoltre, il livello di presentazione può comunicare con la logica di accesso ai dati nel livello intermedio tramite un servizio, ad esempio un servizio. La separazione dei componenti dell'applicazione in livelli aumenta la gestibilità e la manutenibilità dell'applicazione, Ciò avviene mediante l'adozione semplificata di nuove tecnologie che possono essere applicati a un singolo livello senza la necessità di riprogettare l'intera soluzione. Inoltre, le applicazioni a più livelli in genere archiviano informazioni riservate nel livello intermedio, che mantiene isolamento dal livello di presentazione.

Visual Studio contiene diverse funzionalità per aiutare gli sviluppatori di creare applicazioni a più livelli:

- Il set di dati fornisce una **DataSetProject** proprietà che consente di separare il set di dati (il livello di entità di dati) e gli oggetti TableAdapter (livello di accesso ai dati) in progetti discreti.

- Il [gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) fornisce le impostazioni per generare le classi DataContext e di dati in diversi spazi dei nomi. In questo modo la separazione logica dei livelli di entità di data e l'accesso ai dati.

- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) fornisce il <xref:System.Data.Linq.Table%601.Attach%2A> metodo che consente di raggruppare la proprietà DataContext da livelli diversi in un'applicazione. Per altre informazioni, vedere [a più livelli e le applicazioni remote con LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql).

## <a name="presentation-tier"></a>Livello di presentazione
Il *livello di presentazione* è il livello in cui gli utenti interagiscono con un'applicazione. Spesso contiene la logica dell'applicazione aggiuntivi anche. Componenti del livello presentazione tipici includono quanto segue:

- Data binding, componenti, ad esempio la <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.

- Oggetto rappresentazioni dei dati, ad esempio [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) le classi di entità per l'uso al livello presentazione.

Il livello di presentazione accede in genere il livello intermedio con un riferimento al servizio (ad esempio, un [servizi di Windows Communication Foundation e WCF Data Services in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) applicazione). Il livello di presentazione non accede direttamente al livello dati. Il livello di presentazione comunica con il livello dati tramite il componente di accesso ai dati nel livello intermedio.

## <a name="middle-tier"></a>Livello intermedio
Il *livello intermedio* viene usato il livello di presentazione e i dati di livello consente di comunicare tra loro. I componenti di livello intermedio tipici includono quanto segue:

- Logica di business, ad esempio la convalida di regole e dati business.

- Componenti di accesso ai dati e per la logica, come il seguente:

  - [Gli oggetti TableAdapter](create-and-configure-tableadapters.md) e [DataAdapter e DataReader](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

  - Oggetto rappresentazioni dei dati, ad esempio [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) le classi di entità.

  - Servizi di applicazione comuni, ad esempio autenticazione, autorizzazione e la personalizzazione.

La figura seguente mostra le funzionalità e le tecnologie disponibili in Visual Studio e in cui che potrebbe essere appropriato per il livello intermedio di un'applicazione a più livelli.

![Componenti di livello intermedio](../data-tools/media/ntiermid.png) livello intermedio

Il livello intermedio in genere si connette al livello dati tramite una connessione dati. Questa connessione dati viene in genere archiviata nel componente di accesso di dati.

## <a name="data-tier"></a>Livello dati
Il *livello dati* è fondamentalmente il server che archivia i dati di un'applicazione (ad esempio, un server che esegue SQL Server).

La figura seguente mostra le funzionalità e le tecnologie disponibili in Visual Studio e in cui che potrebbe essere appropriato per il livello di dati di un'applicazione a più livelli.

![I componenti livello dati](../data-tools/media/ntierdatatier.png) livello dati

Il livello dati non sono accessibili direttamente dal client al livello presentazione. Al contrario, il componente di accesso ai dati nel livello intermedio viene utilizzato per la comunicazione tra i livelli di dati e di presentazione.

## <a name="help-for-n-tier-development"></a>Guida per lo sviluppo a n livelli
Gli argomenti seguenti forniscono informazioni sull'utilizzo delle applicazioni a più livelli:

[Separare set di dati e TableAdapter in progetti diversi](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

[Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

[Applicazioni a più livelli e remote con LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
