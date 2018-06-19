---
title: Strumenti di dati di Visual Studio per .NET
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: 2b7fc572541e0c2f0f5aa04c6e676d1e2913ff9f
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2018
ms.locfileid: "33864720"
---
# <a name="visual-studio-data-tools-for-net"></a>Strumenti di dati di Visual Studio per .NET

Visual Studio e .NET Framework forniscono insieme completo di API e gli strumenti di supporto per la connessione a database, modellazione dei dati in memoria e la visualizzazione dei dati nell'interfaccia utente. Le classi di .NET Framework che forniscono funzionalità di accesso ai dati sono note come [ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, insieme ai dati per gli strumenti in Visual Studio, è stato progettato principalmente per supportare i database relazionali e XML. Oggi, molti fornitori di database NoSQL, o di terze parti, offrono provider ADO.NET.

[.NET core](/dotnet/core/) supporta ADO.NET, ad eccezione di set di dati e i tipi correlati. Se si è destinati a .NET Core e richiede un livello di mapping relazionale a oggetti (ORM), utilizzare [Entity Framework Core](/ef/core/).

Il diagramma seguente mostra una visualizzazione semplificata dell'architettura di base:

![Architettura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Flusso di lavoro tipico

Il flusso di lavoro tipico è la seguente:

1. Installare un database di test o di sviluppo nel computer locale. Vedere [installare sistemi di database, strumenti ed esempi](../data-tools/installing-database-systems-tools-and-samples.md). Se si utilizza un servizio dati di Azure, questo passaggio non è più necessario.

2. Verificare la connessione al database (o servizio o un file locale) in Visual Studio. Vedere [aggiungere nuove connessioni](../data-tools/add-new-connections.md).

3. (Facoltativo) Utilizzare gli strumenti per generare e configurare un nuovo modello. Modelli basati su Entity Framework sono incentivazione predefinita per le nuove applicazioni. Il modello, a seconda del valore uno si utilizza, è l'origine dati che l'applicazione interagisce con. Il modello si trova in modo logico tra il database o servizio e l'applicazione. Vedere [aggiungere nuove origini dati](../data-tools/add-new-data-sources.md).

4. Trascinare l'origine dati dal **origini dati** finestra in un'area di progettazione Windows Form, ASP.NET o Windows Presentation Foundation per generare il codice di associazione di dati che consente di visualizzare i dati per l'utente nel modo desiderato. Vedere [associare i controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Aggiungere codice personalizzato per operazioni come le regole di business, ricerca e la convalida dei dati, o per sfruttare i vantaggi di funzionalità personalizzata che espone il database sottostante.

È possibile ignorare il passaggio 3 e un'applicazione .NET per inviare comandi direttamente a un database, anziché utilizzare un modello di programmazione. In questo caso, si troverà la relativa documentazione: [ADO.NET](/dotnet/framework/data/adonet/index). Si noti che è comunque possibile utilizzare la configurazione guidata origine dati e le finestre di progettazione per generare il codice di associazione dati per popolare gli oggetti in memoria e quindi controlli dell'interfaccia utente di eseguire l'associazione dati a tali oggetti.

## <a name="see-also"></a>Vedere anche

- [Accedere ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)