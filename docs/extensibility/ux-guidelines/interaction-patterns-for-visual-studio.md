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
ms.openlocfilehash: 5bc1d93d4b99b99a2a833d3301f32a5005d6dda3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122152042"
---
# <a name="interaction-patterns-for-visual-studio"></a>Modelli di interazione per Visual Studio
## <a name="overview"></a>Panoramica
 Un modello di progettazione, in generale, è il nucleo di una progettazione che può essere applicata in situazioni specifiche per risolvere i problemi con set di vincoli simili. I progettisti di funzionalità e sistemi usano questi modelli di progettazione come punti di partenza, che possono quindi essere adattati alla propria situazione specifica.

 Visual Studio ha una libreria di modelli di interazione comuni che devono essere considerati quando si compilano nuove funzionalità. Esistono due contesti di base per i modelli di progettazione: Visual Studio Client (devenv) e GitHub Codespaces (in precedenza Visual Studio Online). Per alcuni problemi di progettazione, esiste un modello onnipresente che funziona bene in tutte le situazioni. In molti casi, tuttavia, la soluzione potrebbe essere diversa per l'interfaccia utente presentata all'interno di un browser e quella ospitata in un'applicazione client.

### <a name="visual-studio-client-pattern-types"></a>Visual Studio Tipi di modello client

|Tipo di modello|Descrizione|Esempi|
|------------------|-----------------|--------------|
|**Modelli a livello di applicazione**|Modelli di alto livello comuni all'applicazione, che determinano o visualizzano il contesto dell'applicazione e contengono modelli compositi e di controllo al loro interno|- Finestre degli strumenti<br />- Finestre del documento|
|**Modelli compositi**|Modelli comuni che possono estendersi tra modelli di applicazione o un modello riconosciuto costituito da diversi controlli in una configurazione distinta|- Cambio di visualizzazione<br />- Generatori di elenchi<br />- Visualizzazione dei dati<br />- Notifiche<br />- Convalida<br />- Modelli di selezione|
|**Pattern di controllo**|Specifiche sul comportamento previsto dei controlli di basso livello|- Visualizzazioni albero<br />- Modifica all'interno di un controllo griglia|

## <a name="application-patterns"></a>Modelli di applicazione
 A livello di alto livello, l'Visual Studio è costituita da più finestre, finestre di dialogo, comandi e barre degli strumenti all'interno di un singolo IDE. La Visual Studio gerarchia determina il contesto e guida i menu. I punti di integrazione chiave nell'interfaccia utente dell'IDE sono finestre del documento, finestre degli strumenti, progetti, struttura dei comandi, editor di testo, casella degli strumenti, Finestra Proprietà e Strumenti > opzioni.

 Esistono modelli di utilizzo di base per ognuno dei punti di integrazione chiave nell'interfaccia utente dell'IDE:

- [Menu e comandi per Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Modelli delle applicazioni per Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interazioni tra finestre](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Finestre degli strumenti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Convenzioni dell'editor di documenti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Dialoghi](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Progetti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Pattern di controllo comuni
 I pattern di controllo riguardano principalmente il comportamento dei singoli controlli. Si tratta di un'area in cui la coerenza è più importante.

 I controlli più comuni in Visual Studio devono seguire le linee guida Windows desktop. Le linee guida includono solo aree in cui è necessario aumentare le convenzioni comuni con interazioni specifiche di Visual Studio o luoghi in cui le linee guida vengono sostituite interamente per adattare Visual Studio alle esigenze degli utenti sofisticati.

- [Modelli dei controlli comuni per Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Controlli comuni](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Controlli di testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Pulsanti e collegamenti ipertestuali](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Modelli compositi
 Esistono diversi modi in cui gli utenti prevedono di eseguire attività. Laddove possibile, le funzionalità devono essere progettate per usare questi modelli sia per l'interazione che per la progettazione visiva.

 Anche se esistono molti modelli compositi all'interno Visual Studio, alcuni dei più importanti per quanto riguarda la coerenza sono:

- [Modelli compositi per Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Interfaccia utente e visualizzazione in base all'oggetto](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modelli di selezione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Persistenza e salvataggio delle impostazioni](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Input tocco](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
