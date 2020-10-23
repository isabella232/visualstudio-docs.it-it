---
title: Modelli di interazione per Visual Studio | Microsoft Docs
ms.date: 05/13/2020
ms.topic: conceptual
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a5376c1edf2c87ece78d966bede05b60cc0b6bab
ms.sourcegitcommit: bf5e2bba5acdcf05869b861211f8bb755081e5ce
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2020
ms.locfileid: "92467648"
---
# <a name="interaction-patterns-for-visual-studio"></a>Modelli di interazione per Visual Studio
## <a name="overview"></a>Panoramica
 Uno schema progettuale, in generale, è il nucleo di una progettazione che può essere applicata in situazioni specifiche per risolvere i problemi relativi a set di vincoli simili. I progettisti di funzionalità e di sistema utilizzano questi modelli di progettazione come punti di partenza, che possono essere adattati alla situazione specifica.

 Visual Studio include una libreria di modelli di interazione comuni che devono essere presi in considerazione quando si compilano nuove funzionalità. Sono disponibili due contesti di base per i nostri modelli di progettazione: Visual Studio client (devenv) e gli spazi dei messaggi di GitHub (in precedenza Visual Studio online). Per alcuni problemi di progettazione, è disponibile un modello onnipresente che funziona correttamente in tutte le situazioni. In molti casi, tuttavia, la soluzione potrebbe essere diversa per l'interfaccia utente presentata in un browser e ospitata in un'applicazione client.

### <a name="visual-studio-client-pattern-types"></a>Tipi di modelli client di Visual Studio

|Tipo di modello|Descrizione|Esempi|
|------------------|-----------------|--------------|
|**Modelli a livello di applicazione**|Modelli di alto livello comuni all'applicazione, determinazione o visualizzazione del contesto dell'applicazione e contenente i pattern di controllo e compositi al loro interno|-Finestre degli strumenti<br />-Finestre documenti|
|**Modelli compositi**|Modelli comuni che possono estendersi tra modelli di applicazione o un modello riconosciuto costituito da diversi controlli in una configurazione distinta|-Visualizzazione cambio<br />-Elenca i generatori<br />-Visualizzazione dei dati<br />-Notifiche<br />-Convalida<br />-Modelli di selezione|
|**Pattern di controllo**|Specifiche relative al comportamento previsto per i controlli di basso livello|-Visualizzazioni albero<br />-Modifica all'interno di un controllo Grid|

## <a name="application-patterns"></a>Modelli di applicazione
 A livello generale, l'interfaccia di Visual Studio comprende più finestre, finestre di dialogo, comandi e barre degli strumenti all'interno di un singolo IDE. La gerarchia di Visual Studio determina i menu del contesto e delle unità. I punti di integrazione principali nell'interfaccia utente dell'IDE sono le finestre dei documenti, le finestre degli strumenti, i progetti, la struttura del comando, l'editor di testo, la casella degli strumenti, il Finestra Proprietà e gli strumenti > opzioni.

 Sono disponibili modelli di utilizzo di base per ognuno dei punti di integrazione principali nell'interfaccia utente dell'IDE:

- [Menu e comandi per Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)

- [Modelli delle applicazioni per Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)

  - [Interazioni finestra](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)

  - [Finestre degli strumenti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)

  - [Convenzioni dell'editor di documenti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)

  - [Dialoghi](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs)

  - [Progetti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)

## <a name="common-control-patterns"></a>Pattern di controllo comuni
 I pattern di controllo prevedono principalmente il comportamento dei singoli controlli. Si tratta di un'area in cui la coerenza è più critica.

 I controlli più comuni in Visual Studio devono seguire le linee guida di Windows desktop. Le linee guida includono solo aree in cui è necessario aumentare le convenzioni comuni con interazioni specifiche di Visual Studio o posizioni in cui le linee guida vengono sostituite interamente per adattare Visual Studio in modo da soddisfare le esigenze degli utenti sofisticati.

- [Modelli dei controlli comuni per Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)

  - [Controlli comuni](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)

  - [Controlli di testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)

  - [Pulsanti e collegamenti ipertestuali](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)

## <a name="composite-patterns"></a>Modelli compositi
 Esistono diversi modi in cui gli utenti si aspettano di eseguire le attività. Laddove possibile, le funzionalità devono essere progettate in modo da usare tali modelli per l'interazione e la progettazione visiva.

 Sebbene esistano molti modelli compositi all'interno di Visual Studio, alcuni dei più importanti per quanto riguarda la coerenza sono:

- [Modelli compositi per Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)

  - [Interfaccia utente e visualizzazione in oggetto](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)

  - [Modelli di selezione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)

  - [Persistenza e salvataggio delle impostazioni](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)

  - [Input tocco](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)
