---
title: Generare un override - la generazione di codice (c#) | Documenti Microsoft
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: dotnet
ms.openlocfilehash: 622c05f51d0dc32739f5d27b75aec31c69ee4d87
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="generate-an-override-in-c"></a>Generare una sostituzione in c# #

**Novità:** consente di generare immediatamente il codice per qualsiasi metodo che può essere sottoposto a override da una classe base.

**Quando:** che si desidera eseguire l'override di un metodo della classe base e generare automaticamente la firma.

**Motivo:** è possibile scrivere la firma del metodo, tuttavia questa funzionalità genera automaticamente la firma.

**Procedura:**

1. Tipo di **override** (parola chiave), seguito da uno spazio, in cui si desidera inserire una firma del metodo sottoposto a override e verrà visualizzato un elenco a discesa IntelliSense.

   ![Eseguire l'override di IntelliSense](media/override_intellisense.png)

1. Selezionare il metodo di cui si desidera eseguire l'override della classe base facendo clic con il mouse o passare a esso con la tastiera e premendo **invio**.

   >[!TIP]
   >* Utilizzare l'icona delle proprietà ![Icona della proprietà](media/override_property.png) Per mostrare o nascondere le proprietà nell'elenco.
   >* Utilizzare l'icona del metodo ![Icona del metodo](media/override_method.png) Per mostrare o nascondere i metodi nell'elenco.

1. Il metodo selezionato o la proprietà verrà aggiunto alla classe come una sostituzione, pronta per essere implementato.

   ![Eseguire l'override di risultati](media/override_result.png)

## <a name="see-also"></a>Vedere anche

[Code Generation (C#)](../code-generation-csharp.md) (Generazione di codice (C#))
