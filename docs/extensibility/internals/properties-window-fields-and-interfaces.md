---
title: Proprietà Window Fields and Interfaces | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 31ff83f412380de4ea0eda37d2be53ccb8b59d41
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512197"
---
# <a name="properties-window-fields-and-interfaces"></a>Campi e interfacce della finestra Proprietà
Il modello per la selezione determinare quali informazioni vengono visualizzate nel **proprietà** finestra è basata sulla finestra di stato attivo nell'IDE. Ogni finestra e oggetto all'interno della finestra selezionata, può avere relativo oggetto di contesto di selezione il push nel contesto di selezione globale. L'ambiente aggiorna il contesto di selezione globale con i valori di una cornice di finestra quando tale finestra ha lo stato attivo. Quando viene modificato lo stato attivo, pertanto, non il contesto di selezione.  
  
## <a name="tracking-selection-in-the-ide"></a>Traccia della selezione nell'IDE  
 Il frame della finestra o il sito, di proprietà dall'IDE, offre un servizio chiamato <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. I passaggi seguenti mostrano come una modifica in una selezione, causata dall'utente modificando lo stato attivo a un'altra finestra aperta o selezionando un elemento di progetto diverso nel **Esplora soluzioni**, viene implementata per modificare il contenuto visualizzato nella finestra di  **Proprietà** finestra.  
  
1.  L'oggetto creato dal pacchetto VSPackage che viene inserito nelle chiamate finestra selezionata <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> avere <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> richiamare <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Il contenitore di selezione, fornito per la finestra selezionata, consente di creare un proprio <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> oggetto. Quando la modifica di selezione, il pacchetto VSPackage chiama <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> per notificare a qualsiasi listener nell'ambiente, inclusi i **proprietà** finestra, della modifica. Fornisce inoltre l'accesso alle informazioni di gerarchia ed elemento correlate alla nuova selezione.  
  
3.  La chiamata <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> e passando gli elementi della gerarchia selezionata nel `VSHPROPID_BrowseObject` parametro consente di popolare il <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> oggetto.  
  
4.  Oggetto derivato dal [IDispatch Interface](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) viene restituita per <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> per l'elemento richiesto e l'ambiente esegue il wrapping in un <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (vedere il passaggio seguente). Se la chiamata non riesce, l'ambiente esegue una seconda chiamata a `IVsHierarchy::GetProperty`, passandolo al contenitore di selezioni <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> che specifichino l'elemento della gerarchia o gli elementi.  
  
     Il progetto VSPackage non viene creato <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> perché la finestra fornita dall'ambiente di VSPackage che implementa (ad esempio, **Esplora soluzioni**) costruisce <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> per suo conto.  
  
5.  L'ambiente chiama i metodi della <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> per ottenere gli oggetti in base il `IDispatch` interfaccia per riempire il **proprietà** finestra.  
  
 Quando un valore nel **delle proprietà** finestra viene modificata, i pacchetti VSPackage implementare `IVsTrackSelectionEx::OnElementValueChangeEx` e `IVsTrackSelectionEx::OnSelectionChangeEx` per segnalare la modifica per il valore dell'elemento. Richiama quindi l'ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> oppure <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> per mantenere le informazioni visualizzate nel **proprietà** finestra sincronizzati con i valori delle proprietà. Per altre informazioni, vedere [aggiornare i valori delle proprietà nella finestra proprietà](#updating-property-values-in-the-properties-window).  
  
 Oltre a selezionare un altro elemento del progetto **Esplora soluzioni** per visualizzare le proprietà correlate a tale elemento, è anche possibile scegliere un oggetto diverso all'interno di una finestra del form o un documento utilizzando l'elenco a discesa disponibile nel **Proprietà** finestra. Per altre informazioni, vedere [elenco di oggetti finestra proprietà](../../extensibility/internals/properties-window-object-list.md).  
  
 È possibile modificare il modo in cui vengono visualizzate informazioni il **proprietà** griglia della finestra dall'ordine alfabetico per categoria, e, se disponibile, è anche possibile aprire una pagina delle proprietà dell'oggetto selezionato facendo clic sui pulsanti appropriati nel  **Proprietà** finestra. Per altre informazioni, vedere [pulsanti della finestra proprietà](../../extensibility/internals/properties-window-buttons.md) e [pagine delle proprietà](../../extensibility/internals/property-pages.md).  
  
 Infine, la parte inferiore della **delle proprietà** finestra contiene inoltre una descrizione del campo selezionato nel **proprietà** griglia della finestra. Per altre informazioni, vedere [recupero delle descrizioni dei campi dalla finestra delle proprietà](#getting-field-descriptions-from-the-properties-window).  
  
## <a name="updating-property-values-in-the-properties-window"></a> Aggiornamento dei valori di proprietà nella finestra proprietà
Esistono due modi per mantenere sincronizzata la finestra **Proprietà** con le modifiche dei valori della proprietà. Il primo consiste nel chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interfaccia, che fornisce l'accesso alle funzionalità windowing di base, inclusi l'accesso e creazione di finestre dei documenti e finestre fornita dall'ambiente. I passaggi seguenti descrivono il processo di sincronizzazione.  
  
### <a name="updating-property-values-using-ivsuishell"></a>Aggiornamento dei valori di proprietà tramite IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>Per aggiornare i valori di proprietà tramite l'interfaccia IVsUIShell  
  
1.  Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (tramite <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> servizio) ogni volta che VSPackage, progetti o editor devono creare o enumerare finestre degli strumenti o documento.  
  
2.  Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> per mantenere il **delle proprietà** finestra sincronizzato con le modifiche alle proprietà per un progetto (o qualsiasi altro oggetto selezionato visualizzato tramite il **proprietà** finestra) senza implementare <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> e la generazione di <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> gli eventi.  
  
3.  Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> metodi <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> per stabilire e disabilitare, rispettivamente, la notifica client degli eventi della gerarchia senza richiedere la gerarchia per implementare <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
### <a name="updating-property-values-using-iconnection"></a>Aggiornamento dei valori di proprietà tramite IConnection  
 Il secondo modo per mantenere sincronizzata la finestra **Proprietà** con le modifiche dei valori della proprietà consiste nell'implementare `IConnection` sull'oggetto collegabile per indicare l'esistenza delle interfacce in uscita. Se si vuole localizzare il nome della proprietà, derivare l'oggetto da <xref:System.ComponentModel.ICustomTypeDescriptor>. Il <xref:System.ComponentModel.ICustomTypeDescriptor> implementazione può modificare i descrittori di proprietà restituisce e cambiare il nome di una proprietà. Per localizzare la descrizione, creare un attributo che deriva da <xref:System.ComponentModel.DescriptionAttribute> ed eseguire l'override della proprietà Description.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Considerazioni relative all'implementazione dell'interfaccia IConnection  
  
1.  `IConnection` fornisce l'accesso a un oggetto secondario enumeratore con il <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfaccia. Fornisce inoltre l'accesso a tutti di oggetti punto di connessione secondaria, ciascuno dei quali implementa il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia.  
  
2.  Qualsiasi oggetto è responsabile dell'implementazione un' <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> evento. Nella finestra **Proprietà** verrà indicato l'evento impostato tramite `IConnection`.  
  
3.  Un punto di connessione controlla il numero di connessioni (uno o più) consente nella propria implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Un punto di connessione che consente una sola interfaccia può restituire <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> dal <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> (metodo).  
  
4.  Un client può chiamare le `IConnection` interfaccia per ottenere l'accesso a un oggetto secondario enumeratore con il <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfaccia. Il <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> interfaccia è quindi possibile chiamare per enumerare i punti di connessione per ogni ID (IID) dell'interfaccia in uscita.  
  
5.  `IConnection` può anche essere chiamato per ottenere l'accesso agli oggetti secondari di punto di connessione con il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia per ogni IID in uscita. Tramite il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia, un client avvia o termina un ciclo consultivo con l'oggetto collegabile e la sincronizzazione del client. Il client può anche chiamare il <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> interfaccia per ottenere un oggetto enumeratore con il <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> interfaccia per enumerare le connessioni note.  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a> Descrizioni dei campi dalla finestra delle proprietà
Nella parte inferiore della finestra **Proprietà** è disponibile un'area per la descrizione che visualizza informazioni relative al campo della proprietà selezionata. Questa funzionalità è attivata per impostazione predefinita. Se si vuole nascondere il campo della descrizione, fare clic con il pulsante destro del mouse nella finestra **Proprietà** e fare clic su **Descrizione**. In questo modo viene anche rimosso il segno di spunta accanto al titolo **Descrizione** nella finestra del menu. È possibile visualizzare di nuovo il campo con la stessa procedura per riattivare il campo **Descrizione** .  
  
 Le informazioni nel campo della descrizione derivano da <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Per ogni metodo, interfaccia, coclasse e così via può esistere un attributo `helpstring` non localizzato nella libreria dei tipi. Il **delle proprietà** finestra Recupera la stringa da <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>Per specificare stringhe della Guida localizzate  
  
1.  Aggiungere l'attributo `helpstringdll` all'istruzione library nella libreria dei tipi (`typelib`).  
  
    > [!NOTE]
    >  Questo passaggio è facoltativo se la libreria dei tipi è inclusa in un file di libreria di oggetti (con estensione olb).  
  
2.  Specificare gli attributi `helpstringcontext` per le stringhe. È anche possibile specificare attributi `helpstring` .  
  
     Questi attributi sono distinti dagli attributi `helpfile` e `helpcontext` , contenuti negli argomenti della Guida nei file effettivi con estensione chm.  
  
 Per recuperare le informazioni di descrizione da visualizzare per il nome della proprietà evidenziata, la **delle proprietà** finestra chiamate <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> per la proprietà è selezionata, specificando il valore desiderato `lcid` attributo per il stringa di output. Internamente <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> trova il file DLL specificato nel `helpstringdll` attributo e le chiamate `DLLGetDocumentation` su tale file con estensione dll con il contesto specificato e `lcid` attributo.  
  
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
  
 Un altro modo per ottenere il nome localizzato e la descrizione di una proprietà è implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Per altre informazioni sull'implementazione di questo metodo, vedere [proprietà Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md).  

## <a name="see-also"></a>Vedere anche  
 [Estensione delle proprietà](../../extensibility/internals/extending-properties.md)