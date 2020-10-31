---
title: Completamento IntelliSense per i tipi & metodi di estensione
description: Come usare il completamento IntelliSense per i tipi e i metodi di estensione che non sono stati ancora importati con una `using` direttiva.
ms.custom: SEO-VS-2020
ms.date: 07/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3eb912ebb4d8d7d4596a6aae6499ac054d4514ca
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102506"
---
# <a name="intellisense-completion-for-unimported-types-and-extension-methods"></a>Completamento IntelliSense per i tipi non importati e i metodi di estensione

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** IntelliSense fornisce il completamento per i tipi non importati e i metodi di estensione.

**Quando:** Si vuole usare un tipo o metodi di estensione che già hanno una dipendenza nel progetto, ma l'istruzione using non è stata ancora aggiunta al file.

**Motivo:** Non è necessario aggiungere manualmente l'istruzione using al file.

## <a name="how-to"></a>Procedure

1. Quando si inizia a digitare il nome di un tipo o di un metodo di estensione con una dipendenza nel progetto, IntelliSense fornirà suggerimenti. Per gli elementi degli spazi dei nomi non importati verrebbe visualizzato lo spazio dei nomi che lo contiene come suffisso.

   > [!TIP]
   > È possibile mostrare o nascondere elementi da spazi dei nomi non importati su richiesta, usando il **pulsante di espansione (ALT + A)** visualizzato nella parte inferiore sinistra dell'elenco di completamento. Per modificare il comportamento predefinito, passare a **strumenti**  >  **Opzioni**  >  **editor di testo**  >  **C#**  /  **Basic**  >  **IntelliSense** e cercare **Mostra elementi da spazi dei nomi non importati** .

2. Consente di selezionare ed eseguire il commit di un elemento non importato.

   L'istruzione using verrà aggiunta automaticamente al file.

   ![Completamento di IntelliSense per tipi non importati](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Vedere anche

- [IntelliSense](../using-intellisense.md)
- [Refactoring](../refactoring-in-visual-studio.md)
