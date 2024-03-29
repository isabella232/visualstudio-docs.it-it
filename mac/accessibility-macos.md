---
title: Uso delle opzioni di accessibilità di macOS
description: Uso di funzionalità e opzioni di accessibilità di macOS, ad esempio contrasto elevato, navigazione tramite tastiera e VoiceOver
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/23/2019
ms.assetid: 598FC25A-6DA3-44BB-B128-AD979E9F86EA
ms.topic: how-to
ms.openlocfilehash: 6796ab12716d1d2f3ec2570c32b410c8360b8a81
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710497"
---
# <a name="accessibility-features-of-macos"></a>Funzionalità di accessibilità di macOS

macOS è un sistema operativo accessibile, con diverse funzionalità per assistere gli utenti con diverse capacità. Queste funzionalità includono una modalità a contrasto elevato, la navigazione tramite tastiera e VoiceOver (utilità per la lettura dello schermo macOS).

## <a name="enable-accessibility-features"></a>Abilitare le funzionalità di accessibilità

In Visual Studio per Mac, il supporto per le tecnologie di assistive è disattivato per impostazione predefinita. Per abilitare il supporto dell'accessibilità:

1. Passare a **Visual Studio (menu)**  >  **Preferenze**  >  **Altro** e selezionare **Accessibilità**.

1. Selezionare la **casella di controllo Abilita** accessibilità.

   ![Screenshot delle preferenze di accessibilità, con l'opzione Abilita accessibilità selezionata](media/accessibility-preferences.png)

1. Selezionare **Riavvia Visual Studio** per abilitare il supporto per le tecnologie di assistive di Apple.

In alternativa, è possibile usare la riga di comando per abilitare le funzionalità di accessibilità. A tale scopo, immettere il comando seguente nel terminale:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Dopo aver modificato questa impostazione tramite la riga di comando, è necessario riavviare Visual Studio.

## <a name="increase-the-contrast-in-macos"></a>Aumentare il contrasto in macOS

Visual Studio per Mac supporta un maggiore contrasto in macOS, aumentando il contrasto degli elementi dell'interfaccia utente e rendendo più definiti i contorni. Per abilitare questa funzionalità:

1. Aprire **Preferenze di sistema**.

1. Passare a **Accessibilità** e selezionare **Visualizza.**

1. Selezionare la **casella di controllo Aumenta** contrasto.
