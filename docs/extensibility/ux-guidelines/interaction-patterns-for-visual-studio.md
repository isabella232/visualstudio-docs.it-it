---
title: Modelli di interazione per Visual Studio . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac917aeb2530570b755e7f1e6fc6de00714a54b0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698368"
---
# <a name="interaction-patterns-for-visual-studio"></a>Modelli di interazione per Visual Studio
## <a name="overview"></a>Panoramica
 Un modello di progettazione, in generale, è il nucleo di un progetto che può essere applicato in situazioni specifiche per risolvere problemi con insiemi di vincoli simili. I progettisti di funzionalità e sistemi utilizzano questi modelli di progettazione come punti di partenza, che possono quindi essere adattati alla loro situazione specifica.

 Visual Studio dispone di una libreria di modelli di interazione comuni che devono essere considerati durante la creazione di nuove funzionalità. Esistono due contesti principali per i modelli di progettazione: Visual Studio Client (devenv) e Visual Studio Online.There are two core contexts for our design patterns: Visual Studio Client (devenv) and Visual Studio Online. Per alcuni problemi di progettazione, c'è un modello onnipresente che funziona bene in tutte le situazioni. In molti casi, tuttavia, la soluzione potrebbe essere diversa per l'interfaccia utente che viene presentata all'interno di un browser e ciò che è ospitato in un'applicazione client.

### <a name="visual-studio-client-pattern-types"></a>Tipi di modello client di Visual StudioVisual Studio Client pattern types

|Tipo di modello|Descrizione|Esempi|
|------------------|-----------------|--------------|
|**Modelli a livello di applicazioneApplication-level patterns**|Modelli di alto livello comuni all'applicazione, determinare o visualizzare il contesto dell'applicazione e contenere i pattern compositi e di controllo al loro interno|- Finestre degli utensili<br />- Finestre dei documenti|
|**Modelli compositi**|Modelli comuni che possono estendersi tra modelli di applicazione o un modello riconosciuto costituito da diversi controlli in una configurazione distintaCommon patterns that may span across application patterns, or a recognized pattern made up of several controls in a distinct configuration|- Commutazione vista<br />- Costruttori di liste<br />- Visualizzazione dei dati<br />- Notifiche<br />- Convalida<br />- Modelli di selezione|
|**Pattern di controllo**|Specifiche sul comportamento previsto dei controlli di basso livello|- Viste sugli alberi<br />- Modifica all'interno di un controllo griglia|

## <a name="application-patterns"></a>Modelli di applicazione
 A livello generale, l'interfaccia di Visual Studio comprende più finestre, finestre di dialogo, comandi e barre degli strumenti all'interno di un singolo IDE. La gerarchia di Visual Studio determina il contesto e le unità menu. I punti di integrazione chiave nell'interfaccia utente dell'IDE sono finestre di documento, finestre degli strumenti, progetti, la struttura dei comandi, l'editor di testo, la casella degli strumenti, la finestra Proprietà e Strumenti > Opzioni.

 Esistono modelli di utilizzo di base per ognuno dei punti di integrazione chiave nell'interfaccia utente dell'IDE:There are basic usage patterns for each of the key integration points in the user interface of the IDE:

- [Menu e comandi per Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Modelli delle applicazioni per Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interazioni con le finestre](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Finestre degli strumenti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Convenzioni dell'editor di documenti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Finestre di dialogo](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Progetti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Pattern di controllo comuni
 I pattern di controllo riguardano principalmente il comportamento previsto dei singoli controlli. Questo è un settore in cui la coerenza è più critica.

 I controlli più comuni in Visual Studio devono seguire le linee guida di Windows per il desktop. Le nostre linee guida includono solo le aree in cui è necessario aumentare le convenzioni comuni con le interazioni specifiche di Visual Studio o luoghi in cui sostituiamo completamente le linee guida al fine di personalizzare Visual Studio per soddisfare le esigenze dei nostri utenti sofisticati.

- [Modelli dei controlli comuni per Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Controlli comuni](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Controlli testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Pulsanti e collegamenti ipertestuali](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Modelli compositi
 Esistono diversi modi in cui gli utenti si aspettano di eseguire attività. Ove possibile, le funzionalità devono essere progettate per utilizzare tali modelli sia per l'interazione che per la progettazione visiva.

 Sebbene siano presenti molti modelli compositi all'interno di Visual Studio, alcuni dei più importanti per quanto riguarda la coerenza sono:While there are many composite patterns within Visual Studio, some of the most important per regards to consistency are:

- [Modelli compositi per Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Interfaccia utente per gli oggetti e visualizzazione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modelli di selezione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Persistenza e salvataggio delle impostazioni](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Ingresso tocco](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
