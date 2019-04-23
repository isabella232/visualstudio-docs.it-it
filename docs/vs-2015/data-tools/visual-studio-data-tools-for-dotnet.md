---
title: Visual Studio data tools per .NET | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b42617892e377dcf750e9f5cafc914759b7d0c13
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60110926"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio data tools per .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio e .NET Framework forniscono insieme completo di API e supporto degli strumenti per la connessione ai database, modellazione dei dati in memoria e la visualizzazione dei dati nell'interfaccia utente.  Le classi di .NET Framework che forniscono funzionalità di accesso ai dati sono dette [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). ADO.NET, insieme ai dati degli strumenti in Visual Studio, è stato originariamente progettato principalmente per supportare i database relazionali e XML. Oggi, molti fornitori di database NoSQL, o di terze parti, offrono i provider ADO.NET.  
  
 Visual Studio 2015 Update 2 include gli aggiornamenti più recenti di [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), che abilitano il supporto per le funzionalità più recenti di Azure [Database SQL](https://azure.microsoft.com/services/sql-database/) e [SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016). [.NET core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project) supporta ADO.NET, fatta eccezione per i set di dati e i tipi correlati. Se si è destinati a .NET Core e richiede un livello di mapping relazionale a oggetti (ORM), usare [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).  
  
 Il diagramma seguente mostra una vista semplificata dell'architettura di base:  
  
 ![Architettura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata diagramma dell'architettura di ADO.NET")  
  
 Il flusso di lavoro tipico è il seguente:  
  
1. Installare un database di test o sviluppo nel computer locale. Visualizzare [installazione di sistemi di database, strumenti ed esempi](../data-tools/installing-database-systems-tools-and-samples.md). Se si usa un servizio dati di Azure, questo passaggio non è più necessario.  
  
2. Testare la connessione al database (o servizio o file locale) in Visual Studio. Visualizzare [aggiungere le nuove connessioni](../data-tools/add-new-connections.md).  
  
3. (Facoltativo) Utilizzare gli strumenti per generare e configurare un nuovo modello. I modelli basati su Entity Framework sono incentivazione predefinita per le nuove applicazioni. Il modello, quella che si usa, è l'origine dati che l'applicazione interagisce con. Il modello risiede logicamente tra il database o del servizio e l'applicazione.  Visualizzare [aggiungono nuove origini dati](../data-tools/add-new-data-sources.md).  
  
4. Trascinare l'origine dati dal **Zdroje dat** finestra in un'area di progettazione Windows Form, ASP.NET o Windows Presentation Foundation per generare il codice di associazione dati che verrà visualizzati i dati per l'utente in modo che preferisci. Visualizzare [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
5. Aggiungere codice personalizzato per elementi quali le regole di business, ricerca e la convalida dei dati o per sfruttare i vantaggi della funzionalità personalizzata che espone il database sottostante.  
  
   È possibile ignorare il passaggio 3 e programmare un'applicazione .NET per eseguire comandi direttamente a un database, anziché utilizzare un modello. In questo caso, è possibile trovare la relativa documentazione: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Si noti che è comunque possibile usare la configurazione guidata origine dati e le finestre di progettazione per generare il codice di associazione dati quando si popola gli oggetti in memoria e controlli dell'interfaccia utente di eseguire l'associazione dati a tali oggetti.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
  
- [Creare un'applicazione dati semplice tramite ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)  
  
- [Aggiungere nuove connessioni](../data-tools/add-new-connections.md)  
  
- [Aggiungi nuova origine dati](../data-tools/add-new-data-sources.md)  
  
- [Strumenti di Entity Data Model in Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)  
  
- [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
  
- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
  
- [Risorse aggiuntive per la risoluzione dei problemi di accesso ai dati](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)  
  
- [Creazione e gestione di database e applicazioni di livello dati in Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)  
  
- [Risorse aggiuntive per la risoluzione dei problemi di accesso ai dati](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
