---
title: Strumenti dati per .NET
description: Esaminare Visual Studio strumenti dati per .NET, che forniscono supporto per API e strumenti per connettersi ai database, modellare i dati in memoria e visualizzare i dati nell'interfaccia utente.
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
ms.openlocfilehash: adf70d81747cfee833c996acaaecf6b1009f6fed
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631074"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio data tools per .NET

Visual Studio e .NET offrono un ampio supporto per API e strumenti per la connessione ai database, la modellazione dei dati in memoria e la visualizzazione dei dati nell'interfaccia utente. Le classi .NET che forniscono funzionalità di accesso ai dati sono note [come ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, insieme agli strumenti di dati in Visual Studio, è stato progettato principalmente per supportare i database relazionali e XML. In questi giorni, molti fornitori di database NoSQL o terze parti offrono ADO.NET provider.

[.NET Core](/dotnet/core/) supporta ADO.NET, ad eccezione dei set di dati e dei relativi tipi correlati. Se si usa .NET Core come destinazione e si richiede un livello ORM (Object-Relational Mapping), usare [Entity Framework Core](/ef/core/).

Il diagramma seguente illustra una visualizzazione semplificata dell'architettura di base:

![Architettura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Flusso di lavoro tipico

Il flusso di lavoro tipico è il seguente:

1. Installare un database di sviluppo o test nel computer locale. Vedere [Installazione di sistemi di database, strumenti ed esempi.](../data-tools/installing-database-systems-tools-and-samples.md) Se si usa un servizio dati di Azure, questo passaggio non è necessario.

2. Testare la connessione al database (o al servizio o al file locale) in Visual Studio. Vedere [Aggiungere nuove connessioni.](../data-tools/add-new-connections.md)

3. (Facoltativo) Usare gli strumenti per generare e configurare un nuovo modello. I modelli basati Entity Framework sono la raccomandazione predefinita per le nuove applicazioni. Il modello, indipendentemente dall'utente, è l'origine dati con cui interagisce l'applicazione. Il modello si trova logicamente tra il database o il servizio e l'applicazione. Vedere [Aggiungere nuove origini dati.](../data-tools/add-new-data-sources.md)

4. Trascinare l'origine  dati dalla finestra Origini dati in un'area di progettazione Windows Forms, ASP.NET o Windows Presentation Foundation per generare il codice di data binding che visualizza i dati all'utente nel modo specificato. Vedere [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Aggiungere codice personalizzato per elementi quali regole di business, ricerca e convalida dei dati o per sfruttare le funzionalità personalizzate esporrà il database sottostante.

È possibile ignorare il passaggio 3 e programmare un'applicazione .NET per eseguire comandi direttamente a un database, anziché usare un modello. In questo caso, è possibile trovare la relativa documentazione: [ADO.NET](/dotnet/framework/data/adonet/index). Si noti che è  comunque possibile usare la Configurazione guidata origine dati e le finestre di progettazione per generare codice di associazione dati quando si popolano i propri oggetti in memoria e quindi si associano i controlli dell'interfaccia utente a tali oggetti.

## <a name="see-also"></a>Vedi anche

- [Accedere ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
