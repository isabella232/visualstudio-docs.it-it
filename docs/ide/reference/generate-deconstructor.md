---
title: Generare un'azione rapida decostruttore
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2ca2d3a0c174fa4c7d0f66d3abc440b8c9aa93cf
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62790313"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Generare un decostruttore in Visual Studio

Questa generazione di codice si applica a:

- C#

**Cosa:** consente di generare immediatamente lo stub del metodo per un nuovo decostruttore.

**Quando:** si vuole decostruire correttamente il tipo automaticamente.

**Perché?:** è possibile digitare manualmente un decostruttore, ma questa funzionalità genera automaticamente lo stub con i parametri out corretti.

## <a name="generate-a-deconstructor"></a>Generare un decostruttore

1. Dichiarare un nuovo tipo con i parametri out desiderati specificati. Questa dichiarazione genererà un errore quando non è possibile trovare istanze di decostruzione corrispondenti alla dichiarazione.

   ![Errore di decostruttore mancante](media/deconstruct.png)

2. Eseguire uno dei passaggi seguenti:

   - **Tastiera**
      - Con il cursore nella dichiarazione, selezionare CTRL+. per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
      - Selezionare l'icona a forma di ![cacciavite](media/screwdriver.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga vuota nella classe.

      ![Correzione del codice di generazione del decostruttore](media/deconstruct-codefix.png)

3. Selezionare **Genera il metodo 'MyInternalClass.Deconstruct'** per generare il decostruttore.

   ![Codice del decostruttore risultante](media/deconstruct-result.png)

## <a name="see-also"></a>Vedere anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)
- [Suggerimenti per gli sviluppatori di .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)