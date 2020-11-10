---
title: Panoramica delle applicazioni dati a più livelli
description: Leggi una panoramica dell'applicazione dati a più livelli. Dette anche applicazioni distribuite o applicazioni multilivello, si tratta di applicazioni dati separate in molti livelli.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ea1ab222868df6ff1b22eee7827e1edd3978a88e
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436211"
---
# <a name="n-tier-data-applications-overview"></a>Panoramica delle applicazioni dati a più livelli
Le applicazioni dati a più *livelli* sono applicazioni dati separate in più *livelli*. Dette anche "applicazioni distribuite" e "applicazioni a più livelli", le applicazioni a più livelli dipendono dall'elaborazione in livelli discreti distribuiti tra il client e il server. Quando si sviluppano applicazioni che accedono ai dati, è necessario avere una netta separazione tra i vari livelli che costituiscono l'applicazione.

Una tipica applicazione a più livelli include un livello di presentazione, un livello intermedio e un livello dati. Il modo più semplice per separare i vari livelli in un'applicazione a più livelli consiste nel creare progetti discreti per ogni livello che si desidera includere nell'applicazione. Ad esempio, il livello di presentazione potrebbe essere un Windows Forms Application, mentre la logica di accesso ai dati potrebbe essere una libreria di classi che si trova nel livello intermedio. Inoltre, il livello di presentazione potrebbe comunicare con la logica di accesso ai dati nel livello intermedio tramite un servizio, ad esempio un servizio Web. La separazione dei componenti dell'applicazione in livelli aumenta la gestibilità e la manutenibilità dell'applicazione, Questo consente di semplificare l'adozione di nuove tecnologie che possono essere applicate a un singolo livello senza la necessità di riprogettare l'intera soluzione. Inoltre, le applicazioni a più livelli in genere archiviano informazioni riservate nel livello intermedio, che mantiene l'isolamento dal livello di presentazione.

Visual Studio contiene diverse funzionalità che consentono agli sviluppatori di creare applicazioni a più livelli:

- Il set di dati fornisce una proprietà del **progetto DataSet** che consente di separare il set di dati (livello entità di dati) e i TableAdapter (livello di accesso ai dati) in progetti discreti.

- Gli [strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) forniscono le impostazioni per generare le classi di dati e DataContext in spazi dei nomi distinti. Ciò consente la separazione logica dei livelli di accesso ai dati e di entità dati.

- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) fornisce il <xref:System.Data.Linq.Table%601.Attach%2A> metodo che consente di riunire DataContext da livelli diversi in un'applicazione. Per altre informazioni, vedere [applicazioni a più livelli e remote con LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql).

## <a name="presentation-tier"></a>Livello presentazione
Il *livello presentazione* è il livello in cui gli utenti interagiscono con un'applicazione. Spesso contiene anche una logica dell'applicazione aggiuntiva. I componenti del livello presentazione tipici includono i seguenti:

- Componenti di data binding, ad esempio <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator> .

- Rappresentazioni di oggetti dei dati, ad esempio [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) classi di entità da utilizzare nel livello di presentazione.

Il livello di presentazione accede in genere al livello intermedio usando un riferimento al servizio (ad esempio, un [Windows Communication Foundation servizi e WCF Data Services nell'applicazione di Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) ). Il livello di presentazione non accede direttamente al livello dati. Il livello presentazione comunica con il livello dati tramite il componente di accesso ai dati nel livello intermedio.

## <a name="middle-tier"></a>Livello intermedio
Il livello *intermedio* è quello usato dal livello presentazione e dal livello dati per comunicare tra loro. I componenti di livello intermedio tipici includono i seguenti:

- Logica di business, ad esempio regole di business e convalida dei dati.

- Componenti e logica di accesso ai dati, come i seguenti:

  - [Oggetti TableAdapter](create-and-configure-tableadapters.md) e [DataAdapter e DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

  - Rappresentazioni di oggetti dei dati, ad esempio [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) classi di entità.

  - Servizi applicativi comuni, ad esempio autenticazione, autorizzazione e personalizzazione.

Nella figura seguente sono illustrate le funzionalità e le tecnologie disponibili in Visual Studio e la posizione in cui possono rientrare nel livello intermedio di un'applicazione a più livelli.

![Livello intermedio dei componenti di livello intermedio ](../data-tools/media/ntiermid.png)

Il livello intermedio si connette in genere al livello dati utilizzando una connessione dati. Questa connessione dati viene in genere archiviata nel componente di accesso ai dati.

## <a name="data-tier"></a>Livello dati
Il *livello dati* è fondamentalmente il server su cui vengono archiviati i dati di un'applicazione (ad esempio, un server che esegue SQL Server).

Nella figura seguente sono illustrate le funzionalità e le tecnologie disponibili in Visual Studio e la posizione in cui possono adattarsi al livello dati di un'applicazione a più livelli.

![Livello dati componenti livello dati ](../data-tools/media/ntierdatatier.png)

Non è possibile accedere al livello dati direttamente dal client nel livello di presentazione. Al contrario, il componente di accesso ai dati nel livello intermedio viene usato per la comunicazione tra i livelli di presentazione e di dati.

## <a name="help-for-n-tier-development"></a>Guida per lo sviluppo a più livelli
Negli argomenti seguenti vengono fornite informazioni sull'utilizzo di applicazioni a più livelli:

[Separare set di dati e TableAdapter in progetti diversi](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

[Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

[Applicazioni a più livelli e remote con LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
