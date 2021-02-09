---
title: Data Tools per .NET
description: Esaminare Visual Studio Data Tools per .NET, che fornisce il supporto per API e strumenti per connettersi ai database, modellare i dati in memoria e visualizzare i dati nell'interfaccia utente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: f0a9609a578deb0c7c1b39a43f45b796b66a55ce
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858215"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio data tools per .NET

Visual Studio e .NET forniscono insieme un ampio supporto di API e strumenti per la connessione ai database, la modellazione dei dati in memoria e la visualizzazione dei dati nell'interfaccia utente. Le classi .NET che forniscono funzionalità di accesso ai dati sono note come [ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, insieme agli strumenti dati in Visual Studio, è stato progettato principalmente per supportare i database relazionali e XML. In questi giorni, molti fornitori di database NoSQL o terze parti offrono provider ADO.NET.

[.NET Core](/dotnet/core/) supporta ADO.NET, eccetto i set di elementi e i tipi correlati. Se la destinazione è .NET Core e si richiede un livello ORM (Object-Relational Mapping), usare [Entity Framework Core](/ef/core/).

Il diagramma seguente mostra una vista semplificata dell'architettura di base:

![Architettura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Flusso di lavoro tipico

Il flusso di lavoro tipico è il seguente:

1. Installare un database di sviluppo o di test nel computer locale. Vedere [installazione di sistemi di database, strumenti ed esempi](../data-tools/installing-database-systems-tools-and-samples.md). Se si usa un servizio dati di Azure, questo passaggio non è necessario.

2. Testare la connessione al database (o al servizio o al file locale) in Visual Studio. Vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).

3. Opzionale Usare gli strumenti di per generare e configurare un nuovo modello. I modelli basati su Entity Framework sono l'indicazione predefinita per le nuove applicazioni. Il modello, a seconda di quale utente si utilizza, è l'origine dati con cui interagisce l'applicazione. Il modello si trova logicamente tra il database o il servizio e l'applicazione. Vedere [aggiungere nuove origini dati](../data-tools/add-new-data-sources.md).

4. Trascinare l'origine dati dalla finestra **origini dati** in un'area di progettazione Windows Form, ASP.NET o Windows Presentation Foundation per generare il codice di data binding che visualizzerà i dati all'utente nel modo specificato. Vedere [associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Aggiungere codice personalizzato per elementi come regole di business, ricerca e convalida dei dati oppure per sfruttare le funzionalità personalizzate esposte dal database sottostante.

È possibile ignorare il passaggio 3 e programmare un'applicazione .NET per inviare comandi direttamente a un database, anziché usare un modello. In questo caso, è possibile trovare la relativa documentazione: [ADO.NET](/dotnet/framework/data/adonet/index). Si noti che è comunque possibile usare la **Configurazione guidata origine dati** e le finestre di progettazione per generare codice di data binding quando si popolano oggetti personalizzati in memoria e quindi si associano i controlli dell'interfaccia utente a tali oggetti.

## <a name="see-also"></a>Vedi anche

- [Accedere ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
