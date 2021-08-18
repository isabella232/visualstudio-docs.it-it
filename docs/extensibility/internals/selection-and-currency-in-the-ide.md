---
title: Selezione e valuta nell'IDE | Microsoft Docs
description: Informazioni su come i pacchetti VSPackage fanno parte del rilevamento della valuta. L Visual Studio IDE gestisce le informazioni sugli oggetti attualmente selezionati usando il contesto di selezione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f540618c6b125012d332a683ba534fbaa5082990
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122049545"
---
# <a name="selection-and-currency-in-the-ide"></a>Selezione e valuta nell'IDE
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]L'ambiente di sviluppo integrato (IDE) gestisce le informazioni sugli oggetti attualmente selezionati degli utenti usando il contesto di *selezione*. Con il contesto di selezione, i pacchetti VSPackage possono partecipare al rilevamento della valuta in due modi:

- Propagando le informazioni sulla valuta relative ai pacchetti VSPackage nell'IDE.

- Monitorando le selezioni attualmente attive degli utenti all'interno dell'IDE.

## <a name="selection-context"></a>Contesto di selezione
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]L'IDE tiene traccia a livello globale della valuta IDE nel proprio oggetto contesto di selezione globale. Nella tabella seguente vengono illustrati gli elementi che costituiscono il contesto di selezione.

|Elemento|Descrizione|
|-------------|-----------------|
|Gerarchia corrente|In genere il progetto corrente; Una gerarchia corrente NULL indica che l'intera soluzione è corrente.|
|Id elemento corrente|Elemento selezionato all'interno della gerarchia corrente. Quando sono presenti più selezioni in una finestra del progetto, possono essere presenti più elementi correnti.|
|Corrente `SelectionContainer`|Contiene uno o più oggetti per i quali l'Finestra Proprietà visualizzare le proprietà.|

 Inoltre, l'ambiente gestisce due elenchi globali:

- Elenco di identificatori di comandi dell'interfaccia utente attivi

- Elenco di tipi di elementi attualmente attivi.

### <a name="window-types-and-selection"></a>Tipi di finestra e selezione
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]L'IDE organizza le finestre in due tipi generali:

- Finestre di tipo gerarchia

- Finestre cornice, ad esempio finestre degli strumenti e di documenti

  L'IDE tiene traccia della valuta in modo diverso per ognuno di questi tipi di finestra.

  La finestra di tipo progetto più comune è Esplora soluzioni, che l'IDE controlla. Una finestra di tipo progetto tiene traccia della gerarchia globale e di ItemID del contesto di selezione globale e la finestra si basa sulla selezione dell'utente per determinare la gerarchia corrente. Per le finestre di tipo progetto, l'ambiente fornisce il servizio globale , tramite il quale i pacchetti VSPackage possono <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> monitorare i valori correnti per gli elementi aperti. L'esplorazione delle proprietà nell'ambiente è basata su questo servizio globale.

  Le finestre cornice, d'altra parte, usano il DocObject all'interno della finestra cornice per eseguire il push del valore SelectionContext (hierarchy/ItemID/SelectionContainer). . Le finestre cornice usano il servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> a questo scopo. Il DocObject può eseguire il push solo dei valori per il contenitore di selezione, lasciando invariati i valori locali per hierarchy e ItemID, come è tipico per i documenti figlio MDI.

### <a name="events-and-currency"></a>Eventi e valuta
 Possono verificarsi due tipi di eventi che influiscono sulla nozione di valuta dell'ambiente:

- Eventi propagati al livello globale e modificano il contesto di selezione della cornice della finestra. Esempi di questo tipo di evento includono l'apertura di una finestra figlio MDI, l'apertura di una finestra degli strumenti globale o l'apertura di una finestra degli strumenti di tipo progetto.

- Eventi che modificano gli elementi tracciati all'interno del contesto di selezione della cornice della finestra. Ad esempio, la modifica della selezione all'interno di un DocObject o la modifica della selezione in una finestra di tipo progetto.

## <a name="see-also"></a>Vedi anche
- [Oggetti del contesto di selezione](../../extensibility/internals/selection-context-objects.md)
- [Commenti e suggerimenti per l'utente](../../extensibility/internals/feedback-to-the-user.md)
