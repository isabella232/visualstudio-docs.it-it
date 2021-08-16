---
title: Strumenti dati per .NET
description: Esaminare Visual Studio di dati per .NET, che offrono supporto per API e strumenti per connettersi ai database, modellare i dati in memoria e visualizzare i dati nell'interfaccia utente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: e04665d4cf05c8440681ebffbf2223ef1054fcced6d3608aa3c289546e8226c7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346616"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio data tools per .NET

Visual Studio e .NET offrono ampio supporto per API e strumenti per la connessione ai database, la modellazione dei dati in memoria e la visualizzazione dei dati nell'interfaccia utente. Le classi .NET che forniscono funzionalità di accesso ai dati sono note [come ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, insieme agli strumenti per i dati in Visual Studio, è stato progettato principalmente per supportare database relazionali e XML. Oggi, molti fornitori di database NoSQL o terze parti offrono ADO.NET provider.

[.NET Core supporta](/dotnet/core/) ADO.NET, ad eccezione dei set di dati e dei relativi tipi correlati. Se la destinazione è .NET Core e è necessario un livello ORM (Object-Relational Mapping), usare [Entity Framework Core](/ef/core/).

Il diagramma seguente mostra una visualizzazione semplificata dell'architettura di base:

![Architettura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Flusso di lavoro tipico

Il flusso di lavoro tipico è il seguente:

1. Installare un database di sviluppo o di test nel computer locale. Vedere [Installazione di sistemi di database, strumenti ed esempi.](../data-tools/installing-database-systems-tools-and-samples.md) Se si usa un servizio dati di Azure, questo passaggio non è necessario.

2. Testare la connessione al database (o al servizio o al file locale) in Visual Studio. Vedere [Aggiungere nuove connessioni.](../data-tools/add-new-connections.md)

3. (Facoltativo) Usare gli strumenti per generare e configurare un nuovo modello. I modelli basati Entity Framework sono la raccomandazione predefinita per le nuove applicazioni. Il modello, indipendentemente da quello in uso, è l'origine dati con cui interagisce l'applicazione. Il modello si trova logicamente tra il database o il servizio e l'applicazione. Vedere [Aggiungere nuove origini dati.](../data-tools/add-new-data-sources.md)

4. Trascinare l'origine  dati dalla finestra Origini dati in un'area di progettazione Windows Forms, ASP.NET o Windows Presentation Foundation per generare il codice di associazione dati che visualizza i dati all'utente nel modo specificato. Vedere [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Aggiungere codice personalizzato per elementi come regole business, ricerca e convalida dei dati o per sfruttare le funzionalità personalizzate espore dal database sottostante.

È possibile ignorare il passaggio 3 e programmare un'applicazione .NET per mettere comandi direttamente in un database, anziché usare un modello. In questo caso, è possibile trovare la relativa documentazione: [ADO.NET](/dotnet/framework/data/adonet/index). Si noti che è  comunque possibile usare la Configurazione guidata origine dati e le finestre di progettazione per generare codice di data binding quando si popolano i propri oggetti in memoria e quindi si associano i controlli dell'interfaccia utente a tali oggetti.

## <a name="see-also"></a>Vedi anche

- [Accedere ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
