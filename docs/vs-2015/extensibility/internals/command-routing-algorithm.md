---
title: Algoritmo di Routing di comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands, routing
- command routing
ms.assetid: 998b616b-bd08-45cb-845f-808efb8c33bc
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3cfd90bf3cefd941c28e20eccdafb44d4a4d1b36
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965363"
---
# <a name="command-routing-algorithm"></a>Algoritmo di routing dei comandi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In Visual Studio i comandi vengono gestiti da un numero di componenti diversi. I comandi sono indirizzati da un contesto più interno, basata sulla selezione corrente, nel contesto più esterno (noto anche come globale). Per altre informazioni, vedere [disponibilità](../../extensibility/internals/command-availability.md).  
  
## <a name="order-of-command-resolution"></a>Ordine di risoluzione di comando  
 I comandi vengono passati attraverso i livelli di contesto del comando seguenti:  
  
1.  Componenti aggiuntivi: In primo luogo, l'ambiente offre il comando per i componenti aggiuntivi che sono presenti.  
  
2.  Comandi di priorità: Questi comandi vengono registrati tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterPriorityCommandTarget>. Quando vengono chiamate per ogni comando in Visual Studio e vengono chiamati nell'ordine in cui sono stati registrati.  
  
3.  Comandi di menu di scelta rapida: Un comando che si trova in un menu di scelta rapida prima di tutto viene offerto alla destinazione del comando che viene fornita per il menu di scelta rapida e in seguito al routing tipico.  
  
4.  Sulla barra degli strumenti imposta destinazioni dei comandi: Queste destinazioni di comando vengono registrate quando si chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell4.SetupToolbar2%2A>. Il `pCmdTarget` parametro può essere `null`. Se non è `null`, questa destinazione del comando viene usato per aggiornare tutti i comandi che si trova sulla barra degli strumenti che si sta impostando. Se la shell sta configurando la barra degli strumenti, quindi passa la cornice della finestra di `pCmdTarget` in modo che tutti gli aggiornamenti per i comandi al flusso della barra degli strumenti tramite cornice della finestra, anche quando non è in stato attivo.  
  
5.  Finestra degli strumenti: Strumento windows, che in genere implementano la <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> l'interfaccia, deve implementare anche il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia in modo che Visual Studio è possibile ottenere la destinazione del comando quando la finestra degli strumenti è la finestra attiva. Tuttavia, se la finestra degli strumenti con stato attivo si trova il **progetto** finestra, quindi il comando viene instradato al <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia padre comune degli elementi selezionati. Se questa selezione si estende su più progetti, il comando viene indirizzato il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution> gerarchia. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia contiene il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A> metodi che sono analoghi per i corrispondenti comandi il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia.  
  
6.  Finestra del documento: Se il comando ha impostato il flag RouteToDocs nel relativo file con estensione vsct, Visual Studio cerca una destinazione del comando nell'oggetto visualizzazione del documento, vale a dire un'istanza di un <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane> interfaccia o un'istanza di un oggetto documento (in genere un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines> interfaccia o un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextBuffer> interface). Se l'oggetto visualizzazione del documento non supporta il comando, Visual Studio consente di indirizzare il comando per il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia restituita. (Questa è un'interfaccia facoltativa per oggetti dati documenti).  
  
7.  Gerarchia corrente: La gerarchia corrente può essere il progetto a cui appartiene la finestra del documento attivo o la gerarchia selezionata nel **Esplora soluzioni**. Visual Studio cerca il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia implementata sulla gerarchia attiva o corrente. La gerarchia deve supportare i comandi che sono validi, ogni volta che la gerarchia è attiva, anche se una finestra del documento di un elemento del progetto ha lo stato attivo. Tuttavia, i comandi che si applicano solo quando **Esplora soluzioni** ha lo stato attivo deve essere supportato usando la <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia e la relativa <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>metodi.  
  
     **Tagliare**, **copia**, **Incolla**, **eliminare**, **rinominare**, **immettere**e **DoubleClick** comandi richiedono una gestione speciale. Per informazioni su come gestire **eliminare** e **rimuovere** comandi nelle gerarchie, vedere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchyDeleteHandler> interfaccia.  
  
8.  Globale: Se un comando non è stato gestito da contesti indicati in precedenza, Visual Studio prova a indirizzarlo al pacchetto VSPackage che possiede un comando che implementa il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. Se il pacchetto VSPackage non è già stato caricato, non viene caricato quando Visual Studio chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> (metodo). Il VSPackage viene caricato solo quando il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> viene chiamato il metodo.  
  
## <a name="see-also"></a>Vedere anche  
 [Progettazione dei comandi](../../extensibility/internals/command-design.md)
