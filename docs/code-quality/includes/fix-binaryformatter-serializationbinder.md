---
ms.openlocfilehash: 557d811e2eeaf926cb958471d214fc23c50a25f2
ms.sourcegitcommit: 43df639b2cd99200f725a8ebb941477481a6f0ff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2020
ms.locfileid: "87471577"
---
- Usare invece un serializzatore protetto e **non consentire a un utente malintenzionato di specificare un tipo arbitrario da deserializzare**. Per ulteriori informazioni, vedere le [alternative preferite](/dotnet/standard/serialization/binaryformatter-security-guide#preferred-alternatives).
- Eseguire la prova di manomissione dei dati serializzati. Dopo la serializzazione, la firma crittografica dei dati serializzati. Prima della deserializzazione, convalidare la firma crittografica. Proteggere la chiave crittografica da divulgare e progettare per le rotazioni delle chiavi.
- Questa opzione rende il codice vulnerabile ad attacchi di tipo Denial of Service e possibili attacchi di esecuzione di codice remoto in futuro. Per ulteriori informazioni, vedere la [Guida alla sicurezza di BinaryFormatter](/dotnet/standard/serialization/binaryformatter-security-guide). Limitare i tipi deserializzati. Implementare un oggetto personalizzato <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType> . Prima della deserializzazione, impostare la `Binder` proprietà su un'istanza di personalizzata <xref:System.Runtime.Serialization.SerializationBinder> in tutti i percorsi del codice. Nel metodo sottoposto a override <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> , se il tipo è imprevisto, generare un'eccezione per arrestare la deserializzazione.
