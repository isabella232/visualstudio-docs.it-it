---
title: Proprietà delle classi di dominio
description: Informazioni sulle varie proprietà delle classi di dominio, ad esempio Modificatore di accesso, Attributi personalizzati e Genera derivate doppie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: eaaae0028d574a521319ae045cdb4f7f1bdafaa2
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390008"
---
# <a name="properties-of-domain-classes"></a>Proprietà delle classi di dominio
Le classi di dominio hanno le proprietà nella tabella seguente. Per informazioni sulle classi di dominio, vedere [Informazioni su modelli, classi e relazioni.](../modeling/understanding-models-classes-and-relationships.md) Per altre informazioni su come usare queste proprietà, vedere Personalizzazione ed estensione di [un Domain-Specific linguaggio](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Modificatore di accesso|Livello di accesso della classe di dominio (`public` o `internal`).|`public`|
|Attributi personalizzati|Usato per aggiungere attributi alla classe del codice sorgente generata da questa classe di dominio.|\<none>|
|Genera una derivazione doppia|Se , verranno generate sia una classe di base che una classe `True` parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Ha un costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per altre informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe del codice sorgente generata dalla classe di dominio ( `none` , `abstract` o `sealed` ).|`none`|
|Classe base|Se questa classe di dominio è derivata, il nome della classe di base.|\<none>|
|Nome|Nome di questa classe di dominio.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi di questa classe di dominio.|Spazio dei nomi corrente|
|Note|Note informali associate a questa classe di dominio.|\<none>|
|Descrizione|Descrizione usata per documentare l'interfaccia utente della finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questa classe di dominio.|\<none>|
|Parola chiave della Guida|Parola chiave facoltativa usata per indicizzare la Guida F1 per questa classe di dominio.|\<none>|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))