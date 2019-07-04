---
title: Completamento di IntelliSense per tipi non importati
description: Come usare il completamento IntelliSense per i tipi che non sono stati ancora importati con una direttiva `using`.
ms.date: 06/20/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: f313cfa8520e4c13b310be0f9223466c529ca18f
ms.sourcegitcommit: 16bcaca215de75479695738d3c2d703c78c3500e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2019
ms.locfileid: "67312923"
---
# <a name="intellisense-completion-for-unimported-types"></a>Completamento di IntelliSense per tipi non importati

Questo refactoring si applica a:

- C#

**Cosa:** IntelliSense offre la funzionalità di completamento per i tipi non importati.

**Quando:** si vuole aggiungere un tipo che ha già una dipendenza nel progetto, ma l'istruzione di importazione non è stata ancora aggiunta nel file. 

**Perché?:** non è necessario aggiungere manualmente l'istruzione di importazione nel file.

## <a name="how-to"></a>Procedura

1. Dopo che si è iniziato a usare un tipo che ha una dipendenza nel progetto, IntelliSense visualizzerà i suggerimenti.
2. Premere **TAB**. 

   L'istruzione di importazione verrà aggiunta nel file.

   ![Completamento di IntelliSense per tipi non importati](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Vedere anche

- [Refactoring](../refactoring-in-visual-studio.md)
