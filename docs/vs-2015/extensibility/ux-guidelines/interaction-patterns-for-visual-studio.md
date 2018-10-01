---
title: Modelli di interazione per Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a3643792-b0df-481c-bc35-576f948e04cf
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: cf21a8aa3c2a2813c71907d1d79bdcd4f7cde323
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527028"
---
# <a name="interaction-patterns-for-visual-studio"></a>Modelli di interazione per Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [modelli di interazione per Visual Studio](https://docs.microsoft.com/visualstudio/extensibility/ux-guidelines/interaction-patterns-for-visual-studio).  
  
## <a name="overview"></a>Panoramica  
 Un modello di progettazione, in generale, è la base di una progettazione che può essere applicata in situazioni specifiche per risolvere i problemi con i set analogo di vincoli. Finestre di progettazione di funzionalità e sistema di usare questi schemi progettuali come punti, che quindi possono essere adattati alle loro esigenze di partenza.  
  
 Visual Studio include una libreria di modelli di interazione comune da considerare durante la creazione di nuove funzionalità. Esistono due contesti di core per i modelli di progettazione: Client (devenv) di Visual Studio e Visual Studio Online. Per alcuni problemi di progettazione, è disponibile un modello comune che funziona correttamente in tutte le situazioni. In molti casi, tuttavia, la soluzione potrebbe essere diversa per l'interfaccia utente che viene presentata all'interno di un browser e di cui è ospitato in un'applicazione client.  
  
### <a name="visual-studio-client-pattern-types"></a>Tipi di modelli Visual Studio Client  
  
|Tipo di modello|Descrizione|Esempi|  
|------------------|-----------------|--------------|  
|**Modelli a livello di applicazione**|Modelli di alto livello comuni per l'applicazione, che determina o visualizzazione di contesto dell'applicazione e contenente composita e pattern di controllo al loro interno|-Finestre degli strumenti<br />: Le finestre dei documenti|  
|**Pattern compositi**|Modelli comuni che possono estendersi tra i modelli di applicazione o un modello riconosciuto costituito da diversi controlli in una configurazione distinct|-Altra vista<br />-I generatori list<br />-Visualizzazione di dati<br />-Notifiche<br />-Convalida<br />-Modelli selezione|  
|**Pattern di controllo**|Informazioni specifiche sui controlli a basso livello come si prevede un comportamento|: Visualizzazioni dell'albero<br />-Modifica all'interno di un controllo griglia|  
  
## <a name="application-patterns"></a>Modelli di applicazione  
 A livello generale, l'interfaccia di Visual Studio è costituito da più finestre, finestre di dialogo, comandi e le barre degli strumenti all'interno di un unico IDE. La gerarchia di Visual Studio determina i menu di contesto e le unità. I punti di integrazione principali nell'interfaccia utente dell'IDE sono finestre dei documenti, finestre degli strumenti, progetti, la struttura del comando, l'editor di testo, casella degli strumenti, la finestra proprietà e gli strumenti > Opzioni.  
  
 Sono disponibili modelli di utilizzo di base per ognuno dei punti di integrazione principali nell'interfaccia utente dell'IDE:  
  
-   [Menu e comandi per Visual Studio](../../extensibility/ux-guidelines/menus-and-commands-for-visual-studio.md)  
  
-   [Modelli delle applicazioni per Visual Studio](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md)  
  
    -   [Interazioni di finestra](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_WindowInteractions)  
  
    -   [Finestre degli strumenti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_ToolWindows)  
  
    -   [Convenzioni dell'editor di documento](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_DocumentEditorConventions)  
  
    -   [Dialogs](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Dialogs) (Finestre di dialogo)  
  
    -   [Progetti](../../extensibility/ux-guidelines/application-patterns-for-visual-studio.md#BKMK_Projects)  
  
## <a name="common-control-patterns"></a>Pattern di controllo comuni  
 I pattern di controllo sono principalmente sui controlli dei singoli sono previsti un comportamento. Si tratta di un'area in cui è più importante della coerenza.  
  
 Controlli più comuni in Visual Studio devono seguire le linee guida per Windows Desktop. Le linee guida includono solo le aree in cui è necessario aumentare le convenzioni comuni con le interazioni di specifiche di Visual Studio o posizioni in cui si sostituiscono le linee guida interamente per personalizzare Visual Studio per soddisfare le esigenze dei nostri utenti sofisticate.  
  
-   [Modelli dei controlli comuni per Visual Studio](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md)  
  
    -   [Controlli comuni](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_CommonControls)  
  
    -   [Controlli testo](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_TextControls)  
  
    -   [I collegamenti ipertestuali e pulsanti](../../extensibility/ux-guidelines/common-control-patterns-for-visual-studio.md#BKMK_ButtonsAndHyperlinks)  
  
## <a name="composite-patterns"></a>Pattern compositi  
 Esistono numerosi modi in cui gli utenti si aspettano per eseguire le attività. Laddove possibile, le funzionalità devono essere progettate per utilizzare tali modelli per l'interazione e progettazione visiva.  
  
 Sebbene esistano numerosi modelli compositi all'interno di Visual Studio, alcuni dei più importanti per quanto riguarda la coerenza sono:  
  
-   [Modelli compositi per Visual Studio](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md)  
  
    -   [Per gli oggetti dell'interfaccia utente e la lettura](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_OnObjectUI)  
  
    -   [Modelli di selezione](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_SelectionModels)  
  
    -   [Persistenza e il salvataggio delle impostazioni](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_PersistenceAndSavingSettings)  
  
    -   [Input tocco](../../extensibility/ux-guidelines/composite-patterns-for-visual-studio.md#BKMK_TouchInput)

