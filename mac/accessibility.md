---
title: Accessibilità
description: Questo articolo descrive le funzionalità di accessibilità in Visual Studio per Mac e il modo in cui possono essere abilitate.
author: conceptdev
ms.author: crdun
ms.date: 04/17/2019
ms.assetid: 2C4AAC2E-3B4A-4496-8BE0-1F5A7F81D1CA
ms.openlocfilehash: 0ee6ffc7bd1567a86bc361f55e00c52ccecddd61
ms.sourcegitcommit: 75807551ea14c5a37aa07dd93a170b02fc67bc8c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2019
ms.locfileid: "67824453"
---
# <a name="accessibility"></a>Accessibilità

Visual Studio per Mac include le funzionalità di accessibilità seguenti che rendono il programma più accessibile per gli utenti diversamente abili:

- Ingrandimento del testo nei riquadri della soluzione e dell'editor
- Opzioni per la dimensione del testo negli editor
- Personalizzazione dei colori negli editor
- Navigazione tramite tastiera
- Personalizzazione dei tasti di scelta rapida
- Completamento del codice per metodi e parametri

Oltre a queste funzionalità, Apple offre una serie di strumenti per assistere gli utenti con esigenze particolari, come VoiceOver e Dictation.

Per altre informazioni sulle funzionalità di accessibilità in macOS, vedere il [sito Web di Apple](https://www.apple.com/accessibility/mac/).

## <a name="enabling-macos-assistive-technologies-in-visual-studio-for-mac"></a>Abilitazione delle funzionalità di Assistive Technology di macOS in Visual Studio per Mac

Il supporto di Visual Studio per Mac per le funzionalità di Assistive Technology di macOS è disattivato per impostazione predefinita. Per attivarlo, attenersi alle seguente procedura:

1. Passare a **Visual Studio (menu) > Preferenze > Altro > Accessibilità**

2. Selezionare la casella di controllo **Abilita accessibilità**:

   ![Casella di controllo per le preferenze di accessibilità](media/accessibility-preferences.png)

3. Selezionare il pulsante **Riavvia Visual Studio** per riavviare Visual Studio e abilitare il supporto per le funzionalità di Assistive Technology di Apple.

## <a name="how-to-use-keyboard-navigation"></a>Procedura: Usare la navigazione tramite tastiera

Il supporto per la navigazione tramite tastiera è integrato in macOS, ma per disporre dell'esperienza più completa è necessario impostare macOS per la navigazione di **tutti i controlli**:

![Preferenze di sistema - Tastiera - Tutti i controlli](media/accessibility-preferences-keyboard.png)

L'impostazione di **Accesso completo tramite tastiera** su **Tutti i controlli** consente di spostarsi tra tutti i controlli in una finestra o una finestra di dialogo. È quindi possibile selezionare i controlli usando:

- Tabulatore per spostarsi in avanti tra i controlli
- Maiuscole-Tabulatore per spostarsi indietro tra i controlli
- Tasti freccia per spostarsi tra i controlli nella direzione delle frecce
- CTRL+TAB per uscire dalle caselle con un'area di testo
- Premendo BARRA SPAZIATRICE, viene attivato il controllo con lo stato attivo.

## <a name="how-to-enable-and-use-voiceover"></a>Procedura: Abilitare e usare la funzionalità VoiceOver

Per abilitare o disabilitare VoiceOver, premere **&#8984;+F5**

I comandi di VoiceOver sono riportati in questa guida come **VO+*tasto***, dove **VO** si riferisce al modificatore impostato nell'applicazione **Utility VoiceOver**. Il modificatore predefinito è **CTRL+ALT**. Ad esempio, a seconda del modificatore di VoiceOver, **VO+M** indica **CTRL+ALT+M**. Per brevità, i tasti cursore sanno denominati **SINISTRA**, **DESTRA** e così via.

Per spostarsi all'interno dell'interfaccia utente di Visual Studio per Mac, usare le combinazioni di tasti seguenti:

- **VO+DESTRA/SINISTRA**: spostarsi tra gli elementi dell'interfaccia utente
  - VoiceOver pronuncerà l'etichetta e il tipo di controllo e descriverà come interagire con tale controllo.
- **VO+MAIUSC+GIÙ/SU**: passare a/da un elemento
  - Una volta all'interno di un elemento, è possibile usare **VO+SINISTRA/DESTRA** per spostarsi tra gli elementi in esso contenuti.
- **VO+BARRA SPAZIATRICE**: selezionare/interagire con un controllo
- **VO+M**: interagire con la barra dei menu di Visual Studio per Mac

Per altre informazioni sull'uso di VoiceOver e un elenco completo dei comandi, fare riferimento alle guide seguenti:

- [Apple VoiceOver Getting Started Guide](https://support.apple.com/en-us/guide/voiceover-guide/welcome/web) (Guida introduttiva ad Apple VoiceOver)
- [VoiceOver commands in macOS](http://lab.dotjay.com/notes/voiceover-commands/) (Comandi di VoiceOver in macOS)

## <a name="see-also"></a>Vedere anche

- [Funzionalità di accessibilità di Visual Studio (in Windows)](/visualstudio/ide/reference/accessibility-features-of-visual-studio)
