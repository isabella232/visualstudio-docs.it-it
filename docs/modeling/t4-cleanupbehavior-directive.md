---
title: Direttiva T4 CleanUpBehavior | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: d0a03a57734a6536c147759ea05745497eeeffa1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="t4-cleanupbehavior-directive"></a>Direttiva T4 CleanUpBehavior
Per eliminare l'appDomain dopo l'elaborazione un modello di testo, includere la riga seguente:  
  
```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 I modelli di testo vengono elaborati in un appDomain separato dal processo host. Nella maggior parte dei casi, quando un modello di testo è stato elaborato, l'appdomain viene utilizzato nuovamente per elaborare il modello seguente. Se tuttavia si specifica CleanupBehavior, l'appDomain viene eliminato e il modello seguente verrà elaborato in un nuovo appDomain.  
  
 Ciò rallenta l'elaborazione del testo, ma può essere utile per assicurarsi che le risorse vengano eliminate.  
  
 Questa direttiva viene eseguita solo nell'host di Visual Studio.