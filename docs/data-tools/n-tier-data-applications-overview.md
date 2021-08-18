---
title: Panoramica delle applicazioni dati a più livelli
description: Leggere una panoramica dell'applicazione dati a più livelli. Chiamate anche applicazioni distribuite o applicazioni multilivello, si tratta di applicazioni dati separate in più livelli.
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 4e713fe3afa88fffee002561bc1ab687be0dcd40
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122075190"
---
# <a name="n-tier-data-applications-overview"></a>Panoramica delle applicazioni dati a più livelli
*Le applicazioni dati a* più livelli sono applicazioni dati separate in *più livelli.* Chiamate anche "applicazioni distribuite" e "applicazioni multilivello", le applicazioni a più livelli separano l'elaborazione in livelli discreti distribuiti tra il client e il server. Quando si sviluppano applicazioni che accedono ai dati, è necessario avere una netta separazione tra i vari livelli che costituiscono l'applicazione.

Una tipica applicazione a più livelli include un livello di presentazione, un livello intermedio e un livello dati. Il modo più semplice per separare i vari livelli in un'applicazione a più livelli è creare progetti discreti per ogni livello che si vuole includere nell'applicazione. Ad esempio, il livello di presentazione potrebbe essere un'applicazione Windows Forms, mentre la logica di accesso ai dati potrebbe essere una libreria di classi che si trova nel livello intermedio. Inoltre, il livello di presentazione potrebbe comunicare con la logica di accesso ai dati nel livello intermedio tramite un servizio, ad esempio un servizio Web. La separazione dei componenti dell'applicazione in livelli aumenta la gestibilità e la manutenibilità dell'applicazione, A tale scopo, è possibile semplificare l'adozione di nuove tecnologie che possono essere applicate a un singolo livello senza dover riprogettare l'intera soluzione. Inoltre, le applicazioni a più livelli archiviano in genere informazioni riservate nel livello intermedio, che mantiene l'isolamento dal livello di presentazione.

Visual Studio contiene diverse funzionalità che consentono agli sviluppatori di creare applicazioni a più livelli:

- Il set di dati fornisce una proprietà **Project DataSet** che consente di separare il set di dati (livello entità dati) e gli oggetti TableAdapter (livello di accesso ai dati) in progetti discreti.

- Gli [LINQ to SQL disponibili in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) le impostazioni per generare dataContext e le classi di dati in spazi dei nomi separati. Ciò consente la separazione logica dei livelli di accesso ai dati e di entità dati.

- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) fornisce il <xref:System.Data.Linq.Table%601.Attach%2A> metodo che consente di riunire DataContext da livelli diversi in un'applicazione. Per altre informazioni, vedere Applicazioni remote e a più livelli [con LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql).

## <a name="presentation-tier"></a>Livello presentazione
Il *livello di presentazione* è il livello in cui gli utenti interagiscono con un'applicazione. Spesso contiene anche logica di applicazione aggiuntiva. Di seguito sono riportati i componenti tipici del livello presentazione:

- Componenti di data binding, ad esempio <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator> .

- Rappresentazioni di oggetti di dati, ad esempio [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) di entità da usare nel livello di presentazione.

Il livello di presentazione accede in genere al livello intermedio usando un riferimento al servizio , ad esempio un'applicazione Windows Communication Foundation Services e WCF Data Services [nell Visual Studio app.](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) Il livello presentazione non accede direttamente al livello dati. Il livello presentazione comunica con il livello dati tramite il componente di accesso ai dati nel livello intermedio.

## <a name="middle-tier"></a>Livello intermedio
Il *livello intermedio* è il livello utilizzato dal livello presentazione e dal livello dati per comunicare tra loro. Di seguito sono riportati i componenti tipici del livello intermedio:

- Logica di business, ad esempio regole di business e convalida dei dati.

- Componenti e logica di accesso ai dati, ad esempio:

  - [TableAdapter e](create-and-configure-tableadapters.md) [DataAdapter e DataReader](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

  - Rappresentazioni di oggetti di dati, [ad](/dotnet/framework/data/adonet/sql/linq/index) esempio LINQ to SQL di entità.

  - Servizi dell'applicazione comuni, ad esempio autenticazione, autorizzazione e personalizzazione.

La figura seguente illustra le funzionalità e le tecnologie disponibili in Visual Studio e dove possono essere adattate al livello intermedio di un'applicazione a più livelli.

![Componenti di livello ](../data-tools/media/ntiermid.png) intermedio Livello intermedio

Il livello intermedio si connette in genere al livello dati usando una connessione dati. Questa connessione dati viene in genere archiviata nel componente di accesso ai dati.

## <a name="data-tier"></a>Livello dati
Il *livello dati* è fondamentalmente il server su cui vengono archiviati i dati di un'applicazione (ad esempio, un server che esegue SQL Server).

La figura seguente illustra le funzionalità e le tecnologie disponibili in Visual Studio e dove possono essere adattate al livello dati di un'applicazione a più livelli.

![Componenti del livello dati ](../data-tools/media/ntierdatatier.png) Livello dati

Non è possibile accedere al livello dati direttamente dal client nel livello presentazione. Al contrario, il componente di accesso ai dati nel livello intermedio viene usato per la comunicazione tra i livelli presentazione e dati.

## <a name="help-for-n-tier-development"></a>Guida per lo sviluppo a più livelli
Negli argomenti seguenti vengono fornite informazioni sull'uso di applicazioni a più livelli:

[Separare set di dati e TableAdapter in progetti diversi](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

[Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

[Applicazioni remote e a più livelli con LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: Creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [Aggiornamento gerarchico](../data-tools/hierarchical-update.md)
- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
- [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
