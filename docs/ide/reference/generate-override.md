---
title: Generare un override di metodo
description: Informazioni su come generare immediatamente il codice per qualsiasi metodo di cui è possibile eseguire l'override da una classe di base.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 0724500bf90e3e0253d936facf4be62f68533ba1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085897"
---
# <a name="generate-an-override-in-visual-studio"></a>Generare un override in Visual Studio

Questa generazione di codice si applica a:

- C#

- Visual Basic

**Cosa:** consente di generare immediatamente il codice per qualsiasi metodo che può essere sottoposto a override da una classe di base.

**Quando:** si vuole eseguire l'override di un metodo della classe di base e generare automaticamente la firma.

**Perché:** è possibile scrivere la firma del metodo manualmente, ma questa funzionalità la genera automaticamente.

## <a name="how-to"></a>Procedure

1. Digitare `override` in C# o `Overrides` in Visual Basic, seguito da uno spazio, nella posizione in cui si vuole inserire un metodo di override.

   - C#:

      ![IntelliSense per l'override C#](media/override-intellisense-cs.png)

   - Visual Basic:

      ![IntelliSense per l'override VB](media/override-intellisense-vb.png)

2. Selezionare il metodo di cui si vuole eseguire l'override dalla classe di base.

   > [!TIP]
   > - Usare l'icona delle proprietà ![Icona della proprietà](media/override-property-cs.png) per mostrare o nascondere le proprietà nell'elenco.
   > - Usare l'icona dei metodi ![Icona del metodo](media/override-method-cs.png) per mostrare o nascondere i metodi nell'elenco.

   Il metodo o la proprietà selezionati vengono aggiunti alla classe come override, pronti per l'implementazione.

   - C#:

       ![Risultato dell'override C#](media/override-result-cs.png)

   - Visual Basic:

       ![Risultato dell'override VB](media/override-result-vb.png)

## <a name="see-also"></a>Vedi anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
