---
title: Uso di assembly di interoperabilità di Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5926b2cce217565c889c7ef2eeef877691101ed6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704127"
---
# <a name="using-visual-studio-interop-assemblies"></a>Uso degli assembly di interoperabilità di Visual Studio
Gli assembly di interoperabilità di Visual Studio consentono alle applicazioni gestite di accedere alle interfacce COM che forniscono l'estendibilità di Visual Studio. Esistono alcune differenze tra le interfacce COM diritte e le relative versioni di interoperabilità. Gli HRESULT, ad esempio, vengono in genere rappresentati come valori int e devono essere gestiti in modo analogo alle eccezioni e i parametri (in particolare i parametri out) vengono trattati in modo diverso.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Gestione di valori HRESULT restituiti al codice gestito da COM
 Quando si chiama un'interfaccia COM dal codice gestito, esaminare il valore HRESULT e generare un'eccezione, se necessario. La classe <xref:Microsoft.VisualStudio.ErrorHandler> contiene il metodo <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, che genera un'eccezione COM, a seconda del valore HRESULT passato.

 Per impostazione predefinita, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> genera un'eccezione ogni volta che viene passato un valore HRESULT minore di zero. Nei casi in cui tali valori HRESULT sono valori accettabili e non deve essere generata alcuna eccezione, i valori HRESULT aggiuntivi devono essere passati a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> dopo essere stati testati. Se il valore HRESULT testato corrisponde a qualsiasi valore HRESULT passato in modo esplicito a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, non viene generata alcuna eccezione.

> [!NOTE]
> La <xref:Microsoft.VisualStudio.VSConstants> classe contiene costanti per HRESULT comuni, ad esempio, e e <xref:Microsoft.VisualStudio.VSConstants.S_OK> <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULT, ad esempio <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> e <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> . <xref:Microsoft.VisualStudio.VSConstants> fornisce inoltre i metodi <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> e <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, che corrispondono alle macro SUCCEEDED e FAILED in COM.

 Si consideri, ad esempio, la seguente chiamata di funzione, in cui <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> è un valore restituito accettabile, ma qualsiasi altro valore HRESULT minore di zero rappresenta un errore.

 [!code-vb[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb)]
 [!code-csharp[VSSDKHRESULTInformation#1](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]

 Se ci sono più valori restituiti accettabili, è sufficiente aggiungere gli ulteriori valori HRESULT all'elenco nella chiamata a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.

 [!code-vb[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb)]
 [!code-csharp[VSSDKHRESULTInformation#2](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Restituzione di valori HRESULT a COM dal codice gestito
 Se non si verifica alcuna eccezione, il codice gestito restituisce <xref:Microsoft.VisualStudio.VSConstants.S_OK> alla funzione COM che lo ha chiamato. L'interoperabilità COM supporta eccezioni comuni fortemente tipizzate nel codice gestito. Ad esempio, un metodo che riceve un argomento `null` non accettabile, genera un'eccezione <xref:System.ArgumentNullException>.

 Se non si è certi di quale eccezione generare, ma si conosce il valore HRESULT che si vuole restituire a COM, è possibile usare il metodo <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> per generare un'eccezione appropriata. Ciò funziona anche con un errore non standard, ad esempio <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> prova a eseguire il mapping tra valore HRESULT passato e un'eccezione fortemente tipizzata. Se ciò non è possibile, genera un'eccezione COM generica. Il risultato finale è che il valore HRESULT passato a <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> dal codice gestito viene restituito alla funzione COM che lo ha chiamato.

> [!NOTE]
> Le eccezioni compromettono le prestazioni e servono per indicare condizioni anomale dei programmi. Le condizioni che si verificano spesso devono essere gestite inline, invece di generare un'eccezione.

## <a name="iunknown-parameters-passed-as-type-void"></a>Parametri IUnknown passati come tipo void * *
 Cercare i parametri [out] definiti come tipo `void **` nell'interfaccia com, ma che sono definiti come `[``iid_is``]` nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo del metodo di assembly di interoperabilità.

 In alcuni casi, un'interfaccia COM genera un `IUnknown` oggetto e l'interfaccia com la passa quindi come tipo `void **` . Queste interfacce sono particolarmente importanti perché se la variabile è definita come [out] nell'IDL, l' `IUnknown` oggetto viene conteggiato come riferimento con il `AddRef` metodo. Si verifica una perdita di memoria se l'oggetto non è gestito correttamente.

> [!NOTE]
> Un `IUnknown` oggetto creato dall'interfaccia com e restituito in una variabile [out] causa una perdita di memoria se non viene rilasciata in modo esplicito.

 I metodi gestiti che gestiscono tali oggetti devono <xref:System.IntPtr> essere trattati come un puntatore a un `IUnknown` oggetto e chiamare il <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> metodo per ottenere l'oggetto. Il chiamante deve quindi eseguire il cast del valore restituito a qualsiasi tipo appropriato. Quando l'oggetto non è più necessario, chiamare <xref:System.Runtime.InteropServices.Marshal.Release%2A> per rilasciarlo.

 Di seguito è riportato un esempio di chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> metodo e di gestione `IUnknown` corretta dell'oggetto:

```
MyClass myclass;
Object object;
IntPtr pObj;
Guid iid = Typeof(MyClass).Guid;
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);
if (NativeMethods.Succeeded(hr))
{
    try
    {
        object = Marshal.GetObjectForIUnknown(pObj);
        myclass = object;
    }
    finally
    {
        Marshal.Release(pObj);
    }
}
else
{
    // error calling QueryViewInterface
}
```

> [!NOTE]
> I metodi seguenti sono noti per passare i `IUnknown` puntatori all'oggetto come tipo <xref:System.IntPtr> . Gestirli come descritto in questa sezione.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Parametri [out] facoltativi
 Cercare i parametri definiti come tipo di dati [out] ( `int` , `object` e così via) nell'interfaccia com, ma che sono definiti come matrici con lo stesso tipo di dati nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo del metodo di assembly di interoperabilità.

 Alcune interfacce COM, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , considerano i parametri [out] come facoltativi. Se un oggetto non è necessario, queste interfacce COM restituiscono un `null` puntatore come valore di tale parametro anziché creare l'oggetto [out]. Questo si verifica per motivi strutturali. Per queste interfacce, i `null` puntatori vengono considerati come parte del comportamento corretto del pacchetto VSPackage e non viene restituito alcun errore.

 Poiché CLR non consente il valore di un parametro [out] `null` , parte del comportamento progettato di queste interfacce non è direttamente disponibile all'interno del codice gestito. I [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metodi di assembly di interoperabilità per le interfacce interessate aggirano il problema definendo i parametri pertinenti come matrici perché CLR consente il passaggio di `null` matrici.

 Le implementazioni gestite di questi metodi devono inserire una `null` matrice nel parametro quando non è presente alcun elemento da restituire. In caso contrario, creare una matrice a un elemento del tipo corretto e inserire il valore restituito nella matrice.

 I metodi gestiti che ricevono informazioni dalle interfacce con i parametri [out] facoltativi ricevono il parametro come matrice. Esaminare semplicemente il valore del primo elemento della matrice. In caso contrario `null` , considerare il primo elemento come se fosse il parametro originale.

## <a name="passing-constants-in-pointer-parameters"></a>Passaggio di costanti nei parametri del puntatore
 Cercare i parametri definiti come [in] puntatori nell'interfaccia COM, ma che sono definiti come <xref:System.IntPtr> tipo nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo del metodo di assembly di interoperabilità.

 Un problema simile si verifica quando un'interfaccia COM passa un valore speciale, ad esempio 0,-1 o-2, anziché un puntatore a un oggetto. Diversamente da [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] , CLR non consente il cast delle costanti come oggetti. Al contrario, l' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assembly di interoperabilità definisce il parametro come <xref:System.IntPtr> tipo.

 Le implementazioni gestite di questi metodi dovrebbero sfruttare il fatto che la <xref:System.IntPtr> classe dispone di entrambi `int` i `void *` costruttori e per creare un <xref:System.IntPtr> oggetto da un oggetto o da una costante Integer, a seconda dei casi.

 I metodi gestiti che ricevono <xref:System.IntPtr> parametri di questo tipo devono usare gli <xref:System.IntPtr> operatori di conversione dei tipi per gestire i risultati. Convertire innanzitutto <xref:System.IntPtr> in `int` e testarlo rispetto alle costanti Integer pertinenti. Se nessun valore corrisponde, convertirlo in un oggetto del tipo richiesto e continuare.

 Per esempi, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .

## <a name="ole-return-values-passed-as-out-parameters"></a>Valori restituiti OLE passati come parametri [out]
 Cercare i metodi che hanno un `retval` valore restituito nell'interfaccia com, ma che hanno un `int` valore restituito e un parametro di matrice [out] aggiuntivo nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo del metodo di assembly di interoperabilità. Dovrebbe essere chiaro che questi metodi richiedono una gestione speciale perché i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipi dei metodi di assembly di interoperabilità hanno un parametro maggiore rispetto ai metodi dell'interfaccia com.

 Molte interfacce COM che gestiscono l'attività OLE inviano informazioni sullo stato OLE al programma chiamante archiviato nel `retval` valore restituito dell'interfaccia. Anziché utilizzare un valore restituito, i [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metodi di assembly di interoperabilità corrispondenti inviano le informazioni al programma chiamante archiviato in un parametro di matrice [out].

 Le implementazioni gestite di questi metodi devono creare una matrice a elemento singolo dello stesso tipo del parametro [out] e inserirla nel parametro. Il valore dell'elemento di matrice deve essere uguale a quello dell'elemento COM appropriato `retval` .

 I metodi gestiti che chiamano interfacce di questo tipo devono estrarre il primo elemento dalla matrice [out]. Questo elemento può essere considerato come se fosse un `retval` valore restituito dall'interfaccia com corrispondente.

## <a name="see-also"></a>Vedere anche
- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)
