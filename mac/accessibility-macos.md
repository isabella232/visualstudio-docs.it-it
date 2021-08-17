---
title: Uso delle opzioni di accessibilità macOS
description: Uso di funzionalità e opzioni di accessibilità macOS, ad esempio contrasto elevato, spostamento tramite tastiera e VoiceOver
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/23/2019
ms.assetid: 598FC25A-6DA3-44BB-B128-AD979E9F86EA
ms.topic: how-to
ms.openlocfilehash: e03a4271ee81213ac387b58603acdb5053a50a524a741a4c60b50990ce0cd2f1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121349997"
---
# <a name="accessibility-features-of-macos"></a>Funzionalità di accessibilità di macOS

macOS è un sistema operativo accessibile, con una serie di funzionalità per assistere gli utenti con diverse capacità. Queste funzionalità includono una modalità a contrasto elevato, lo spostamento tramite tastiera e VoiceOver (l'utilità per la lettura dello schermo macOS).

## <a name="enable-accessibility-features"></a>Abilitare le funzionalità di accessibilità

In Visual Studio per Mac, il supporto per assistive technology è disattivato per impostazione predefinita. Per abilitare il supporto dell'accessibilità:

1. Passare a **Visual Studio (menu)**  >  **Preferenze**  >  **Altro** e selezionare **Accessibilità.**

1. Selezionare la **casella di controllo Abilita** accessibilità.

   ![Screenshot delle preferenze di accessibilità, con l'opzione Abilita accessibilità selezionata](media/accessibility-preferences.png)

1. Selezionare **Riavvia Visual Studio** per abilitare il supporto per le assistive technology di Apple.

In alternativa, è possibile usare la riga di comando per abilitare le funzionalità di accessibilità. A tale scopo, immettere il comando seguente nel terminale:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Dopo aver modificato questa impostazione tramite la riga di comando, è necessario riavviare Visual Studio.

## <a name="increase-the-contrast-in-macos"></a>Aumentare il contrasto in macOS

Visual Studio per Mac supporta un maggiore contrasto in macOS, aumentando il contrasto degli elementi dell'interfaccia utente e rendendo più definiti i contorni. A tale scopo:

1. Aprire **Preferenze di Sistema**.

1. Passare a **Accessibilità** e selezionare **Visualizza.**

1. Selezionare la casella **di controllo Aumenta** contrasto .
