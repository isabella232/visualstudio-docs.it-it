---
title: Uso di un modello concettuale (WCF Data Services)
description: Usare un modello concettuale in WCF Data Services. Eseguire query sui dati tramite oggetti invece di eseguire la conversione tra schemi di database e modelli a oggetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], querying a service
- data [Visual Studio], LINQ to Entities
- data [Visual Studio], querying an EDM
ms.assetid: 2cd873cf-b010-49f2-a278-bb1277aaa934
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 84c5ae1cf5bff93389477071892aa420081731e9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631013"
---
# <a name="work-with-a-conceptual-model-wcf-data-services"></a>Usare un modello concettuale (WCF Data Services)

Quando si usa un modello concettuale per descrivere i dati in un database, è possibile eseguire query sui dati tramite gli oggetti anziché traslare avanti e indietro tra uno schema del database e un modello a oggetti.

È possibile utilizzare i modelli concettuali con le applicazioni Data Services WCF. Negli argomenti seguenti viene illustrato come eseguire query sui dati tramite un modello concettuale.

| Argomento | Descrizione |
| - | - |
| [Procedura: Eseguire query del servizio dati](/dotnet/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services) | Illustra come eseguire query su un servizio dati da un'applicazione .NET. |
| [Procedura: determinare Project risultati della query](/dotnet/framework/data/wcf/how-to-project-query-results-wcf-data-services) | Viene illustrato come ridurre la quantità di dati restituiti tramite una query del servizio dati. |

Quando si usa un modello concettuale, è possibile definire il tipo di dati validi nel linguaggio corrispondente al dominio. È possibile definire dati validi nel modello oppure aggiungere la convalida alle operazioni eseguite su un'entità o un servizio dati.

Negli argomenti riportati di seguito viene illustrato come aggiungere la convalida alle applicazioni WCF Data Services.

|Argomento|Descrizione|
|-----------|-----------------|
|[Procedura: Intercettare i messaggi del servizio dati](/dotnet/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services)|Viene illustrato come aggiungere la convalida a un'operazione del servizio dati.|

 Gli argomenti seguenti illustrano come creare, aggiornare ed eliminare dati eseguendo operazioni sulle entità.

|Argomento|Descrizione|
|-----------|-----------------|
|[Procedura: Aggiungere, modificare ed eliminare entità](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)|Illustra come creare, aggiornare ed eliminare dati di entità in un servizio dati.|
|[Procedura: Definire relazioni tra entità](/dotnet/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services)|Viene illustrato come creare o modificare relazioni in un servizio dati.|

## <a name="see-also"></a>Vedi anche

- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Esecuzione di query sul servizio dati](/dotnet/framework/data/wcf/querying-the-data-service-wcf-data-services)
