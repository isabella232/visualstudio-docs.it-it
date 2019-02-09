---
title: Proprietà delle relazioni di dominio
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a2693994c9ead711f3bb536d0e37f485bc00047b
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55938176"
---
# <a name="properties-of-domain-relationships"></a>Proprietà delle relazioni di dominio
Le proprietà nella tabella seguente sono associate a una relazione di dominio. Per informazioni sulle relazioni di dominio, vedere [informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md). Per altre informazioni su come usare queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Proprietà|Descrizione|Impostazione predefinita|
|-|-|-|
|Modificatore di accesso|Il livello di accesso della relazione di dominio (`public` o `internal`).|`public`|
|Attributi personalizzati|Consente di aggiungere attributi alla classe di codice sorgente generato dalla relazione di dominio.|\<nessuno>|
|Genera l'errore doppia derivati|Se `True`, viene generata una classe di base sia una classe parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Ha un costruttore personalizzato|Se `True`, indica che viene fornito un costruttore personalizzato nel codice sorgente. Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dalla relazione di dominio (`none`, `abstract` o `sealed`).|\<nessuno>|
|Consente i duplicati|Se `True`, è possibile creare collegamenti duplicati di relazione di dominio tra gli stessi due elementi.|`False`|
|Relazioni di base|Se la relazione di dominio è derivata, la relazione di base della relazione di dominio.|\<nessuno>|
|È di incorporamento|Se `True`, la relazione di dominio è una relazione di incorporamento. Se `False`, la relazione è una relazione di riferimento.|\<both>|
|nome|Il nome della relazione di dominio.|Nome corrente|
|Spazio dei nomi|Lo spazio dei nomi che è affiliato alla relazione di dominio.|Spazio dei nomi corrente|
|Note|Note informali associate la relazione di dominio.|\<nessuno>|
|Descrizione|La descrizione che consente di documentare il codice e viene utilizzata nell'interfaccia utente della finestra di progettazione generata.|\<nessuno>|
|Nome visualizzato|Il nome visualizzato nella finestra di progettazione generata per la relazione di dominio.|\<nessuno>|
|Parola chiave della Guida|La parola chiave facoltativa utilizzata per indicizzare la Guida F1 per la relazione di dominio.|\<nessuno>|

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)