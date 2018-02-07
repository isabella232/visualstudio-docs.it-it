---
title: Generare un override - Generazione del codice (C#) | Microsoft Docs
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b3c8cfc4-7c1f-4606-970e-3f7651604bab
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 3801d8ce60cf87126f8894bf44c77056f996cde1
ms.sourcegitcommit: b01406355e3b97547b7cbf8ce3960f101b165cec
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/06/2018
---
# <a name="generate-an-override-in-c"></a>Generare un override in C# #

**Cosa:** consente di generare immediatamente il codice per qualsiasi metodo che può essere sottoposto a override da una classe di base.

**Quando:** si vuole eseguire l'override di un metodo della classe di base e generare automaticamente la firma.

**Perché:** è possibile scrivere la firma del metodo manualmente, ma questa funzionalità la genera automaticamente.

**Come:**

1. Digitare la parola chiave **override** seguita da uno spazio nella posizione in cui si vuole inserire la firma di un metodo sottoposto a override e verrà visualizzato un elenco a discesa IntelliSense.

   ![IntelliSense per l'override](media/override-intellisense-cs.png)

1. Selezionare il metodo di cui si vuole eseguire l'override dalla classe di base facendo clic con il mouse o spostandosi su di esso con la tastiera e premendo **INVIO**.

   >[!TIP]
   >* Usare l'icona Proprietà ![Icona della proprietà](media/override-property-cs.png) per mostrare o nascondere le proprietà nell'elenco.
   >* Usare l'icona Metodo ![Icona del metodo](media/override-method-cs.png) per mostrare o nascondere i metodi nell'elenco.

1. Il metodo o la proprietà selezionati verranno aggiunti alla classe come override, pronti per l'implementazione.

   ![Risultato dell'override](media/override-result-cs.png)

## <a name="see-also"></a>Vedere anche

[Generazione codice](../code-generation-in-visual-studio.md)
