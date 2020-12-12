---
title: Proprietà delle relazioni di dominio
description: Informazioni sulle proprietà associate a un relationshop di dominio, ad esempio modificatore di accesso, attributi personalizzati e generazione di un valore Double derivato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88c5db50432947b99a2667280fe7861e7acd95ac
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97362457"
---
# <a name="properties-of-domain-relationships"></a>Proprietà delle relazioni di dominio
Le proprietà nella tabella seguente sono associate a una relazione di dominio. Per informazioni sulle relazioni tra domini, vedere informazioni su [modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un linguaggio Domain-Specific](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Proprietà|Descrizione|Predefinito|
|-|-|-|
|Modificatore di accesso|Livello di accesso della relazione di dominio ( `public` o `internal` ).|`public`|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice sorgente generata dalla relazione di dominio.|\<none>|
|Genera il doppio derivato|Se `True` , viene generata una classe di base e una classe parziale (per supportare la personalizzazione tramite override). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Con costruttore personalizzato|Se `True` , indica che nel codice sorgente viene fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dalla relazione di dominio ( `none` , `abstract` o `sealed` ).|\<none>|
|Consente i duplicati|Se `True` , è possibile creare collegamenti duplicati della relazione di dominio tra gli stessi due elementi.|`False`|
|Relazioni di base|Se la relazione di dominio è derivata, la relazione di base della relazione di dominio.|\<none>|
|Incorporamento|Se `True` , la relazione di dominio è una relazione di incorporamento. Se `False` , la relazione è una relazione di riferimento.|\<both>|
|Nome|Nome della relazione di dominio.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato alla relazione di dominio.|Spazio dei nomi corrente|
|Note|Note informali associate alla relazione di dominio.|\<none>|
|Description|Descrizione utilizzata per documentare il codice e utilizzata nell'interfaccia utente della finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome visualizzato nella finestra di progettazione generata per la relazione di dominio.|\<none>|
|Parola chiave della Guida|Parola chiave facoltativa utilizzata per indicizzare la Guida sensibile al contesto per la relazione di dominio.|\<none>|

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))