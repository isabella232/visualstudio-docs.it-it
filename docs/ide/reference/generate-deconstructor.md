---
title: Generare un'azione rapida decostruttore
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: a609b16e0d1bc7e30dc26ef047228a6cacdb46b2
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2019
ms.locfileid: "57324736"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Generare un decostruttore in Visual Studio

Questa generazione di codice si applica a:

- C#

**Cosa:** consente di generare immediatamente lo stub del metodo per un nuovo decostruttore.

**Quando:** si vuole decostruire correttamente il tipo automaticamente.

**Perché?:** è possibile digitare manualmente un decostruttore, tuttavia questa funzionalità genererà automaticamente lo stub con i parametri out corretti.

## <a name="generate-deconstructor"></a>Generare un decostruttore

1. Dichiarare un nuovo tipo con i parametri out desiderati specificati. Questa dichiarazione genererà un errore quando non è possibile trovare istanze di decostruzione corrispondenti alla dichiarazione.

   ![Errore di decostruttore mancante](media/deconstruct.png)

2. Eseguire quindi una delle operazioni seguenti con:

   - **Tastiera**
      - Con il cursore nella dichiarazione, premere **CTRL**+**.** per attivare il menu **Azioni rapide e refactoring**.
   - **Mouse**
      - Fare clic con il pulsante destro del mouse e scegliere il menu **Azioni rapide e refactoring**.
      - Fare clic sul pulsante ![cacciavite](media/screwdriver.png) che viene visualizzata nel margine sinistro se il cursore del testo si trova già nella riga vuota nella classe.

      ![Correzione del codice di generazione del decostruttore](media/deconstruct-codefix.png)

3. Selezionare **Genera il metodo 'MyInternalClass.Deconstruct'** per generare il decostruttore.

   ![Codice del decostruttore risultante](media/deconstruct-result.png)


## <a name="see-also"></a>Vedere anche

- [Generazione di codice](../code-generation-in-visual-studio.md)
- [Visualizzare l'anteprima delle modifiche](../../ide/preview-changes.md)
- [Suggerimenti per gli sviluppatori di .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)