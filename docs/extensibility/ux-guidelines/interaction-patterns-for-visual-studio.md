---
title: Modelli di interazione per Visual Studio | Microsoft Docs
description: Informazioni sulla libreria di modelli di interazione comuni che è possibile usare quando si compilano nuove funzionalità per Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 05/13/2020
ms.topic: reference
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7e47879db77ebe5888291e9c5b3b622ab66f85461d1993df670c5c2b22c567d3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375130"
---
# <a name="interaction-patterns-for-visual-studio"></a>Modelli di interazione per Visual Studio
## <a name="overview"></a>Panoramica
 Uno schema progettuale, in generale, è il nucleo di una progettazione che può essere applicata in situazioni specifiche per risolvere i problemi con set di vincoli simili. I progettisti di funzionalità e sistemi usano questi schemi progettuali come punti di partenza, che possono quindi essere adattati alla situazione specifica.

 Visual Studio ha una libreria di modelli di interazione comuni che devono essere considerati durante la creazione di nuove funzionalità. Esistono due contesti di base per i modelli di progettazione: Visual Studio Client (devenv) e GitHub Codespaces (in precedenza Visual Studio Online). Per alcuni problemi di progettazione, esiste un modello comune che funziona bene in tutte le situazioni. In molti casi, tuttavia, la soluzione potrebbe essere diversa per l'interfaccia utente presentata all'interno di un browser e quella ospitata in un'applicazione client.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio Tipi di modelli client

|Tipo di criterio|Descrizione|Esempi|
|------------------|-----------------|--------------|
|**Modelli a livello di applicazione**|Modelli di alto livello comuni all'applicazione, che determinano o visualizzano il contesto dell'applicazione e contengono pattern compositi e di controllo al loro interno|- Finestre degli strumenti<br />- Finestre dei documenti|
|**Modelli compositi**|Modelli comuni che possono estendersi tra modelli di applicazione o un modello riconosciuto costituito da diversi controlli in una configurazione distinta|- Cambio di visualizzazione<br />- Generatori di elenchi<br />- Visualizzazione dei dati<br />- Notifiche<br />- Convalida<br />- Modelli di selezione|
|**Pattern di controllo**|Specifiche sul comportamento previsto dei controlli di basso livello|- Visualizzazioni albero<br />- Modifica all'interno di un controllo griglia|

## <a name="application-patterns"></a>Modelli di applicazione
 A livello elevato, l'interfaccia Visual Studio è costituita da più finestre, finestre di dialogo, comandi e barre degli strumenti all'interno di un singolo IDE. La gerarchia Visual Studio determina il contesto e i menu delle unità. I punti di integrazione principali nell'interfaccia utente dell'IDE sono finestre dei documenti, finestre degli strumenti, progetti, struttura dei comandi, editor di testo, casella degli strumenti, Finestra Proprietà e Strumenti > opzioni.

 Esistono modelli di utilizzo di base per ognuno dei punti di integrazione principali nell'interfaccia utente dell'IDE:

- [Menu e comandi per Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Modelli delle applicazioni per Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interazioni tra finestre](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Finestre degli strumenti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Convenzioni dell'editor di documenti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Dialoghi](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Progetti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Pattern di controllo comuni
 I pattern di controllo riguardano principalmente il comportamento previsto dei singoli controlli. Si tratta di un'area in cui la coerenza è più critica.

 I controlli più comuni in Visual Studio devono seguire le linee guida per l'Windows desktop. Le linee guida includono solo aree in cui è necessario ampliare le convenzioni comuni con interazioni specifiche di Visual Studio o posizioni in cui vengono sostituite interamente le linee guida per personalizzare Visual Studio per soddisfare le esigenze degli utenti sofisticati.

- [Modelli dei controlli comuni per Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Controlli comuni](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Controlli di testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Pulsanti e collegamenti ipertestuali](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Modelli compositi
 Esistono diversi modi in cui gli utenti si aspettano di eseguire attività. Laddove possibile, le funzionalità devono essere progettate per usare tali modelli sia per l'interazione che per la progettazione visiva.

 Anche se esistono molti modelli compositi all Visual Studio, alcuni dei più importanti per quanto riguarda la coerenza sono:

- [Modelli compositi per Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Interfaccia utente su oggetto e visualizzazione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modelli di selezione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Persistenza e salvataggio delle impostazioni](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Input tocco](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
