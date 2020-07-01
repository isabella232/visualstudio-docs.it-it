---
author: dotpaul
ms.author: paulming
ms.date: 05/01/2019
ms.topic: include
ms.openlocfilehash: bc423f10cfbae0b7a0cdaedb72f6891a0e12d228
ms.sourcegitcommit: 748d9cd7328a30f8c80ce42198a94a4b5e869f26
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/15/2019
ms.locfileid: "68147107"
---
- Se possibile, usare invece un serializzatore protetto e **non consentire a un utente malintenzionato di specificare un tipo arbitrario da deserializzare**. Alcuni serializzatori più sicuri includono:
  - <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType>
  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=nameWithType>
  - <xref:System.Web.Script.Serialization.JavaScriptSerializer?displayProperty=nameWithType>-Non usare mai <xref:System.Web.Script.Serialization.SimpleTypeResolver?displayProperty=nameWithType> . Se è necessario usare un resolver di tipi, limitare i tipi deserializzati a un elenco previsto.
  - <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType>
  - Newtonsoft Json.NET-usare TypeNameHandling. None. Se è necessario usare un altro valore per TypeNameHandling, limitare i tipi deserializzati a un elenco previsto con un ISerializationBinder personalizzato.
  - Buffer di protocollo
- Eseguire la prova di manomissione dei dati serializzati. Dopo la serializzazione, la firma crittografica dei dati serializzati. Prima della deserializzazione, convalidare la firma crittografica. Proteggere la chiave crittografica da divulgare e progettare per le rotazioni delle chiavi.