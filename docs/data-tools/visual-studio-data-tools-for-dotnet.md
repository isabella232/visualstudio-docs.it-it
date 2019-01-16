---
title: Data tools per .NET
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: 24da256ac835e477465845714cc844ac5bb305d7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53872752"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio data tools per .NET

Visual Studio e .NET Framework forniscono insieme completo di API e supporto degli strumenti per la connessione ai database, modellazione dei dati in memoria e la visualizzazione dei dati nell'interfaccia utente. Le classi di .NET Framework che forniscono funzionalità di accesso ai dati sono dette [ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, insieme ai dati degli strumenti in Visual Studio, è stato progettato principalmente per supportare i database relazionali e XML. Oggi, molti fornitori di database NoSQL, o di terze parti, offrono i provider ADO.NET.

[.NET core](/dotnet/core/) supporta ADO.NET, fatta eccezione per i set di dati e i tipi correlati. Se si è destinati a .NET Core e richiede un livello di mapping relazionale a oggetti (ORM), usare [Entity Framework Core](/ef/core/).

Il diagramma seguente mostra una vista semplificata dell'architettura di base:

![Architettura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Flusso di lavoro tipico

Il flusso di lavoro tipico è il seguente:

1. Installare un database di test o sviluppo nel computer locale. Visualizzare [installazione di sistemi di database, strumenti ed esempi](../data-tools/installing-database-systems-tools-and-samples.md). Se si usa un servizio dati di Azure, questo passaggio non è più necessario.

2. Testare la connessione al database (o servizio o file locale) in Visual Studio. Visualizzare [aggiungere le nuove connessioni](../data-tools/add-new-connections.md).

3. (Facoltativo) Utilizzare gli strumenti per generare e configurare un nuovo modello. I modelli basati su Entity Framework sono incentivazione predefinita per le nuove applicazioni. Il modello, quella che si usa, è l'origine dati con cui interagisce l'applicazione. Il modello risiede logicamente tra il database o del servizio e l'applicazione. Visualizzare [aggiungono nuove origini dati](../data-tools/add-new-data-sources.md).

4. Trascinare l'origine dati dal **Zdroje dat** finestra in un'area di progettazione Windows Form, ASP.NET o Windows Presentation Foundation per generare il codice di associazione dati che verrà visualizzati i dati per l'utente in modo che preferisci. Visualizzare [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Aggiungere codice personalizzato per elementi quali le regole di business, ricerca e la convalida dei dati o per sfruttare i vantaggi della funzionalità personalizzata che espone il database sottostante.

È possibile ignorare il passaggio 3 e programmare un'applicazione .NET per eseguire comandi direttamente a un database, anziché utilizzare un modello. In questo caso, è possibile trovare la relativa documentazione: [ADO.NET](/dotnet/framework/data/adonet/index). Si noti che è comunque possibile usare la **configurazione guidata origine dati** e finestre di progettazione per generare il codice di associazione dati quando si popola gli oggetti in memoria e controlli dell'interfaccia utente di eseguire l'associazione dati a tali oggetti.

## <a name="see-also"></a>Vedere anche

- [Accedere ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)