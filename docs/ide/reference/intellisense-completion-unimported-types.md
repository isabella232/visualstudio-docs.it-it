---
title: Completamento di IntelliSense per tipi non importati
description: Come usare il completamento IntelliSense per i tipi che non sono stati ancora importati con una direttiva `using`.
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
ms.openlocfilehash: 04ea7c94d3dd24c1a511544adca9bfac3370cd71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094250"
---
# <a name="intellisense-completion-for-unimported-types"></a>Completamento di IntelliSense per tipi non importati

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** IntelliSense consente il completamento per i tipi non importati.

**Quando:** Si desidera aggiungere un tipo che ha già una dipendenza nel progetto, ma l'istruzione import non è ancora stata aggiunta al file. 

**Perché:** Non è necessario aggiungere manualmente l'istruzione import al file.

## <a name="how-to"></a>Procedure

1. Dopo che si è iniziato a usare un tipo che ha una dipendenza nel progetto, IntelliSense visualizzerà i suggerimenti.
2. Premere **TAB**. 

   L'istruzione di importazione verrà aggiunta nel file.

   ![Completamento di IntelliSense per tipi non importati](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
