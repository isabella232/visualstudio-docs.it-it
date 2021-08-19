---
title: Generare un'azione rapida decostruttore
description: Informazioni su come usare il menu Azioni rapide e refactoring per generare immediatamente lo stub del metodo per un nuovo decostruttore.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: eb6ffb06436b36382925fb33ff4fbb35626e8a21
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151652"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Generare un decostruttore in Visual Studio

Questa generazione di codice si applica a:

- C#

**Cosa:** Consente di generare immediatamente lo stub del metodo per un nuovo decostruttore.

**Quando:** Si vuole decostruire correttamente il tipo automaticamente.

**Perché:** È possibile digitare manualmente un decostruttore, ma questa funzionalità genera automaticamente lo stub con i parametri out corretti.

## <a name="generate-a-deconstructor"></a>Generare un decostruttore

1. Dichiarare un nuovo tipo con i parametri out desiderati specificati. Questa dichiarazione genererà un errore quando non è possibile trovare istanze di decostruzione corrispondenti alla dichiarazione.

   ![Errore di decostruttore mancante](media/deconstruct.png)

2. Eseguire uno dei passaggi seguenti:

   - **Tastiera**
      - Con il cursore nella dichiarazione, selezionare CTRL+. per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
      - Selezionare :::image type="icon" source="media/screwdriver.png"::: l'icona visualizzata nel margine sinistro se il cursore di testo si trova già nella riga vuota della classe .

      ![Correzione del codice di generazione del decostruttore](media/deconstruct-codefix.png)

3. Selezionare **Genera il metodo 'MyInternalClass.Deconstruct'** per generare il decostruttore.

   ![Codice del decostruttore risultante](media/deconstruct-result.png)

## <a name="see-also"></a>Vedi anche

- [Generazione codice](../code-generation-in-visual-studio.md)
- [Visualizzare in anteprima le modifiche](../../ide/preview-changes.md)
- [Suggerimenti per sviluppatori .NET](../csharp-developer-productivity.md)