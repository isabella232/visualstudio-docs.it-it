---
title: Convertire un tipo anonimo in classe
description: Informazioni su come usare il menu Azioni rapide e refactoring per convertire un tipo anonimo in una classe in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
monikerRange: '>= vs-2019'
ms.openlocfilehash: eedab2e2d826b44728b4f29569c9086b70eba4a1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123931"
---
# <a name="convert-anonymous-type-to-class"></a>Conversione di tipi anonimi in classe

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Convertire un tipo anonimo in classe .

**Quando:** Si dispone di un tipo anonimo su cui si vuole continuare a usare la compilazione in una classe.

**Perché:** I tipi anonimi sono utili se vengono utilizzati solo in locale. Con l'aumento del codice, è utile avere la possibilità di promuoverli facilmente in una classe.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore in un tipo anonimo.
2. Premere  + **CTRL.** per attivare il menu **Azioni rapide e refactoring**.

   ![Convertire un tipo anonimo in classe](media/convert-anon-to-class.png)

2. Premere **INVIO** per accettare il refactoring.

   ![Conversione del tipo anonimo in classe accettata](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
