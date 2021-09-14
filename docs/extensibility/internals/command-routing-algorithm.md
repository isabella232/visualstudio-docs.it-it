---
title: Algoritmo di routing dei comandi | Microsoft Docs
description: Informazioni sull'ordine di risoluzione dei comandi Visual Studio comandi vengono gestiti da componenti diversi e indirizzati dal contesto più interno al contesto più esterno.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: f99b4e8a4f883d752d217bb1859822c65af07116
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711759"
---
# <a name="command-routing-algorithm"></a>Algoritmo di routing dei comandi
In Visual Studio comandi vengono gestiti da diversi componenti. I comandi vengono indirizzati dal contesto più interno, basato sulla selezione corrente, al contesto più esterno (noto anche come globale). Per altre informazioni, vedere [Disponibilità dei comandi](../../extensibility/internals/command-availability.md).

## <a name="order-of-command-resolution"></a>Ordine di risoluzione dei comandi
 I comandi vengono passati attraverso i livelli di contesto dei comandi seguenti:

1. Componenti aggiuntivi: l'ambiente offre innanzitutto il comando a tutti i componenti aggiuntivi presenti.

2. Comandi di priorità: questi comandi vengono registrati tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget> . Vengono chiamati per ogni comando in Visual Studio e vengono chiamati nell'ordine in cui sono stati registrati.

3. Comandi del menu di scelta rapida: un comando che si trova in un menu di scelta rapida viene prima offerto alla destinazione del comando fornita al menu di scelta rapida e successivamente al routing tipico.

4. Destinazioni dei comandi set della barra degli strumenti: queste destinazioni dei comandi vengono registrate quando si chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A> . Il `pCmdTarget` parametro può essere `null` . Se non è , questa destinazione del comando viene usata per aggiornare tutti i comandi che si trovano sulla `null` barra degli strumenti che si sta configurando. Se la shell configura la barra degli strumenti, passa la cornice della finestra come in modo che tutti gli aggiornamenti ai comandi della barra degli strumenti passino attraverso la cornice della finestra, anche quando non è `pCmdTarget` attiva.

5. Finestra degli strumenti: le finestre degli strumenti, che in genere implementano l'interfaccia , devono implementare anche l'interfaccia in modo che Visual Studio possa ottenere la destinazione del comando quando la finestra degli strumenti è <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> la finestra attiva. Tuttavia, se la finestra degli  strumenti con lo stato attivo è la finestra Project, il comando viene indirizzato all'interfaccia che è l'elemento padre comune <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> degli elementi selezionati. Se questa selezione si estende su più progetti, il comando viene indirizzato alla <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> gerarchia. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>L'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> contiene i metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> e analoghi ai comandi corrispondenti nell'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

6. Finestra del documento: se il comando ha il flag impostato nel file con estensione vsct, Visual Studio cerca una destinazione comando nell'oggetto visualizzazione documento, ovvero un'istanza di un'interfaccia o un'istanza di un oggetto documento (in genere un'interfaccia o `RouteToDocs`  <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> un'interfaccia). Se l'oggetto visualizzazione documento non supporta il comando , Visual Studio il comando viene instradato <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> all'interfaccia restituita. Si tratta di un'interfaccia facoltativa per gli oggetti dati del documento.

7. Gerarchia corrente: la gerarchia corrente può essere il progetto proprietario della finestra del documento attivo o della gerarchia selezionata **in** Esplora soluzioni . Visual Studio cerca <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia implementata nella gerarchia corrente o attiva. La gerarchia deve supportare comandi validi ogni volta che la gerarchia è attiva, anche se una finestra del documento di un elemento di progetto ha lo stato attivo. Tuttavia, i comandi che si applicano **solo quando Esplora soluzioni** ha lo stato attivo devono essere supportati usando l'interfaccia e i relativi metodi e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> .

     **I comandi Taglia**, **Copia** **,** **Incolla**, Elimina , **Rinomina**, **Invio** e **DoubleClick** richiedono una gestione speciale. Per informazioni su come gestire i **comandi Delete** **e Remove** nelle gerarchie, vedere l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> .

8. Globale: se un comando non è stato gestito dai contesti menzionati in precedenza, Visual Studio tenta di instradare il comando al pacchetto VSPackage proprietario di un comando che implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> l'interfaccia . Se il pacchetto VSPackage non è già stato caricato, non viene caricato quando Visual Studio chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo . Il pacchetto VSPackage viene caricato solo quando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> viene chiamato il metodo .

## <a name="see-also"></a>Vedi anche
- [Progettazione dei comandi](../../extensibility/internals/command-design.md)
