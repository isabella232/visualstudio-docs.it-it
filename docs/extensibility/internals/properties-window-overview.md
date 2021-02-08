---
title: Cenni preliminari sulla finestra Proprietà | Microsoft Docs
description: Informazioni sulle interfacce usate per interagire con il Finestra Proprietà nell'IDE di Visual Studio in questa panoramica.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6a33d393cfd904bdae890f4ead9a4c25a6451460
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837294"
---
# <a name="properties-window-overview"></a>Panoramica della finestra Proprietà
La finestra **Proprietà** viene utilizzata per visualizzare le proprietà degli oggetti selezionati nei due tipi principali di Windows disponibili nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE). Questi due tipi di finestre sono:

- Finestre degli strumenti, ad esempio Esplora soluzioni, Visualizzazione classi e Visualizzatore oggetti

- Finestre dei documenti contenenti tali editor e finestre di progettazione come progettazione form, editor XML e editor HTML

## <a name="using-the-properties-window"></a>Uso della finestra Proprietà
 Nella finestra **Proprietà** vengono visualizzate le proprietà di uno o più elementi selezionati. Se sono selezionati più elementi, viene visualizzata l'intersezione di tutte le proprietà per tutti gli oggetti selezionati.

 Gli eventi correlati a un oggetto selezionato in una finestra di progettazione del form o in un editor HTML utilizzando i metadati COM+ vengono visualizzati nella finestra **Proprietà** . È ad esempio possibile selezionare un pulsante e visualizzare gli eventi associati, ad esempio un `OnClick` evento, che può essere collegato a tale pulsante.

 Gli eventi visualizzati nella finestra **Proprietà** vengono utilizzati principalmente con gli oggetti associati al codice. Se si sta modificando un formato di file che non ha nulla a che fare con il codice, non saranno presenti eventi. Gli eventi vengono visualizzati solo nella finestra **Proprietà** quando esiste un'associazione tra l'esecuzione del codice e alcuni eventi associati a oggetti specifici. Un esempio è costituito dal codice sottostante a un oggetto selezionato che viene eseguito quando l'oggetto viene attivato.

 Nella tabella seguente sono elencate le interfacce primarie utilizzate dalla finestra **Proprietà** .

|Interface Name (Nome interfaccia)|Descrizione|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Fornisce un elenco di categorie alla finestra **Proprietà** ed esegue il mapping di ogni proprietà a una categoria.|
|[IDispatch (interfaccia)](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Espone i metodi e le proprietà di un oggetto agli strumenti di programmazione e ad altre applicazioni che supportano l'automazione.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Fornisce pulsanti con i puntini di sospensione (...) chiamati *compilatori* che aprono finestre di dialogo modali implementate dall'oggetto stesso. Utilizzato quando un valore non è facilmente digitato dall'utente in un campo di testo. Ad esempio, può essere usato per aprire una selezione colori che determina il valore RGB.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Consente di accedere agli oggetti utilizzati per aggiornare le informazioni visualizzate nella finestra **Proprietà** . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> viene implementato da Vspackage per ogni finestra che contiene oggetti selezionabili con proprietà correlate da visualizzare.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Fornisce informazioni sul tipo di un oggetto, ad esempio i metodi di un'interfaccia e i campi di una struttura.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Consente ai VSPackage di ricevere la notifica degli eventi di selezione e di recuperare informazioni sulla gerarchia, l'elemento, il valore dell'elemento e il contesto dell'interfaccia utente di comando correnti.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Fornisce l'ambiente con accesso a più selezioni.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Utilizzato per fornire nomi localizzati in alcune proprietà visualizzate nella finestra **Proprietà** .|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifies ai pacchetti VSPackage registrati le modifiche alla selezione, al valore dell'elemento o al contesto dell'interfaccia utente comandi correnti.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Notifica all'ambiente una modifica nella selezione corrente e fornisce l'accesso alle informazioni sulla gerarchia e sugli elementi relativi alla nuova selezione.|

 Per ulteriori informazioni su `IDispatch` , vedere MSDN Library.

## <a name="see-also"></a>Vedi anche
- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
- [Campi e interfacce della finestra Proprietà](../../extensibility/internals/properties-window-fields-and-interfaces.md)
