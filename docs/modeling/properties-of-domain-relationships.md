---
title: Proprietà delle relazioni di dominio
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 7e860daf40358978538f732fdb9fea0696778354
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53937582"
---
# <a name="properties-of-domain-relationships"></a>Proprietà delle relazioni di dominio
Le proprietà nella tabella seguente sono associate a una relazione di dominio. Per informazioni sulle relazioni di dominio, vedere [informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md). Per altre informazioni su come usare queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Proprietà|Descrizione|Impostazione predefinita|
|-|-|-|
|Modificatore di accesso|Il livello di accesso della relazione di dominio (`public` o `internal`).|`public`|
|Attributi personalizzati|Consente di aggiungere attributi alla classe di codice sorgente generato dalla relazione di dominio.|\<Nessuno >|
|Genera l'errore doppia derivati|Se `True`, viene generata una classe di base sia una classe parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Ha un costruttore personalizzato|Se `True`, indica che viene fornito un costruttore personalizzato nel codice sorgente. Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dalla relazione di dominio (`none`, `abstract` o `sealed`).|\<Nessuno >|
|Consente i duplicati|Se `True`, è possibile creare collegamenti duplicati di relazione di dominio tra gli stessi due elementi.|`False`|
|Relazioni di base|Se la relazione di dominio è derivata, la relazione di base della relazione di dominio.|\<Nessuno >|
|È di incorporamento|Se `True`, la relazione di dominio è una relazione di incorporamento. Se `False`, la relazione è una relazione di riferimento.|\<entrambi >|
|nome|Il nome della relazione di dominio.|Nome corrente|
|Spazio dei nomi|Lo spazio dei nomi che è affiliato alla relazione di dominio.|Spazio dei nomi corrente|
|Note|Note informali associate la relazione di dominio.|\<Nessuno >|
|Descrizione|La descrizione che consente di documentare il codice e viene utilizzata nell'interfaccia utente della finestra di progettazione generata.|\<Nessuno >|
|Nome visualizzato|Il nome visualizzato nella finestra di progettazione generata per la relazione di dominio.|\<Nessuno >|
|Parola chiave della Guida|La parola chiave facoltativa utilizzata per indicizzare la Guida F1 per la relazione di dominio.|\<Nessuno >|

## <a name="see-also"></a>Vedere anche

- [Glossario sugli strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)