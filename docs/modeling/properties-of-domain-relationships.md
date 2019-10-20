---
title: Proprietà delle relazioni di dominio
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 26de877643e25413168d074d85a2aeab0794adc1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658185"
---
# <a name="properties-of-domain-relationships"></a>Proprietà delle relazioni di dominio
Le proprietà nella tabella seguente sono associate a una relazione di dominio. Per informazioni sulle relazioni tra domini, vedere informazioni su [modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

|proprietà|Descrizione|Impostazione predefinita|
|-|-|-|
|Modificatore di accesso|Livello di accesso della relazione di dominio (`public` o `internal`).|`public`|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice sorgente generata dalla relazione di dominio.|\<nessuno>|
|Genera il doppio derivato|Se `True`, viene generata una classe di base e una classe parziale (per supportare la personalizzazione tramite override). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Con costruttore personalizzato|Se `True`, indica che nel codice sorgente viene fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dalla relazione di dominio (`none`, `abstract` o `sealed`).|\<nessuno>|
|Consente i duplicati|Se `True`, è possibile creare collegamenti duplicati della relazione di dominio tra gli stessi due elementi.|`False`|
|Relazioni di base|Se la relazione di dominio è derivata, la relazione di base della relazione di dominio.|\<nessuno>|
|Incorporamento|Se `True`, la relazione di dominio è una relazione di incorporamento. Se `False`, la relazione è una relazione di riferimento.|\<both >|
|Name|Nome della relazione di dominio.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato alla relazione di dominio.|Spazio dei nomi corrente|
|Note|Note informali associate alla relazione di dominio.|\<nessuno>|
|Descrizione|Descrizione utilizzata per documentare il codice e utilizzata nell'interfaccia utente della finestra di progettazione generata.|\<nessuno>|
|Nome visualizzato|Nome visualizzato nella finestra di progettazione generata per la relazione di dominio.|\<nessuno>|
|Parola chiave della Guida|Parola chiave facoltativa utilizzata per indicizzare la Guida sensibile al contesto per la relazione di dominio.|\<nessuno>|

## <a name="see-also"></a>Vedere anche

- [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)