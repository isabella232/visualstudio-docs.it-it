---
title: Direttiva T4 CleanUpBehavior
description: Informazioni sulla direttiva CleanUpBehavior e su come eliminare appDomain dopo l'elaborazione di un modello di testo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 49609dd13e2e322f88f265d27e55c49154f4c5c5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899649"
---
# <a name="t4-cleanupbehavior-directive"></a>Direttiva T4 CleanUpBehavior

Per eliminare l'appDomain dopo l'elaborazione un modello di testo, includere la riga seguente:

```
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>
```

I modelli di testo vengono elaborati in un appDomain separato dal processo host. Nella maggior parte dei casi, quando un modello di testo è stato elaborato, l'appdomain viene utilizzato nuovamente per elaborare il modello seguente. Se tuttavia si specifica CleanupBehavior, l'appDomain viene eliminato e il modello seguente verrà elaborato in un nuovo appDomain.

Ciò rallenta l'elaborazione del testo, ma può essere utile per assicurarsi che le risorse vengano eliminate.

Questa direttiva viene eseguita solo nell'host di Visual Studio.
