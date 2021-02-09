---
title: Algoritmo di routing del comando | Microsoft Docs
description: Informazioni sull'ordine di risoluzione del comando in Visual Studio poiché i comandi vengono gestiti da componenti diversi e indirizzati dal più interno al contesto più esterno.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 47991a3d1140893c4695e4edb7b76b808ab2917a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907727"
---
# <a name="command-routing-algorithm"></a>Algoritmo di routing del comando
I comandi di Visual Studio sono gestiti da numerosi componenti diversi. I comandi vengono instradati dal contesto più interno, che è basato sulla selezione corrente, al contesto più esterno (noto anche come globale). Per ulteriori informazioni, vedere la pagina relativa alla [disponibilità dei comandi](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Ordine di risoluzione del comando
 I comandi vengono passati attraverso i livelli di contesto del comando seguenti:

1. Componenti aggiuntivi: l'ambiente offre prima di tutto il comando per tutti i componenti aggiuntivi presenti.

2. Comandi di priorità: questi comandi vengono registrati tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> . Vengono chiamati per ogni comando in Visual Studio e vengono chiamati nell'ordine in cui sono stati registrati.

3. Comandi del menu di scelta rapida: un comando che si trova in un menu di scelta rapida viene innanzitutto offerto alla destinazione del comando fornito al menu di scelta rapida e successivamente al routing tipico.

4. Destinazioni del comando set della barra degli strumenti: queste destinazioni dei comandi vengono registrate quando si chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A> . Il `pCmdTarget` parametro può essere `null` . In caso contrario `null` , la destinazione del comando viene utilizzata per aggiornare tutti i comandi presenti sulla barra degli strumenti che si sta configurando. Se la Shell sta impostando la barra degli strumenti, passa la cornice della finestra come in `pCmdTarget` modo che tutti gli aggiornamenti ai comandi sulla barra degli strumenti scorrano attraverso la cornice della finestra, anche quando non è attiva.

5. Finestra degli strumenti: le finestre degli strumenti, che in genere implementano l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia, devono implementare anche l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia in modo che Visual Studio possa ottenere la destinazione del comando quando la finestra degli strumenti è la finestra attiva. Tuttavia, se la finestra degli strumenti con stato attivo è la finestra del **progetto** , il comando viene indirizzato all' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia che rappresenta l'elemento padre comune degli elementi selezionati. Se questa selezione si estende su più progetti, il comando viene indirizzato alla <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> gerarchia. L' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia contiene i <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metodi e che sono analoghi ai comandi corrispondenti nell' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia.

6. Finestra del documento: se il comando include il `RouteToDocs` flag impostato nel relativo file con *estensione vsct* , Visual Studio cerca una destinazione del comando nell'oggetto visualizzazione del documento, che è un'istanza di un' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia o un'istanza di un oggetto Document (in genere un'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> o un' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interfaccia). Se l'oggetto visualizzazione del documento non supporta il comando, Visual Studio instrada il comando all' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia restituita. Si tratta di un'interfaccia facoltativa per gli oggetti dati del documento.

7. Gerarchia corrente: la gerarchia corrente può essere il progetto a cui appartiene la finestra del documento attivo o la gerarchia selezionata in **Esplora soluzioni**. Visual Studio cerca l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia implementata nella gerarchia corrente o attiva. La gerarchia deve supportare i comandi validi ogni volta che la gerarchia è attiva, anche se una finestra del documento di un elemento di progetto ha lo stato attivo. Tuttavia, i comandi che si applicano solo quando **Esplora soluzioni** dispone dello stato attivo devono essere supportati usando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia e i relativi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metodi e.

     I comandi **taglia**, **copia**, **Incolla**, **Elimina**, **Rinomina**, **invio** e **DoubleClick** richiedono una gestione speciale. Per informazioni su come gestire i comandi **Delete** e **Remove** nelle gerarchie, vedere l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interfaccia.

8. Globale: se un comando non è stato gestito dai contesti citati in precedenza, Visual Studio tenta di instradarlo al pacchetto VSPackage che possiede un comando che implementa l' <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. Se il pacchetto VSPackage non è già stato caricato, non viene caricato quando Visual Studio chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo. Il pacchetto VSPackage viene caricato solo quando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> viene chiamato il metodo.

## <a name="see-also"></a>Vedi anche
- [Progettazione comandi](../../extensibility/internals/command-design.md)
