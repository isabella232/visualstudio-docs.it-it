---
title: Algoritmo di routing dei comandi Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af8d3e53e09214ce36a80ca18856085dfb2bb746
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709544"
---
# <a name="command-routing-algorithm"></a>Algoritmo di routing dei comandi
In Visual Studio i comandi vengono gestiti da diversi componenti. I comandi vengono indirizzati dal contesto più interno, basato sulla selezione corrente, al contesto più esterno (noto anche come globale). Per ulteriori informazioni, vedere [Disponibilità dei](../../extensibility/internals/command-availability.md)comandi .

## <a name="order-of-command-resolution"></a>Ordine di risoluzione dei comandi
 I comandi vengono passati attraverso i seguenti livelli di contesto del comando:

1. Componenti aggiuntivi: l'ambiente offre innanzitutto il comando a tutti i componenti aggiuntivi presenti.

2. Comandi di priorità: questi <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>comandi vengono registrati utilizzando . Vengono chiamati per ogni comando in Visual Studio e vengono chiamati nell'ordine in cui sono stati registrati.

3. Comandi del menu di scelta rapida: un comando che si trova in un menu di scelta rapida viene prima offerto alla destinazione del comando che viene fornito al menu di scelta rapida e dopo di che al routing tipico.

4. Destinazioni del comando set della barra <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>degli strumenti: queste destinazioni del comando vengono registrate quando si chiama . Il `pCmdTarget` parametro `null`può essere . In caso `null`contrario, questa destinazione del comando viene utilizzata per aggiornare tutti i comandi che si trovano sulla barra degli strumenti che si sta impostando. Se la shell sta impostando la barra degli strumenti, passa la cornice della finestra come `pCmdTarget` in modo che tutti gli aggiornamenti ai comandi della barra degli strumenti scorra attraverso la cornice della finestra, anche quando non è attiva.

5. Finestra degli strumenti: le finestre <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> degli strumenti, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> che in genere implementano l'interfaccia, devono implementare anche l'interfaccia in modo che Visual Studio possa ottenere la destinazione del comando quando la finestra degli strumenti è la finestra attiva. Tuttavia, se la finestra degli strumenti che ha lo stato <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> attivo è la finestra **progetto,** quindi il comando viene indirizzato all'interfaccia che è l'elemento padre comune degli elementi selezionati. Se questa selezione si estende su più progetti, il comando viene indirizzato alla <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> gerarchia. L'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> contiene <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> i metodi e analoghi ai <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> comandi corrispondenti sull'interfaccia.

6. Finestra del documento: se `RouteToDocs` il comando ha il flag impostato nel relativo file *vsct,* Visual Studio cerca <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> una destinazione del comando nell'oggetto visualizzazione documento, ovvero un'istanza di un'interfaccia o un'istanza di un oggetto documento (in genere un'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> o un'interfaccia). <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> Se l'oggetto visualizzazione documento non supporta il comando, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Visual Studio indirizza il comando all'interfaccia restituita. Si tratta di un'interfaccia facoltativa per gli oggetti dati del documento.

7. Gerarchia corrente: la gerarchia corrente può essere il progetto proprietario della finestra del documento attivo o la gerarchia selezionata in **Esplora soluzioni**. Visual Studio cerca <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia implementata nella gerarchia corrente o attiva. La gerarchia deve supportare i comandi validi ogni volta che la gerarchia è attiva, anche se una finestra del documento di un elemento di progetto ha lo stato attivo. Tuttavia, i comandi che si applicano solo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> quando Esplora <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> **soluzioni** ha lo stato attivo devono essere supportati tramite l'interfaccia e i relativi metodi e .

     I comandi **Taglia**, **Copia**, **Incolla**, **Elimina**, **Rinomina**, **Invio**e **DoubleClick** richiedono una gestione speciale. Per informazioni su come gestire i comandi di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> **eliminazione** e **rimozione** in gerarchie, vedere l'interfaccia.

8. Globale: se un comando non è stato gestito dai contesti menzionati in precedenza, Visual Studio <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> tenta di instradarlo al pacchetto VSPackage proprietario di un comando che implementa l'interfaccia. Se il pacchetto VSPackage non è già stato caricato, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> non viene caricato quando Visual Studio chiama il metodo. Il pacchetto VSPackage viene <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> caricato solo quando viene chiamato il metodo.

## <a name="see-also"></a>Vedere anche
- [Progettazione dei comandi](../../extensibility/internals/command-design.md)
