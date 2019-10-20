---
title: Proprietà delle classi di dominio
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain class
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23437983950efb8e86aaadd391e96b0e7d0c0a6c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658217"
---
# <a name="properties-of-domain-classes"></a>Proprietà delle classi di dominio
Le classi di dominio hanno le proprietà riportate nella tabella seguente. Per informazioni sulle classi di dominio, vedere informazioni su [modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

|proprietà|Descrizione|Impostazione predefinita|
|-|-|-|
|Modificatore di accesso|Livello di accesso della classe di dominio (`public` o `internal`).|`public`|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice sorgente generata da questa classe di dominio.|\<nessuno>|
|Genera il doppio derivato|Se `True`, verranno generate sia una classe di base che una classe parziale (per supportare la personalizzazione tramite sostituzioni). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Con costruttore personalizzato|Se `True`, nel codice sorgente verrà fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dalla classe di dominio (`none`, `abstract` o `sealed`).|`none`|
|Classe di base|Se questa classe di dominio è derivata, il nome della classe di base.|\<nessuno>|
|Name|Nome di questa classe di dominio.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi di questa classe di dominio.|Spazio dei nomi corrente|
|Note|Note informali associate a questa classe di dominio.|\<nessuno>|
|Descrizione|Descrizione utilizzata per documentare l'interfaccia utente della finestra di progettazione generata.|\<nessuno>|
|Nome visualizzato|Nome che verrà visualizzato nella finestra di progettazione generata per questa classe di dominio.|\<nessuno>|
|Parola chiave della Guida|Parola chiave facoltativa utilizzata per indicizzare la Guida F1 per questa classe di dominio.|\<nessuno>|

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)