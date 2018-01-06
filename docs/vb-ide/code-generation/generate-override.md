---
title: Generare un override - la generazione di codice (Visual Basic) | Documenti Microsoft
ms.custom: 
ms.date: 11/17/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 4a384eb3e75a499eb2a35c747f003846580738e9
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="generate-an-override-in-visual-basic"></a>Generare una sostituzione in Visual Basic
**Novità:** consente di generare immediatamente il codice per un qualsiasi metodo che può essere sottoposto a override da una classe base. 

**Quando:** che si desidera eseguire l'override di un metodo della classe base e generare automaticamente la firma.  

**Motivo:** è possibile scrivere la firma del metodo, tuttavia questa funzionalità genera automaticamente la firma. 

**Procedura:**

1. Tipo di **esegue l'override** (parola chiave), seguito da uno spazio, in cui si desidera inserire una firma del metodo sottoposto a override e verrà visualizzato un elenco a discesa IntelliSense.

   ![Eseguire l'override di IntelliSense](media/override_intellisense.png)

1. Selezionare il metodo di cui si desidera eseguire l'override della classe base facendo clic con il mouse o passare a esso con la tastiera e premendo **invio**.

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override_property.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override_method.png) to show or hide Methods in the list.
-->

1. Il metodo selezionato o la proprietà verrà aggiunto alla classe come una sostituzione, pronta per essere implementato.

   ![Eseguire l'override di risultati](media/override_result.png)

## <a name="see-also"></a>Vedere anche  
[Code Generation (Visual Basic)](../code-generation-vb.md) (Generazione di codice (Visual Basic)) 