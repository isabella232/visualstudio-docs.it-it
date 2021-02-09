---
title: Selezione e valuta nell'IDE | Microsoft Docs
description: Informazioni su come i pacchetti VSPackage partecipano al rilevamento della valuta. L'IDE di Visual Studio mantiene le informazioni sugli oggetti attualmente selezionati usando il contesto di selezione.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0f77afea813158c787978e2ea4dbec1a55e36eca
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99890630"
---
# <a name="selection-and-currency-in-the-ide"></a>Selezione e valuta nell'IDE
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE) mantiene le informazioni sugli oggetti attualmente selezionati dagli utenti usando il *contesto* di selezione. Con il contesto di selezione, i pacchetti VSPackage possono partecipare al rilevamento della valuta in due modi:

- Grazie alla propagazione delle informazioni di valuta sui pacchetti VSPackage nell'IDE.

- Monitorando le selezioni attualmente attive degli utenti all'interno dell'IDE.

## <a name="selection-context"></a>Contesto di selezione
 L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE tiene traccia globalmente della valuta IDE in un oggetto di contesto di selezione globale. Nella tabella seguente vengono illustrati gli elementi che costituiscono il contesto di selezione.

|Elemento|Descrizione|
|-------------|-----------------|
|Gerarchia corrente|In genere il progetto corrente; una gerarchia corrente NULL indica che la soluzione nel suo complesso è corrente.|
|ItemID corrente|Elemento selezionato all'interno della gerarchia corrente. Quando sono presenti più selezioni in una finestra del progetto, possono essere presenti più elementi correnti.|
|Corrente `SelectionContainer`|Include uno o più oggetti per i quali il Finestra Proprietà deve visualizzare le proprietà.|

 Inoltre, l'ambiente gestisce due elenchi globali:

- Elenco di identificatori dei comandi dell'interfaccia utente attivi

- Elenco di tipi di elemento attualmente attivi.

### <a name="window-types-and-selection"></a>Tipi di finestra e selezione
 L' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE organizza le finestre in due tipi generali:

- Finestre di tipo gerarchia

- Finestre cornice, ad esempio finestre di documenti e strumenti

  L'IDE tiene traccia della valuta in modo diverso per ognuno di questi tipi di finestra.

  La finestra di tipo progetto più comune è Esplora soluzioni, che l'IDE controlla. Una finestra di tipo progetto tiene traccia della gerarchia globale e del ItemID del contesto di selezione globale e la finestra si basa sulla selezione dell'utente per determinare la gerarchia corrente. Per le finestre di tipo progetto, l'ambiente fornisce il servizio globale <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> , tramite il quale i pacchetti VSPackage possono monitorare i valori correnti per gli elementi aperti. L'esplorazione delle proprietà nell'ambiente è determinata da questo servizio globale.

  Le finestre cornice, d'altra parte, usano DocObject all'interno della finestra cornice per eseguire il push del valore SelectionContext (Hierarchy/ItemID/SelectionContainer Trio). . Le finestre cornice usano il servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> a questo scopo. DocObject è in grado di eseguire il push solo dei valori per il contenitore di selezione, lasciando invariati i valori locali per la gerarchia e ItemID, come avviene per i documenti figlio MDI.

### <a name="events-and-currency"></a>Eventi e valuta
 Potrebbero verificarsi due tipi di eventi che influiscono sulla nozione di valuta dell'ambiente:

- Eventi che vengono propagati al livello globale e cambiano il contesto della selezione della cornice della finestra. Esempi di questo tipo di evento includono una finestra figlio MDI aperta, una finestra degli strumenti globale da aprire o una finestra degli strumenti di tipo progetto da aprire.

- Eventi che modificano gli elementi tracciati nel contesto della selezione della cornice della finestra. Gli esempi includono la modifica della selezione all'interno di un DocObject o la modifica della selezione in una finestra del tipo di progetto.

## <a name="see-also"></a>Vedi anche
- [Oggetti del contesto di selezione](../../extensibility/internals/selection-context-objects.md)
- [Commenti e suggerimenti per l'utente](../../extensibility/internals/feedback-to-the-user.md)
