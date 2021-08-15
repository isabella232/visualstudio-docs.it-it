---
title: Generale, Ambiente, finestra di dialogo Opzioni
description: Informazioni su come usare la pagina Generale nella sezione Ambiente per modificare i temi dei colori, le impostazioni della barra di stato, le associazioni delle estensioni di file e altro ancora per l'IDE.
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.Environment.General
- VS.Message.0x800a002e
- VS.OptionsDialog.Environment
- VS.ToolsOptionsPages.Environment
- VS.ToolsOptionsPages.Environment.General
helpviewer_keywords:
- recently used file lists
- Windows menu, customizing
- status bar, displaying
- Options dialog box, General Environment
- General Environment Options dialog box
- Environment Options dialog box
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 6bc28e51942e8a1f52dbf573bdc477d081c74efb6aa714c07fc8eff351824fc1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121304229"
---
# <a name="options-dialog-box-environment--general"></a>Finestra di dialogo Opzioni: Generale \> ambiente

Usare questa pagina per modificare i temi di colori, le impostazioni della barra di stato e le associazioni dell'estensione di file, tra le altre opzioni, per l'ambiente di sviluppo integrato (IDE). Per accedere alla finestra di dialogo **Opzioni**, aprire il menu **Strumenti**, scegliere **Opzioni**, aprire la cartella **Ambiente** e scegliere la pagina **Generale**.

## <a name="visual-experience"></a>Esperienza visiva

**Tema colori**

Scegliere il tema colori **Blu**, **Chiaro**, **Scuro** oppure **Blu (massimo contrasto)** per l'IDE.

È possibile installare temi predefiniti aggiuntivi e creare temi personalizzati scaricando e installando **Visual Studio Color Theme Editor** da [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Dopo avere installato questo strumento, i temi colori aggiuntivi vengono visualizzati nella casella di riepilogo **Tema colori**.

**Applica lo stile Tutte Iniziali Maiuscole alla barra dei menu**

I menu usano lo stile con tutte iniziali maiuscole per impostazione predefinita. Deselezionare questa opzione per usare invece lo stile con tutte lettere maiuscole.

::: moniker range=">=vs-2019"

**Ottimizza il rendering per schermi con densità pixel diverse (richiede il riavvio)**

Questa opzione abilita o disabilita la sensibilità ai valori DPI (punti per pollice) per monitor (o *PMA*). Quando la funzionalità PMA è abilitata, l'interfaccia utente di Visual Studio viene visualizzata in modo nitido con qualsiasi fattore di scala di visualizzazione e configurazione DPI, anche su più monitor. Per abilitare PMA, sono necessari Windows 10 April 2018 Update o versioni successive e .NET Framework 4.8 o versioni successive. (Questa opzione risulta inattiva se i due prerequisiti non sono soddisfatti.)

> [!TIP]
> - Windows 10 include l'impostazione **Consenti a Windows di provare a risolvere i problemi delle app in modo da non essere sfocate**. L'impostazione di questa opzione di Windows su **Attivato** ha effetti trascurabili se è selezionata l'opzione **Ottimizza il rendering per schermi con densità pixel diverse**.
> - Windows 10 include anche uno **strumento di risoluzione dei problemi di compatibilità dei programmi**. Non è consigliabile provare a correggere l'aspetto di Visual Studio usando tale strumento di risoluzione dei problemi.

::: moniker-end

**Regola automaticamente in base alle prestazioni del client**

Specifica se Visual Studio imposta automaticamente la regolazione dell'esperienza visiva o la regolazione viene impostata in modo esplicito dall'utente. Questa regolazione può modificare la visualizzazione di colori da gradienti a colori uniformi o può limitare l'uso di animazioni nei menu o finestre a comparsa.

::: moniker range="vs-2017"

> [!TIP]
> Windows 10 include l'impostazione **Consenti a Windows di provare a risolvere i problemi delle app in modo da non essere sfocate**. L'impostazione di questa opzione su **Attivato** è consigliata se Visual Studio viene visualizzato sfocato sullo schermo. Prendere in considerazione l'aggiornamento a [Visual Studio 2019](https://visualstudio.microsoft.com/downloads), che include una nitidezza di visualizzazione notevolmente migliorata, essendo un'applicazione con sensibilità ai valori DPI per monitor.

::: moniker-end

**Abilita esperienza visiva dettagliata del client**

Consente l'esperienza visiva completa di Visual Studio, inclusi i gradienti e le animazioni. Deselezionare questa opzione se si usano Connessioni desktop remoto o schede grafiche obsolete, perché le prestazioni di queste funzionalità potrebbero risultare compromesse. Questa opzione è disponibile solo se si deseleziona l'opzione **Regola automaticamente esperienza visiva in base alle prestazioni del client**.

**Usa accelerazione grafica hardware se disponibile**

Usa l'accelerazione grafica hardware, se disponibile, piuttosto che l'accelerazione software.

## <a name="other"></a>Altro

**Elementi da mostrare nel menu Finestra**

Consente di personalizzare il numero di finestre visualizzate nell'elenco Finestre accessibile dal menu **Finestra**. Immettere un numero compreso tra 1 e 24. Il valore predefinito è 10.

**Elementi negli elenchi degli ultimi file usati**

Consente di personalizzare il numero dei file e dei progetti usati più di recente visualizzati nel menu **File**. Immettere un numero compreso tra 1 e 24. Il valore predefinito è 10. Questa funzionalità offre un modo semplice per recuperare progetti e file usati di recente.

**Mostra barra di stato**

Consente di visualizzare la barra di stato. Nella barra di stato, posizionata nella parte inferiore della finestra dell'IDE, sono visualizzate le informazioni sullo stato delle operazioni in corso.

**Il pulsante Chiudi si applica solo alla finestra degli strumenti attiva**

Consente di specificare che quando si fa clic sul pulsante **Chiudi** deve essere chiusa solo la finestra degli strumenti attiva e non tutte le finestre degli strumenti del set ancorato. Questa opzione è selezionata per impostazione predefinita.

**Il pulsante Nascondi automaticamente si applica solo alla finestra degli strumenti attiva**

Consente di specificare che se si fa clic sul pulsante **Nascondi automaticamente** deve essere nascosta automaticamente solo la finestra degli strumenti attiva e non tutte le finestre degli strumenti del set ancorato. Questa opzione è deselezionata per impostazione predefinita.

## <a name="see-also"></a>Vedi anche

- [Personalizzazione del layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md)
