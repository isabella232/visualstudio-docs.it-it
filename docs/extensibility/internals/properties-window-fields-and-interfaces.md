---
title: Campi e interfacce della finestra Proprietà | Microsoft Docs
description: Informazioni sulla selezione che determina quali informazioni vengono visualizzate nel Finestra Proprietà in base alla finestra che ha lo stato attivo nell'IDE Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 99185ac6fe9d54a21e22fd2ea291089315ed0946
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094555"
---
# <a name="properties-window-fields-and-interfaces"></a>Campi e interfacce della finestra Proprietà
Il modello per la selezione per determinare le informazioni visualizzate nella finestra Proprietà è basato sulla finestra con lo stato attivo nell'IDE.  Per ogni finestra e per ogni oggetto all'interno della finestra selezionata è possibile eseguire il push dell'oggetto del contesto di selezione nel contesto di selezione globale. L'ambiente aggiorna il contesto di selezione globale con i valori di una cornice di finestra quando tale finestra ha lo stato attivo. Quando lo stato attivo cambia, anche il contesto di selezione viene modificato.

## <a name="tracking-selection-in-the-ide"></a>Rilevamento della selezione nell'IDE
 La cornice della finestra o il sito, di proprietà dell'IDE, dispone di un servizio denominato <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . La procedura seguente illustra come viene implementata una modifica in una selezione, causata dalla modifica dello stato attivo in un'altra  finestra aperta o dalla selezione di un elemento di progetto diverso in **Esplora soluzioni**, per modificare il contenuto visualizzato nella finestra Proprietà.

1. L'oggetto creato dal pacchetto VSPackage presente nella finestra selezionata chiama <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> per <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> richiamare <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .

2. Il contenitore di selezione, fornito dalla finestra selezionata, crea il proprio <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> oggetto . Quando la selezione cambia, il pacchetto VSPackage chiama per notificare la modifica a tutti i <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> listener nell'ambiente, inclusa la  finestra Proprietà. Fornisce anche l'accesso alle informazioni sulla gerarchia e sull'elemento correlate alla nuova selezione.

3. La <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> chiamata e il passaggio degli elementi della gerarchia selezionati nel parametro `VSHPROPID_BrowseObject` popolano <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> l'oggetto .

4. Viene restituito un oggetto [derivato dall'interfaccia IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) [per __VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) per l'elemento richiesto e l'ambiente lo esegue il wrapping in <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> un oggetto (vedere il passaggio seguente). Se la chiamata ha esito negativo, l'ambiente esegue una seconda chiamata a , passando il contenitore `IVsHierarchy::GetProperty` di [selezione __VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) che l'elemento o gli elementi della gerarchia forniscono.

    Il progetto VSPackage non viene creato perché il pacchetto VSPackage della finestra fornito dall'ambiente che lo implementa (ad esempio, Esplora soluzioni ) costruisce per <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> suo  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> conto.

5. L'ambiente richiama i metodi di per ottenere gli oggetti in base <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> `IDispatch` all'interfaccia da compilare nella **finestra** Proprietà.

   Quando un valore nella **finestra Proprietà** viene modificato, i pacchetti VSPackage implementano e per segnalare la modifica al `IVsTrackSelectionEx::OnElementValueChangeEx` valore `IVsTrackSelectionEx::OnSelectionChangeEx` dell'elemento. L'ambiente richiama quindi o per mantenere sincronizzate le informazioni visualizzate nella finestra Proprietà <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> con i valori delle <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> proprietà.  Per altre informazioni, vedere [Aggiornamento dei valori delle proprietà nella finestra Proprietà](#updating-property-values-in-the-properties-window).

   Oltre a selezionare un elemento di progetto diverso in Esplora soluzioni per visualizzare le proprietà correlate **a** tale elemento, è anche possibile scegliere  un oggetto diverso dall'interno di una finestra del modulo o di un documento usando l'elenco a discesa disponibile nella finestra Proprietà. Per altre informazioni, vedere [Elenco oggetti della finestra Proprietà](../../extensibility/internals/properties-window-object-list.md).

   È possibile modificare la modalità di  visualizzazione delle informazioni nella griglia della finestra Proprietà da alfabetica a categorica e, se disponibile, è anche possibile aprire una pagina delle proprietà per un oggetto selezionato facendo clic sui pulsanti appropriati nella finestra **Proprietà.** Per altre informazioni, vedere [Pulsanti della finestra Proprietà](../../extensibility/internals/properties-window-buttons.md) e Pagine delle [proprietà.](../../extensibility/internals/property-pages.md)

   Infine, la parte inferiore della **finestra** Proprietà contiene anche una descrizione del campo selezionato nella **griglia della finestra** Proprietà. Per altre informazioni, vedere [Recupero di descrizioni dei campi dalla finestra Proprietà](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a> Aggiornamento dei valori delle proprietà nella finestra Proprietà
Esistono due modi per mantenere sincronizzata la finestra **Proprietà** con le modifiche dei valori della proprietà. Il primo consiste nel chiamare l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>, che fornisce l'accesso alle funzionalità di windowing di base, inclusi l'accesso e la creazione di finestre degli strumenti e dei documenti fornite dall'ambiente. I passaggi seguenti descrivono il processo di sincronizzazione.

### <a name="updating-property-values-using-ivsuishell"></a>Aggiornamento dei valori di proprietà tramite IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Per aggiornare i valori di proprietà tramite l'interfaccia IVsUIShell

1. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (tramite il servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>) ogni volta che VSPackage, progetti o editor devono creare o enumerare finestre degli strumenti o dei documenti.

2. Implementare per mantenere la finestra Proprietà sincronizzata con le modifiche delle proprietà per un progetto (o qualsiasi altro oggetto selezionato esplorato dalla finestra Proprietà) senza implementare e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> generare   <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> eventi.

3. Implementare i metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> per stabilire e disabilitare, rispettivamente, la notifica client degli eventi di gerarchia senza richiedere l'implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> nella gerarchia.

### <a name="updating-property-values-using-iconnection"></a>Aggiornamento dei valori di proprietà tramite IConnection
 Il secondo modo per mantenere sincronizzata la finestra **Proprietà** con le modifiche dei valori della proprietà consiste nell'implementare `IConnection` sull'oggetto collegabile per indicare l'esistenza delle interfacce in uscita. Se si vuole localizzare il nome della proprietà, derivare l'oggetto da <xref:System.ComponentModel.ICustomTypeDescriptor>. L'implementazione <xref:System.ComponentModel.ICustomTypeDescriptor> può modificare i descrittori di proprietà che restituisce e cambiare il nome di una proprietà. Per localizzare la descrizione, creare un attributo che deriva da <xref:System.ComponentModel.DescriptionAttribute> ed eseguire l'override della proprietà Description.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Considerazioni relative all'implementazione dell'interfaccia IConnection

1. `IConnection` fornisce l'accesso a un oggetto secondario enumeratore con l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. Fornisce inoltre l'accesso a tutti gli oggetti secondari del punto di connessione, ciascuno dei quali implementa l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>.

2. Qualsiasi oggetto è responsabile dell'implementazione di un evento <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>. Nella finestra **Proprietà** verrà indicato l'evento impostato tramite `IConnection`.

3. Un punto di connessione controlla il numero di connessioni (una o più) che consente nella propria implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Un punto di connessione che consente una sola interfaccia può restituire <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> dal metodo <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>.

4. Un client può chiamare l'interfaccia `IConnection` per ottenere l'accesso a un oggetto secondario enumeratore con l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. L'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> può quindi essere chiamata per enumerare i punti di connessione per ogni ID di interfaccia (IID) in uscita.

5. `IConnection` può anche essere chiamato per ottenere l'accesso agli oggetti secondari del punto di connessione con l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> per ogni IID in uscita. Tramite l'interfaccia , un client avvia o termina un ciclo consultivo con l'oggetto collegabile e la <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> sincronizzazione del client. Il client può anche chiamare l'interfaccia per ottenere un oggetto enumeratore con l'interfaccia per enumerare <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> le connessioni di cui è a <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> conoscenza.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a> Recupero delle descrizioni dei campi dalla finestra Proprietà
Nella parte inferiore della finestra **Proprietà** è disponibile un'area per la descrizione che visualizza informazioni relative al campo della proprietà selezionata. Questa funzionalità è attivata per impostazione predefinita. Se si vuole nascondere il campo della descrizione, fare clic con il pulsante destro del mouse nella finestra **Proprietà** e fare clic su **Descrizione**. In questo modo viene anche rimosso il segno di spunta accanto al titolo **Descrizione** nella finestra del menu. È possibile visualizzare di nuovo il campo con la stessa procedura per riattivare il campo **Descrizione** .

 Le informazioni visualizzate nel campo della descrizione derivano da <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Per ogni metodo, interfaccia, coclasse e così via può esistere un attributo `helpstring` non localizzato nella libreria dei tipi. La **finestra** Proprietà recupera la stringa da <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A> .

### <a name="to-specify-localized-help-strings"></a>Per specificare stringhe della Guida localizzate

1. Aggiungere l'attributo `helpstringdll` all'istruzione library nella libreria dei tipi (`typelib`).

   > [!NOTE]
   > Questo passaggio è facoltativo se la libreria dei tipi è inclusa in un file di libreria di oggetti (con estensione olb).

2. Specificare gli attributi `helpstringcontext` per le stringhe. È anche possibile specificare attributi `helpstring` .

    Questi attributi sono distinti dagli attributi `helpfile` e `helpcontext` , contenuti negli argomenti della Guida nei file effettivi con estensione chm.

   Per recuperare le informazioni di descrizione da visualizzare  per il nome della proprietà evidenziata, la finestra Proprietà chiama per la proprietà selezionata, specificando l'attributo desiderato per <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> la stringa di `lcid` output. Internamente, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> trova il file DLL specificato nell'attributo `helpstringdll` e chiama `DLLGetDocumentation` su tale file DLL con il contesto e l'attributo `lcid` specificati.

   La firma e l'implementazione di `DLLGetDocumentation` sono:

```cpp
STDAPI DLLGetDocumentation
(
   ITypeLib * /* ptlib */,
   ITypeInfo * /* ptinfo */,
   LCID /* lcid */,
   DWORD dwCtx,
   BSTR * pbstrHelpString
);
```

 La funzione `DLLGetDocumentation` deve essere un'esportazione definita nel file con estensione def per la DLL.

 Internamente, viene creato un file con estensione olb che è in effetti una DLL. Questa DLL contiene una sola risorsa, il file della libreria dei tipi (con estensione tlb) e una funzione esportata, `DLLGetDocumentation`.

 Nel caso dei file con estensione olb, l'attributo `helpstringdll` è facoltativo perché si tratta dello stesso file che contiene il file con estensione tlb.

 Per recuperare le stringhe da visualizzare nel riquadro **Descrizione** , quindi, è necessario come minimo specificare l'attributo `helpstring` nella libreria dei tipi. Se si vuole localizzare le stringhe, è necessario specificare l'attributo facoltativo `helpstringdll` e l'attributo obbligatorio `helpstringcontext` , quindi implementare `DLLGetDocumentation`.

 Non è necessario implementare altre interfacce quando si recuperano le informazioni localizzate tramite l'attributo `helpstringcontext` dell'istruzione IDL e `DLLGetDocumentation`.

 Un altro modo per ottenere il nome e la descrizione localizzati per una proprietà è implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Per altre informazioni sull'implementazione di questo metodo, vedere [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>Vedi anche

- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
