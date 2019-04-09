---
title: Generale, Ambiente, finestra di dialogo Opzioni
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4fdbd8c64514854aa77c358145badbf6583996f1
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647271"
---
# <a name="options-dialog-box-environment--general"></a>Finestra di dialogo Opzioni: Ambiente \> Generale

Usare questa pagina per modificare i temi di colori, le impostazioni della barra di stato e le associazioni dell'estensione di file, tra le altre opzioni, per l'ambiente di sviluppo integrato (IDE). Per accedere alla finestra di dialogo **Opzioni**, aprire il menu **Strumenti**, scegliere **Opzioni**, aprire la cartella **Ambiente** e scegliere la pagina **Generale**. Se la pagina non viene visualizzata nell'elenco, selezionare la casella di controllo **Mostra tutte le impostazioni** nella finestra di dialogo **Opzioni**.

## <a name="visual-experience"></a>Esperienza visiva

**Tema colori**

Scegliere il tema colori **Blu**, **Chiaro**, **Scuro** oppure **Blu (massimo contrasto)** per l'IDE.

È possibile installare temi predefiniti aggiuntivi e creare temi personalizzati scaricando e installando **Visual Studio Color Theme Editor** da [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Dopo avere installato questo strumento, i temi colori aggiuntivi vengono visualizzati nella casella di riepilogo **Tema colori**.

**Applica lo stile Tutte Iniziali Maiuscole alla barra dei menu**

I menu usano lo stile con tutte iniziali maiuscole per impostazione predefinita. Deselezionare questa opzione per usare invece lo stile con tutte lettere maiuscole.

::: moniker range=">=vs-2019"

**Ottimizza il rendering per schermi con densità pixel diverse (richiede il riavvio)**

Questa opzione abilita o disabilita la sensibilità ai valori DPI (punti per pollice) per monitor (o *PMA*). Quando la funzionalità PMA è abilitata, l'interfaccia utente di Visual Studio viene visualizzata in modo nitido con qualsiasi fattore di scala di visualizzazione e configurazione DPI, anche su più monitor. Per abilitare PMA, sono necessari Windows 10 April 2018 Update o versioni successive e .NET Framework 4.8 o versioni successive. (Questa opzione risulta inattiva se i due prerequisiti non sono soddisfatti.)

::: moniker-end

**Regola automaticamente esperienza visiva in base alle prestazioni del client**

Specifica se Visual Studio imposta automaticamente la regolazione dell'esperienza visiva o la regolazione viene impostata in modo esplicito dall'utente. Questa regolazione può modificare la visualizzazione di colori da gradienti a colori uniformi o può limitare l'uso di animazioni nei menu o finestre a comparsa.

**Abilita esperienza visiva dettagliata del client**

Consente l'esperienza visiva completa di Visual Studio, inclusi i gradienti e le animazioni. Deselezionare questa opzione se si usano Connessioni desktop remoto o schede grafiche obsolete, perché le prestazioni di queste funzionalità potrebbero risultare compromesse. Questa opzione è disponibile solo se si deseleziona l'opzione **Regola automaticamente esperienza visiva in base alle prestazioni del client**.

**Usa accelerazione grafica hardware se disponibile**

Usa l'accelerazione grafica hardware, se disponibile, piuttosto che l'accelerazione software.

## <a name="other"></a>Altro

**Elementi da mostrare nel menu Finestra**

Consente di personalizzare il numero di finestre visualizzate nell'elenco Finestre accessibile dal menu **Finestra**. Immettere un numero compreso tra 1 e 24. Il valore predefinito è 10.

**elementi negli elenchi degli ultimi file usati**

Consente di personalizzare il numero dei file e dei progetti usati più di recente visualizzati nel menu **File**. Immettere un numero compreso tra 1 e 24. Il valore predefinito è 10. Questa funzionalità offre un modo semplice per recuperare progetti e file usati di recente.

**Mostra barra di stato**

Consente di visualizzare la barra di stato. Nella barra di stato, posizionata nella parte inferiore della finestra dell'IDE, sono visualizzate le informazioni sullo stato delle operazioni in corso.

**Chiudi ha effetto solo sulla finestra degli strumenti attiva**

Consente di specificare che quando si fa clic sul pulsante **Chiudi** deve essere chiusa solo la finestra degli strumenti attiva e non tutte le finestre degli strumenti del set ancorato. Questa opzione è selezionata per impostazione predefinita.

**Nascondi automaticamente ha effetto solo sulla finestra degli strumenti attiva**

Consente di specificare che se si fa clic sul pulsante **Nascondi automaticamente** deve essere nascosta automaticamente solo la finestra degli strumenti attiva e non tutte le finestre degli strumenti del set ancorato. Questa opzione è deselezionata per impostazione predefinita.

## <a name="see-also"></a>Vedere anche

- [Finestra di dialogo Opzioni ambiente](../../ide/reference/environment-options-dialog-box.md)
- [Personalizzazione del layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md)