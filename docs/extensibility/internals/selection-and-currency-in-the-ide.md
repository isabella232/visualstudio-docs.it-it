---
title: Selezione e valuta nell'IDE Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f580b7c8e1651dcbcd053476ae756399a0ac3482
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705576"
---
# <a name="selection-and-currency-in-the-ide"></a>Selezione e valuta nell'IDE
L'ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di sviluppo integrato (IDE) gestisce le informazioni sugli oggetti attualmente selezionati degli utenti utilizzando il *contesto*di selezione . Con il contesto di selezione, VSPackage possono prendere parte al rilevamento della valuta in due modi:With selection context, VSPackages can take part in currency tracking in two ways:

- Propagando le informazioni di valuta sui package VS all'IDE.

- Monitorando le selezioni attualmente attive degli utenti all'interno dell'IDE.

## <a name="selection-context"></a>Contesto di selezione
 L'IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tiene traccia a livello globale della valuta IDE nel proprio oggetto di contesto di selezione globale. Nella tabella seguente vengono illustrati gli elementi che costituiscono il contesto di selezione.

|Elemento|Descrizione|
|-------------|-----------------|
|Gerarchia corrente|In genere il progetto corrente; una gerarchia corrente NULL indica che la soluzione nel suo complesso è corrente.|
|ItemID corrente|L'elemento selezionato all'interno della gerarchia corrente; quando sono presenti più selezioni in una finestra di progetto, possono essere presenti più elementi correnti.|
|Corrente`SelectionContainer`|Contiene uno o più oggetti per i quali nella finestra Proprietà devono essere visualizzate le proprietà.|

 Inoltre, l'ambiente gestisce due elenchi globali:

- Elenco di identificatori di comando dell'interfaccia utente attivi

- Elenco dei tipi di elementi attualmente attivi.

### <a name="window-types-and-selection"></a>Tipi di finestra e selezione
 L'IDE [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] organizza le finestre in due tipi generali:

- Finestre di tipo gerarchia

- Finestre cornice, ad esempio finestre degli strumenti e del documento

  L'IDE tiene traccia della valuta in modo diverso per ognuno di questi tipi di finestra.

  La finestra di tipo di progetto più comune è Esplora soluzioni, che controlla l'IDE. Una finestra di tipo di progetto tiene traccia della gerarchia globale e ItemID del contesto di selezione globale e la finestra si basa sulla selezione dell'utente per determinare la gerarchia corrente. Per le finestre di tipo progetto, <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>l'ambiente fornisce il servizio globale , tramite il quale VSPackage possono monitorare i valori correnti per gli elementi aperti. L'esplorazione delle proprietà nell'ambiente è guidata da questo servizio globale.

  Le finestre cornice, d'altra parte, usano DocObject all'interno della finestra cornice per inserire il valore SelectionContext (il trio hierarchy/ItemID/SelectionContainer). . Le finestre cornice <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> utilizzano il servizio a questo scopo. Il DocObject può eseguire il push solo i valori per il contenitore di selezione, lasciando invariati i valori locali per la gerarchia e ItemID, come è tipico per i documenti figlio MDI.

### <a name="events-and-currency"></a>Eventi e valuta
 Potrebbero verificarsi due tipi di eventi che influiscono sulla nozione di valuta dell'ambiente:

- Eventi che vengono propagati a livello globale e modificano il contesto di selezione della cornice della finestra. Esempi di questo tipo di evento includono una finestra Web MDI in fase di apertura, una finestra degli strumenti globale in fase di apertura o una finestra degli strumenti di tipo progetto.

- Eventi che modificano gli elementi tracciati all'interno del contesto di selezione della cornice della finestra. Alcuni esempi includono la modifica della selezione all'interno di un oggetto DocObject o la modifica della selezione in una finestra di tipo progetto.

## <a name="see-also"></a>Vedere anche
- [Oggetti del contesto di selezione](../../extensibility/internals/selection-context-objects.md)
- [Commenti e suggerimenti per l'utente](../../extensibility/internals/feedback-to-the-user.md)
