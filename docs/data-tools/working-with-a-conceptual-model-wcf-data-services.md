---
title: Utilizzo di un modello concettuale (WCF Data Services)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], querying a service
- data [Visual Studio], LINQ to Entities
- data [Visual Studio], querying an EDM
ms.assetid: 2cd873cf-b010-49f2-a278-bb1277aaa934
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: cae74c50ecd99716cf26eae2b7defcadf03fecbf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862972"
---
# <a name="work-with-a-conceptual-model-wcf-data-services"></a>Usare un modello concettuale (WCF Data Services)

Quando si usa un modello concettuale per descrivere i dati in un database, è possibile eseguire query sui dati tramite gli oggetti invece di dover tradurre avanti e indietro tra uno schema di database e un modello a oggetti.

 È possibile utilizzare i modelli concettuali con le applicazioni Data Services WCF. Gli argomenti seguenti illustrano come eseguire query sui dati tramite un modello concettuale.


| Argomento | Descrizione |
| - | - |
| [Procedura: eseguire query sul servizio dati](/dotnet/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services) | Viene illustrato come eseguire query su un servizio dati da un [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] dell'applicazione. |
| [Procedura: proiettare risultati di query](/dotnet/framework/data/wcf/how-to-project-query-results-wcf-data-services) | Viene illustrato come ridurre la quantità di dati restituiti tramite una query del servizio dati. |

 Quando si usa un modello concettuale, è possibile definire il tipo di dati è valido nella lingua corrispondente al dominio. È possibile definire dati validi nel modello oppure è possibile aggiungere la convalida per le operazioni eseguite su un'entità o un servizio dati.

 Negli argomenti riportati di seguito viene illustrato come aggiungere la convalida alle applicazioni WCF Data Services.

|Argomento|Descrizione|
|-----------|-----------------|
|[Procedura: i messaggi di servizio dati Intercept](/dotnet/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services)|Viene illustrato come aggiungere la convalida a un'operazione del servizio dati.|

 Gli argomenti seguenti illustrano come creare, aggiornare ed eliminare i dati eseguendo operazioni su entità.

|Argomento|Descrizione|
|-----------|-----------------|
|[Procedura: aggiungere, modificare ed eliminare entità](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)|Viene illustrato come creare, aggiornare ed eliminare i dati di entità in un servizio dati.|
|[Procedura: definire le relazioni tra entità](/dotnet/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services)|Viene illustrato come creare o modificare le relazioni in un servizio dati.|

## <a name="see-also"></a>Vedere anche

- [Servizi Windows Communication Foundation e dati WCF in Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Esecuzione di query sul servizio dati](/dotnet/framework/data/wcf/querying-the-data-service-wcf-data-services)