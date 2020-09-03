---
title: Visual Studio Data Tools per .NET | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d591595c65f00e0198ded9492ae0b8399e363e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670105"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio data tools per .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio e i .NET Framework insieme offrono un ampio supporto di API e strumenti per la connessione ai database, la modellazione dei dati in memoria e la visualizzazione dei dati nell'interfaccia utente.  Le classi .NET Framework che forniscono funzionalità di accesso ai dati sono note come [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). ADO.NET, insieme agli strumenti dati in Visual Studio, è stato originariamente progettato principalmente per supportare i database relazionali e XML. In questi giorni, molti fornitori di database NoSQL o terze parti offrono provider ADO.NET.

 Visual Studio 2015 Update 2 include gli aggiornamenti più recenti di            [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), che abilitano il supporto per le funzionalità più recenti nel [database SQL](https://azure.microsoft.com/services/sql-database/) di Azure e [SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016). [.NET Core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project) supporta ADO.NET, eccetto i set di elementi e i tipi correlati. Se si fa riferimento a .NET Core e si richiede un livello ORM (Object-Relational Mapping), usare [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).

 Il diagramma seguente mostra una vista semplificata dell'architettura di base:

 ![Architettura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png "Diagramma dell'architettura di raddata ADO.NET")

 Il flusso di lavoro tipico è il seguente:

1. Installare un database di sviluppo o di test nel computer locale. Vedere [installazione di sistemi di database, strumenti ed esempi](../data-tools/installing-database-systems-tools-and-samples.md). Se si usa un servizio dati di Azure, questo passaggio non è necessario.

2. Testare la connessione al database (o al servizio o al file locale) in Visual Studio. Vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).

3. Opzionale Usare gli strumenti di per generare e configurare un nuovo modello. I modelli basati su Entity Framework sono l'indicazione predefinita per le nuove applicazioni. Il modello, indipendentemente da quello usato, è l'origine dati con cui interagisce l'applicazione. Il modello si trova logicamente tra il database o il servizio e l'applicazione.  Vedere [aggiungere nuove origini dati](../data-tools/add-new-data-sources.md).

4. Trascinare l'origine dati dalla finestra **origini dati** in un'area di progettazione Windows Forms, ASP.NET o Windows Presentation Foundation per generare il codice di data binding che visualizzerà i dati all'utente nel modo specificato. Vedere [associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Aggiungere codice personalizzato per elementi come regole di business, ricerca e convalida dei dati oppure per sfruttare le funzionalità personalizzate esposte dal database sottostante.

   È possibile ignorare il passaggio 3 e programmare un'applicazione .NET per inviare comandi direttamente a un database, anziché usare un modello. In questo caso, è possibile trovare la relativa documentazione: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Si noti che è comunque possibile usare la configurazione guidata origine dati e le finestre di progettazione per generare codice di data binding quando si popolano oggetti personalizzati in memoria e quindi si associano i controlli dell'interfaccia utente a tali oggetti.

## <a name="in-this-section"></a>Contenuto della sezione

- [Creare un'applicazione dati semplice tramite ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)

- [Aggiungere nuove connessioni](../data-tools/add-new-connections.md)

- [Aggiungi nuova origine dati](../data-tools/add-new-data-sources.md)

- [Strumenti di Entity Data Model in Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)

- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)

- [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

- [Risorse aggiuntive per la risoluzione dei problemi di accesso ai dati](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- [Creazione e gestione di database e applicazioni di livello dati in Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)

- [Risorse aggiuntive per la risoluzione dei problemi di accesso ai dati](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

## <a name="see-also"></a>Vedere anche
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
