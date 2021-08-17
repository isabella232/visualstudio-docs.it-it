---
title: Completamento IntelliSense per i tipi & di estensione
description: Come usare il completamento IntelliSense per i tipi e i metodi di estensione che non sono ancora stati importati con una `using` direttiva .
ms.custom: SEO-VS-2020
ms.date: 07/27/2020
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
ms.openlocfilehash: f011357c3c72d05c280c2dc19a2e7282a10920c5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151496"
---
# <a name="intellisense-completion-for-unimported-types-and-extension-methods"></a>Completamento IntelliSense per tipi e metodi di estensione non importati

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** IntelliSense fornisce il completamento per i tipi e i metodi di estensione non importati.

**Quando:** Si vuole usare un tipo o metodi di estensione che hanno già una dipendenza nel progetto, ma l'istruzione using non è ancora stata aggiunta al file.

**Perché:** Non è necessario aggiungere manualmente l'istruzione using al file.

## <a name="how-to"></a>Procedure

1. Quando si inizia a digitare il nome di un tipo o di un metodo di estensione con una dipendenza nel progetto, IntelliSense offrirà suggerimenti. Per gli elementi degli spazi dei nomi non importati il relativo spazio dei nomi contenitore verrebbe visualizzato come suffisso.

   > [!TIP]
   > È possibile visualizzare/nascondere elementi da spazi dei nomi non importati su richiesta usando il pulsante **Expander (ALT+A)** visualizzato in basso a sinistra nell'elenco di completamento. Per modificare il comportamento predefinito, passare a Strumenti Opzioni Editor di testo  >    >    >    /    >  **IntelliSense** di base C# e cercare Mostra elementi da spazi dei nomi non importati.

2. Selezionare ed eseguire il commit di un elemento non importato.

   L'istruzione using verrà aggiunta automaticamente al file.

   ![Completamento di IntelliSense per tipi non importati](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Vedi anche

- [IntelliSense](../using-intellisense.md)
- [Refactoring](../refactoring-in-visual-studio.md)
