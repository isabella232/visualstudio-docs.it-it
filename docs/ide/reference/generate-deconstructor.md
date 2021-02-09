---
title: Generare un'azione rapida decostruttore
description: Informazioni su come usare il menu azioni rapide e refactoring per generare immediatamente lo stub del metodo per un nuovo costruttore.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: a4c243ab46858a4c8eb944d485900718b685bf5c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99897958"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Generare un decostruttore in Visual Studio

Questa generazione di codice si applica a:

- C#

**Cosa:** Consente di generare immediatamente lo stub del metodo per un nuovo costruttore.

**Quando:** Si vuole decostruire correttamente il tipo automaticamente.

**Motivo:** È possibile digitare manualmente un decostruttore, ma questa funzionalità genera automaticamente lo stub con i parametri out corretti.

## <a name="generate-a-deconstructor"></a>Generare un decostruttore

1. Dichiarare un nuovo tipo con i parametri out desiderati specificati. Questa dichiarazione genererà un errore quando non è possibile trovare istanze di decostruzione corrispondenti alla dichiarazione.

   ![Errore di decostruttore mancante](media/deconstruct.png)

2. Eseguire uno dei passaggi seguenti:

   - **Tastiera**
      - Con il cursore nella dichiarazione, selezionare CTRL+. per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
      - Selezionare l' :::image type="icon" source="media/screwdriver.png"::: icona visualizzata nel margine sinistro se il cursore di testo si trova già nella riga vuota della classe.

      ![Correzione del codice di generazione del decostruttore](media/deconstruct-codefix.png)

3. Selezionare **Genera il metodo 'MyInternalClass.Deconstruct'** per generare il decostruttore.

   ![Codice del decostruttore risultante](media/deconstruct-result.png)

## <a name="see-also"></a>Vedi anche

- [Generazione codice](../code-generation-in-visual-studio.md)
- [Anteprima modifiche](../../ide/preview-changes.md)
- [Suggerimenti per gli sviluppatori .NET](../csharp-developer-productivity.md)