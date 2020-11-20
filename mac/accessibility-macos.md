---
title: Uso delle opzioni di accessibilità macOS
description: Uso delle opzioni e delle funzionalità di accessibilità macOS, ad esempio contrasto elevato, navigazione da tastiera e VoiceOver
author: heiligerdankgesang
ms.author: dominicn
ms.date: 09/23/2019
ms.assetid: 598FC25A-6DA3-44BB-B128-AD979E9F86EA
ms.topic: how-to
ms.openlocfilehash: 6796ab12716d1d2f3ec2570c32b410c8360b8a81
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998386"
---
# <a name="accessibility-features-of-macos"></a>Funzionalità di accessibilità di macOS

macOS è un sistema operativo accessibile, con numerose funzionalità che consentono agli utenti di variare le capacità. Queste funzionalità includono la modalità a contrasto elevato, la navigazione da tastiera e la voce VoiceOver (lettore di schermo macOS).

## <a name="enable-accessibility-features"></a>Abilitare le funzionalità di accessibilità

In Visual Studio per Mac il supporto per le tecnologie per l'accesso facilitato è disattivato per impostazione predefinita. Per abilitare il supporto per l'accessibilità:

1. Passare a **Visual Studio (menu)**  >  **Preferenze**  >  **altro** e selezionare **accessibilità**.

1. Selezionare la casella di controllo **Abilita accessibilità** .

   ![Screenshot delle preferenze di accessibilità, con Abilita accessibilità selezionata](media/accessibility-preferences.png)

1. Selezionare **riavvia Visual Studio** per abilitare il supporto per le tecnologie per l'accesso facilitato di Apple.

In alternativa, è possibile usare la riga di comando per abilitare le funzionalità di accessibilità. A tale scopo, immettere il comando seguente nel terminale:

```bash
defaults write com.microsoft.visual-studio com.monodevelop.AccessibilityEnabled 1
```

Dopo aver modificato questa impostazione tramite la riga di comando, sarà necessario riavviare Visual Studio.

## <a name="increase-the-contrast-in-macos"></a>Aumentare il contrasto in macOS

Visual Studio per Mac supporta un maggiore contrasto in macOS, aumentando il contrasto degli elementi dell'interfaccia utente e rendendo più definiti i profili. Per abilitare questa operazione:

1. Aprire **Preferenze di sistema**.

1. Passare a **accessibilità** e selezionare **Visualizza**.

1. Selezionare la casella di controllo **Aumenta contrasto** .
