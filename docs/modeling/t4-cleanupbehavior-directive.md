---
title: Direttiva T4 CleanUpBehavior
description: Informazioni sulla direttiva CleanUpBehavior e su come eliminare appDomain dopo l'elaborazione di un modello di testo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 454522337d57f5f480aecdc30ef69efd39d6a11ab181f6a0324a84109e9c09db
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370489"
---
# <a name="t4-cleanupbehavior-directive"></a>Direttiva T4 CleanUpBehavior

Per eliminare l'appDomain dopo l'elaborazione un modello di testo, includere la riga seguente:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

I modelli di testo vengono elaborati in un appDomain separato dal processo host. Nella maggior parte dei casi, quando un modello di testo è stato elaborato, l'appdomain viene utilizzato nuovamente per elaborare il modello seguente. Se tuttavia si specifica CleanupBehavior, l'appDomain viene eliminato e il modello seguente verrà elaborato in un nuovo appDomain.

Ciò rallenta l'elaborazione del testo, ma può essere utile per assicurarsi che le risorse vengano eliminate.

Questa direttiva viene eseguita solo nell'host di Visual Studio.
