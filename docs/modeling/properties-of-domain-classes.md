---
title: Proprietà delle classi di dominio
description: Informazioni sulle varie proprietà delle classi di dominio, ad esempio modificatore di accesso, attributi personalizzati e generazione di un valore Double derivato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fd36973a9c355dcaec32b6da4149e6efd88282da
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97360793"
---
# <a name="properties-of-domain-classes"></a>Proprietà delle classi di dominio
Le classi di dominio hanno le proprietà riportate nella tabella seguente. Per informazioni sulle classi di dominio, vedere informazioni su [modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un linguaggio Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Modificatore di accesso|Livello di accesso della classe di dominio (`public` o `internal`).|`public`|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice sorgente generata da questa classe di dominio.|\<none>|
|Genera il doppio derivato|Se `True` , verranno generate sia una classe di base che una classe parziale (per supportare la personalizzazione tramite override). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Con costruttore personalizzato|Se `True` , nel codice sorgente verrà fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dalla classe di dominio ( `none` `abstract` o `sealed` ).|`none`|
|Classe di base|Se questa classe di dominio è derivata, il nome della classe di base.|\<none>|
|Nome|Nome di questa classe di dominio.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi di questa classe di dominio.|Spazio dei nomi corrente|
|Note|Note informali associate a questa classe di dominio.|\<none>|
|Description|Descrizione utilizzata per documentare l'interfaccia utente della finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questa classe di dominio.|\<none>|
|Parola chiave della Guida|Parola chiave facoltativa utilizzata per indicizzare la Guida F1 per questa classe di dominio.|\<none>|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))