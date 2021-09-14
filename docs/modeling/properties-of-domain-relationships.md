---
title: Proprietà delle relazioni di dominio
description: Informazioni sulle proprietà associate a un dominio relationshop, ad esempio Modificatore di accesso, Attributi personalizzati e Genera derivazione doppia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 8972722c0f65f4d007db7173ef41b7a40dba1208
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126637555"
---
# <a name="properties-of-domain-relationships"></a>Proprietà delle relazioni di dominio
Le proprietà nella tabella seguente sono associate a una relazione di dominio. Per informazioni sulle relazioni di dominio, vedere [Informazioni su modelli, classi e relazioni.](../modeling/understanding-models-classes-and-relationships.md) Per altre informazioni su come usare queste proprietà, vedere Personalizzazione ed estensione [di un Domain-Specific linguaggio.](../modeling/customizing-and-extending-a-domain-specific-language.md)

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Modificatore di accesso|Livello di accesso della relazione di dominio ( `public` o `internal` ).|`public`|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe del codice sorgente generata dalla relazione di dominio.|\<none>|
|Genera un valore derivato da Double|Se , vengono generati sia una classe di base che una classe `True` parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [Override ed estensione delle classi generate.](../modeling/overriding-and-extending-the-generated-classes.md)|`False`|
|Ha un costruttore personalizzato|Se `True` , indica che nel codice sorgente viene fornito un costruttore personalizzato. Per altre informazioni, vedere [Override ed estensione delle classi generate.](../modeling/overriding-and-extending-the-generated-classes.md)|`False`|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe del codice sorgente generata dalla relazione di dominio ( `none` o `abstract` `sealed` ).|\<none>|
|Consente duplicati|Se `True` , è possibile creare collegamenti duplicati della relazione di dominio tra gli stessi due elementi.|`False`|
|Relazioni di base|Se la relazione di dominio è derivata, la relazione di base della relazione di dominio.|\<none>|
|Incorporamento|Se `True` , la relazione di dominio è una relazione di incorporamento. Se `False` , la relazione è una relazione di riferimento.|\<both>|
|Nome|Nome della relazione di dominio.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi associato alla relazione di dominio.|Spazio dei nomi corrente|
|Note|Note informali associate alla relazione di dominio.|\<none>|
|Descrizione|Descrizione utilizzata per documentare il codice e utilizzata nell'interfaccia utente della finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome visualizzato nella finestra di progettazione generata per la relazione di dominio.|\<none>|
|Parola chiave della Guida|Parola chiave facoltativa utilizzata per indicizzare la Guida F1 per la relazione di dominio.|\<none>|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))