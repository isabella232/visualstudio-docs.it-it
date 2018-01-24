---
title: Generare un override - Generazione del codice (Visual Basic) | Microsoft Docs
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
ms.openlocfilehash: 334f5a79dad1b7d2c14768d0698797a34ad039c5
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2018
---
# <a name="generate-an-override-in-visual-basic"></a>Generare un override in Visual Basic
**Cosa:** consente di generare immediatamente il codice per qualsiasi metodo che può essere sottoposto a override da una classe di base. 

**Quando:** si vuole eseguire l'override di un metodo della classe di base e generare automaticamente la firma.  

**Perché:** è possibile scrivere la firma del metodo manualmente, ma questa funzionalità la genera automaticamente. 

**Come:**

1. Digitare la parola chiave **Overrides** seguita da uno spazio, nella posizione in cui si vuole inserire la firma di un metodo sottoposto a override e verrà visualizzato un elenco a discesa IntelliSense.

   ![IntelliSense per l'override](media/override-intellisense-vb.png)

1. Selezionare il metodo di cui si vuole eseguire l'override dalla classe di base facendo clic con il mouse o spostandosi su di esso con la tastiera e premendo **INVIO**.

<!--
   >[!TIP]
   >* Use the Property icon ![Property icon](media/override-property-vb.png) to show or hide  Properties in the list.
   >* Use the Method icon ![Property icon](media/override-method-vb.png) to show or hide Methods in the list.
-->

1. Il metodo o la proprietà selezionati verranno aggiunti alla classe come override, pronti per l'implementazione.

   ![Risultato dell'override](media/override-result-vb.png)

## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md) 