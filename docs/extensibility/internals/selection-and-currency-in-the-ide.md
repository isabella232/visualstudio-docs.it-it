---
title: Selezione e valuta nell'IDE | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- currency, Visual Studio IDE
- IDE, selection
- selection, Visual Studio IDE
- IDE, currency
ms.assetid: 2f6f18d1-acd8-454d-a856-9a4d81155052
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23ce55a85fd6f1408c623a49fc16b8766c535dfc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318707"
---
# <a name="selection-and-currency-in-the-ide"></a>Selezione e valuta nell'IDE
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) gestisce le informazioni sugli utenti oggetti attualmente selezionati tramite selezione *contesto*. Con il contesto di selezione, i pacchetti VSPackage possono essere incluse nella valuta verifica in due modi:

- Propagando le informazioni di valuta sui pacchetti VSPackage all'IDE.

- Monitorando selezioni attualmente attiva degli utenti all'interno dell'IDE.

## <a name="selection-context"></a>Contesto di selezione
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE globalmente tiene traccia della valuta IDE nel proprio oggetto di contesto di selezione globale. Nella tabella seguente mostra gli elementi che costituiscono il contesto di selezione.

|Elemento|Descrizione|
|-------------|-----------------|
|Gerarchia corrente.|In genere il progetto corrente. una gerarchia corrente di NULL indica che la soluzione nel suo complesso è corrente.|
|ID dell'elemento corrente|L'elemento selezionato all'interno della gerarchia corrente; Quando sono presenti le selezioni multiple in una finestra del progetto, possono esserci più elementi correnti.|
|Corrente `SelectionContainer`|Contiene uno o più oggetti per cui la finestra Proprietà visualizzazione delle proprietà.|

 Inoltre, l'ambiente mantiene due elenchi globali:

- Un elenco di identificatori di comando dell'interfaccia utente attivi

- Un elenco di tipi di elementi attualmente attivo.

### <a name="window-types-and-selection"></a>Selezione e tipi di finestre
 Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE windows sono organizzati in due tipi generali:

- Windows tipo di gerarchia

- Finestre cornice, ad esempio le finestre dei documenti e finestre

  L'IDE rileva valuta in modo diverso per ognuno di questi tipi di finestra.

  La finestra di tipo di progetto più comune è Esplora soluzioni, che controlla l'IDE. Tiene traccia di una finestra del tipo di progetto della gerarchia globale e l'ID dell'elemento del contesto di selezione globale e la finestra si basa sulla selezione dell'utente per determinare la gerarchia corrente. Per windows: tipo di progetto, l'ambiente fornisce il servizio globale <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection>, tramite quale VSPackage possono monitorare i valori correnti per gli elementi aperti. Proprietà nell'ambiente di esplorazione è determinata dal servizio globale.

  Finestre cornice, utilizzano d'altra parte, dell'oggetto documento all'interno della finestra cornice per inserire il valore di SelectionContext (il trio di gerarchia/ID dell'elemento/SelectionContainer). . Finestre cornice usano il servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> per questo scopo. Oggetto documento può effettuare il push solo i valori per il contenitore di selezione, lasciando i valori locali per la gerarchia e ItemID invariato, come avviene per i documenti figlio MDI.

### <a name="events-and-currency"></a>Gli eventi e valuta
 Due tipi di eventi possono verificarsi che influiscono sulla nozione dell'ambiente di valuta:

- Eventi che vengono propagati a livello globale e modificare il contesto di selezione finestra cornice. Esempi di questo tipo di evento includono una finestra figlio MDI viene aperta una finestra degli strumenti globale in corso l'apertura o una finestra degli strumenti del tipo di progetto in corso l'apertura.

- Eventi che modificano gli elementi viene tracciati nel contesto di selezione finestra cornice. Ad esempio la modifica di selezione all'interno di un DocObject o la modifica di selezione in una finestra del tipo di progetto.

## <a name="see-also"></a>Vedere anche
- [Oggetti del contesto di selezione](../../extensibility/internals/selection-context-objects.md)
- [Commenti e suggerimenti per l'utente](../../extensibility/internals/feedback-to-the-user.md)