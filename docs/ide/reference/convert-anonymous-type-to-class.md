---
title: Convertire un tipo anonimo in classe
description: Informazioni su come usare il menu azioni rapide e refactoring per convertire un tipo anonimo in una classe in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
monikerRange: '>= vs-2019'
ms.openlocfilehash: a041c077a41ce6b37d74507723ec1ce0f8c9585c
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040785"
---
# <a name="convert-anonymous-type-to-class"></a>Conversione di tipi anonimi in classe

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Converte un tipo anonimo in classe.

**Quando:** Si dispone di un tipo anonimo che si vuole continuare a compilare in una classe.

**Motivo:** I tipi anonimi sono utili se vengono utilizzati solo localmente. Con l'aumento del codice, è utile avere la possibilità di promuoverli facilmente in una classe.

## <a name="how-to"></a>Procedure

1. Posizionare il cursore in un tipo anonimo.
2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

   ![Convertire un tipo anonimo in classe](media/convert-anon-to-class.png)

2. Premere **invio** per accettare il refactoring.

   ![Conversione del tipo anonimo in classe accettata](media/convert-anon-to-class-complete.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
