---
title: Interfacce e campi della finestra Proprietà Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9529708c781e7fdb04c3b4c5ee143b7605857e84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706155"
---
# <a name="properties-window-fields-and-interfaces"></a>Campi e interfacce della finestra Proprietà
Il modello per la selezione per determinare quali informazioni vengono visualizzate nella finestra **Proprietà** si basa sulla finestra che ha lo stato attivo nell'IDE. Ogni finestra e oggetto all'interno della finestra selezionata, possono avere il relativo oggetto di contesto di selezione inserito nel contesto di selezione globale. L'ambiente aggiorna il contesto di selezione globale con i valori di una cornice della finestra quando tale finestra ha lo stato attivo. Quando lo stato attivo cambia, cambia anche il contesto di selezione.

## <a name="tracking-selection-in-the-ide"></a>Rilevamento della selezione nell'IDETracking Selection in the IDE
 La cornice della finestra o il sito, di <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>proprietà dell'IDE, dispone di un servizio denominato . Nei passaggi seguenti viene illustrato come viene implementata una modifica in una selezione, causata dallo stato attivo da parte dell'utente che modifica lo stato attivo in un'altra finestra aperta o dalla selezione di un elemento di progetto diverso in **Esplora soluzioni**, per modificare il contenuto visualizzato nella finestra **Proprietà.**

1. L'oggetto creato dal pacchetto VSPackage che si <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> trova <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>nella finestra selezionata chiama per avere richiamare .

2. Il contenitore di selezione, fornito dalla <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> finestra selezionata, crea il proprio oggetto. Quando la selezione viene modificata, il pacchetto VSPackage chiama <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> per notificare i listener nell'ambiente, inclusa la finestra **Proprietà,** della modifica. Fornisce inoltre l'accesso alle informazioni sulla gerarchia e sugli elementi relative alla nuova selezione.

3. La <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> chiamata e il passaggio `VSHPROPID_BrowseObject` degli elementi <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> della gerarchia selezionati nel parametro popola l'oggetto.

4. Un oggetto derivato [dall'interfaccia IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) viene restituito per [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) per l'elemento richiesto e l'ambiente ne esegue il wrapping in un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (vedere il passaggio seguente). Se la chiamata ha esito negativo, l'ambiente effettua una seconda chiamata a `IVsHierarchy::GetProperty`, passandoil e __VSHPROPID il contenitore di [selezione. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) che l'articolo o gli articoli della gerarchia forniscono.

    Il progetto VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> non crea perché la finestra fornita dall'ambiente VSPackage che <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> lo implementa (ad esempio, **Esplora soluzioni**) costruisce per suo conto.

5. L'ambiente richiama i <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> metodi di per `IDispatch` ottenere gli oggetti in base all'interfaccia per compilare il **proprietà** finestra.

   Quando viene modificato un valore nella finestra `IVsTrackSelectionEx::OnElementValueChangeEx` `IVsTrackSelectionEx::OnSelectionChangeEx` **Proprietà,** VSPackage implementare e per segnalare la modifica al valore dell'elemento. L'ambiente richiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> o per mantenere le informazioni visualizzate nella finestra **Proprietà** sincronizzate con i valori delle proprietà. Per ulteriori informazioni, vedere [Aggiornamento dei valori delle proprietà nella finestra Proprietà](#updating-property-values-in-the-properties-window).

   Oltre a selezionare un elemento di progetto diverso in **Esplora soluzioni** per visualizzare le proprietà correlate a tale elemento, è anche possibile scegliere un oggetto diverso all'interno di un form o di una finestra del documento utilizzando l'elenco a discesa disponibile nella finestra **Proprietà.** Per ulteriori informazioni, vedere [Elenco oggetti della finestra Proprietà](../../extensibility/internals/properties-window-object-list.md).

   È possibile modificare la modalità di visualizzazione delle informazioni nella griglia della finestra **Proprietà** da alfabetico a categoria e, se disponibile, è anche possibile aprire una pagina delle proprietà per un oggetto selezionato facendo clic sui pulsanti appropriati nella finestra **Proprietà.** Per ulteriori informazioni, vedere [Pulsanti della finestra Proprietà](../../extensibility/internals/properties-window-buttons.md) e [Pagine delle proprietà](../../extensibility/internals/property-pages.md).

   Infine, nella parte inferiore della finestra **Proprietà** contiene anche una descrizione del campo selezionato nella griglia della finestra **Proprietà.** Per ulteriori informazioni, vedere [Recupero delle descrizioni dei campi dalla finestra Proprietà](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a>Aggiornamento dei valori delle proprietà nella finestra ProprietàUpdating Property Values in the Properties Window
Esistono due modi per mantenere sincronizzata la finestra **Proprietà** con le modifiche dei valori della proprietà. Il primo consiste nel chiamare l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>, che fornisce l'accesso alle funzionalità di windowing di base, inclusi l'accesso e la creazione di finestre degli strumenti e dei documenti fornite dall'ambiente. I passaggi seguenti descrivono il processo di sincronizzazione.

### <a name="updating-property-values-using-ivsuishell"></a>Aggiornamento dei valori di proprietà tramite IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Per aggiornare i valori di proprietà tramite l'interfaccia IVsUIShell

1. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (tramite il servizio <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>) ogni volta che VSPackage, progetti o editor devono creare o enumerare finestre degli strumenti o dei documenti.

2. Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> per mantenere la finestra **Proprietà** sincronizzata con le modifiche alle proprietà per un progetto (o qualsiasi altro oggetto selezionato visualizzato dalla finestra **Proprietà)** senza implementare <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> e generando <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> eventi.

3. Implementare i metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy><xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> per stabilire e disabilitare, rispettivamente, la notifica client degli eventi di gerarchia senza richiedere l'implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> nella gerarchia.

### <a name="updating-property-values-using-iconnection"></a>Aggiornamento dei valori di proprietà tramite IConnection
 Il secondo modo per mantenere sincronizzata la finestra **Proprietà** con le modifiche dei valori della proprietà consiste nell'implementare `IConnection` sull'oggetto collegabile per indicare l'esistenza delle interfacce in uscita. Se si vuole localizzare il nome della proprietà, derivare l'oggetto da <xref:System.ComponentModel.ICustomTypeDescriptor>. L'implementazione <xref:System.ComponentModel.ICustomTypeDescriptor> può modificare i descrittori di proprietà che restituisce e cambiare il nome di una proprietà. Per localizzare la descrizione, creare un attributo che deriva da <xref:System.ComponentModel.DescriptionAttribute> ed eseguire l'override della proprietà Description.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Considerazioni relative all'implementazione dell'interfaccia IConnection

1. `IConnection` fornisce l'accesso a un oggetto secondario enumeratore con l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. Fornisce inoltre l'accesso a tutti gli oggetti secondari del punto di connessione, ciascuno dei quali implementa l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>.

2. Qualsiasi oggetto è responsabile dell'implementazione di un evento <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>. Nella finestra **Proprietà** verrà indicato l'evento impostato tramite `IConnection`.

3. Un punto di connessione controlla il numero di connessioni (una o più) che consente nella propria implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Un punto di connessione che consente una sola interfaccia può restituire <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> dal metodo <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>.

4. Un client può chiamare l'interfaccia `IConnection` per ottenere l'accesso a un oggetto secondario enumeratore con l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>. L'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> può quindi essere chiamata per enumerare i punti di connessione per ogni ID di interfaccia (IID) in uscita.

5. `IConnection` può anche essere chiamato per ottenere l'accesso agli oggetti secondari del punto di connessione con l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> per ogni IID in uscita. Tramite <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> l'interfaccia, un client avvia o termina un ciclo consultivo con l'oggetto collegabile e la sincronizzazione del client. Il client può <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> anche chiamare l'interfaccia <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> per ottenere un oggetto enumeratore con l'interfaccia per enumerare le connessioni che conosce.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a>Recupero delle descrizioni dei campi dalla finestra Proprietà
Nella parte inferiore della finestra **Proprietà** è disponibile un'area per la descrizione che visualizza informazioni relative al campo della proprietà selezionata. Questa funzionalità è attivata per impostazione predefinita. Se si vuole nascondere il campo della descrizione, fare clic con il pulsante destro del mouse nella finestra **Proprietà** e fare clic su **Descrizione**. In questo modo viene anche rimosso il segno di spunta accanto al titolo **Descrizione** nella finestra del menu. È possibile visualizzare di nuovo il campo con la stessa procedura per riattivare il campo **Descrizione** .

 Le informazioni visualizzate nel campo della descrizione derivano da <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Per ogni metodo, interfaccia, coclasse e così via può esistere un attributo `helpstring` non localizzato nella libreria dei tipi. La finestra **Proprietà** recupera <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>la stringa da .

### <a name="to-specify-localized-help-strings"></a>Per specificare stringhe della Guida localizzate

1. Aggiungere l'attributo `helpstringdll` all'istruzione library nella libreria dei tipi (`typelib`).

   > [!NOTE]
   > Questo passaggio è facoltativo se la libreria dei tipi è inclusa in un file di libreria di oggetti (con estensione olb).

2. Specificare gli attributi `helpstringcontext` per le stringhe. È anche possibile specificare attributi `helpstring` .

    Questi attributi sono distinti dagli attributi `helpfile` e `helpcontext` , contenuti negli argomenti della Guida nei file effettivi con estensione chm.

   Per recuperare le informazioni di descrizione da visualizzare per il <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> nome della proprietà evidenziata, `lcid` la finestra **Proprietà** chiama per la proprietà selezionata, specificando l'attributo desiderato per la stringa di output. Internamente, <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> trova il file DLL specificato nell'attributo `helpstringdll` e chiama `DLLGetDocumentation` su tale file DLL con il contesto e l'attributo `lcid` specificati.

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

## <a name="see-also"></a>Vedere anche

- [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)
