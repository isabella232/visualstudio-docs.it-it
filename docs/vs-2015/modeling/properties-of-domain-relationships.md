---
title: Proprietà delle relazioni di dominio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95372b2bc7537e017a4eeca9b414ef054d82046d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671548"
---
# <a name="properties-of-domain-relationships"></a>Proprietà delle relazioni di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le proprietà nella tabella seguente sono associate a una relazione di dominio. Per informazioni sulle relazioni tra domini, vedere informazioni su [modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzazione ed estensione di un Domain-Specific Language](../modeling/customizing-and-extending-a-domain-specific-language.md).

|Proprietà|Descrizione|Predefinito|
|--------------|-----------------|-------------|
|Modificatore di accesso|Livello di accesso della relazione di dominio ( `public` o `internal` ).|`public`|
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice sorgente generata dalla relazione di dominio.|\<none>|
|Genera il doppio derivato|Se `True` , viene generata una classe di base e una classe parziale (per supportare la personalizzazione tramite override). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Con costruttore personalizzato|Se `True` , indica che nel codice sorgente viene fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generata dalla relazione di dominio ( `none` , `abstract` o `sealed` ).|\<none>|
|Consente i duplicati|Se `True` , è possibile creare collegamenti duplicati della relazione di dominio tra gli stessi due elementi.|`False`|
|Relazioni di base|Se la relazione di dominio è derivata, la relazione di base della relazione di dominio.|\<none>|
|Incorporamento|Se `True` , la relazione di dominio è una relazione di incorporamento. Se `False` , la relazione è una relazione di riferimento.|\<both>|
|Name|Nome della relazione di dominio.|Nome corrente|
|Spazio dei nomi|Spazio dei nomi affiliato alla relazione di dominio.|Spazio dei nomi corrente|
|Note|Note informali associate alla relazione di dominio.|\<none>|
|Descrizione|Descrizione utilizzata per documentare il codice e utilizzata nell'interfaccia utente della finestra di progettazione generata.|\<none>|
|Nome visualizzato|Nome visualizzato nella finestra di progettazione generata per la relazione di dominio.|\<none>|
|Parola chiave della Guida|Parola chiave facoltativa utilizzata per indicizzare la Guida sensibile al contesto per la relazione di dominio.|\<none>|

## <a name="see-also"></a>Vedere anche
 [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
