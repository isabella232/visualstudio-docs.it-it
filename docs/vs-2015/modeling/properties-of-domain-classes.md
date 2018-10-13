---
title: Proprietà delle classi di dominio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: f9f84290ca8155cb2cf2b48a5d9b3f5f68c7ce9a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49172627"
---
# <a name="properties-of-domain-classes"></a>Proprietà delle classi di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Classi di dominio hanno le proprietà nella tabella seguente. Per informazioni sulle classi di dominio, vedere [informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md). Per altre informazioni su come usare queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Proprietà|Descrizione|Impostazione predefinita|  
|--------------|-----------------|-------------|  
|Modificatore di accesso|Livello di accesso della classe di dominio (`public` o `internal`).|`public`|  
|Attributi personalizzati|Consente di aggiungere attributi alla classe di codice sorgente generato da questa classe di dominio.|\<Nessuno >|  
|Genera l'errore doppia derivati|Se `True`, verrà generate una classe di base sia una classe parziale (per supportare la personalizzazione tramite override). Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Ha un costruttore personalizzato|Se `True`, verrà fornito un costruttore personalizzato nel codice sorgente. Per altre informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dalla classe di dominio (`none`, `abstract` o `sealed`).|`none`|  
|Classe di base|Se questa classe di dominio è derivata, il nome della classe di base.|\<Nessuno >|  
|nome|Il nome di questa classe di dominio.|Nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi di questa classe di dominio.|Spazio dei nomi corrente|  
|Note|Note informali associate a questa classe di dominio.|\<Nessuno >|  
|Descrizione|La descrizione che consente di documentare l'interfaccia utente della finestra di progettazione generata.|\<Nessuno >|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per questa classe di dominio.|\<Nessuno >|  
|Parola chiave della Guida|La parola chiave facoltativa utilizzata per indicizzare la Guida F1 per questa classe di dominio.|\<Nessuno >|  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario sugli strumenti Domain-Specific Language](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)



