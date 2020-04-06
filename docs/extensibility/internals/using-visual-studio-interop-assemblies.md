---
title: Utilizzo degli assembly di interoperabilità di Visual Studio . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704127"
---
# <a name="using-visual-studio-interop-assemblies"></a>Uso degli assembly di interoperabilità di Visual Studio
Gli assembly di interoperabilità di Visual Studio consentono alle applicazioni gestite di accedere alle interfacce COM che forniscono l'estensibilità di Visual Studio.Visual Studio interop assemblies allow managed applications to access the COM interfaces that provide Visual Studio extensibility. Esistono alcune differenze tra le interfacce COM dirette e le relative versioni di interoperabilità. Ad esempio, gli HRESULT sono generalmente rappresentati come valori int e devono essere gestiti nello stesso modo delle eccezioni e i parametri (in particolare i parametri out) vengono trattati in modo diverso.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Gestione di valori HRESULT restituiti al codice gestito da COM
 Quando si chiama un'interfaccia COM dal codice gestito, esaminare il valore HRESULT e generare un'eccezione, se necessario. La classe <xref:Microsoft.VisualStudio.ErrorHandler> contiene il metodo <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, che genera un'eccezione COM, a seconda del valore HRESULT passato.

 Per impostazione predefinita, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> genera un'eccezione ogni volta che viene passato un valore HRESULT minore di zero. Nei casi in cui tali valori HRESULT sono valori accettabili e non deve essere generata alcuna eccezione, i valori HRESULT aggiuntivi devono essere passati a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> dopo essere stati testati. Se il valore HRESULT testato corrisponde a qualsiasi valore HRESULT passato in modo esplicito a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, non viene generata alcuna eccezione.

> [!NOTE]
> La <xref:Microsoft.VisualStudio.VSConstants> classe contiene costanti per HRESULTS <xref:Microsoft.VisualStudio.VSConstants.S_OK> comuni, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ad esempio , <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> e <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, e HRESULTS, ad esempio, e . <xref:Microsoft.VisualStudio.VSConstants> fornisce inoltre i metodi <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> e <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, che corrispondono alle macro SUCCEEDED e FAILED in COM.

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

## <a name="iunknown-parameters-passed-as-type-void"></a>Parametri IUnknown passati come Tipo void
 Cercare i parametri [out] definiti `void **` come tipo nell'interfaccia COM, ma definiti come `[``iid_is``]` nel prototipo del metodo dell'assembly [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di interoperabilità.

 In alcuni stati, `IUnknown` un'interfaccia COM genera un oggetto `void **`e l'interfaccia COM lo passa quindi come tipo . Queste interfacce sono particolarmente importanti perché se la variabile è definita `IUnknown` come [out] nel `AddRef` file IDL, l'oggetto viene conteggiato con il metodo. Se l'oggetto non viene gestito correttamente, si verifica una perdita di memoria.

> [!NOTE]
> Un `IUnknown` oggetto creato dall'interfaccia COM e restituito in una variabile [out] causa una perdita di memoria se non viene rilasciato in modo esplicito.

 I metodi gestiti che <xref:System.IntPtr> gestiscono tali `IUnknown` oggetti devono essere <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> considerati come puntatore a un oggetto e chiamare il metodo per ottenere l'oggetto. Il chiamante deve quindi eseguire il cast del valore restituito al tipo appropriato. Quando l'oggetto non è <xref:System.Runtime.InteropServices.Marshal.Release%2A> più necessario, chiamare per rilasciarlo.

 Di seguito è riportato un esempio di chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> metodo e gestione corretta dell'oggetto: `IUnknown`

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
> I metodi riportati `IUnknown` di seguito sono <xref:System.IntPtr>noti per passare puntatori a oggetti come tipo . Maneggiarli come descritto in questa sezione.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Parametri [out] facoltativi
 Cercare i parametri definiti come tipo di`int`dati `object`[out] ( , , e così via) nell'interfaccia COM, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ma definiti come matrici dello stesso tipo di dati nel prototipo del metodo dell'assembly di interoperabilità.

 Alcune interfacce COM, <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>ad esempio , considerano i parametri [out] come facoltativi. Se un oggetto non è necessario, `null` queste interfacce COM restituiscono un puntatore come valore di tale parametro anziché creare l'oggetto [out]. Questo si verifica per motivi strutturali. Per queste interfacce, `null` i puntatori vengono considerati come parte del comportamento corretto del pacchetto VSPackage e non viene restituito alcun errore.

 Poiché CLR non consente che il valore di `null`un parametro [out] sia , parte del comportamento progettato di queste interfacce non è direttamente disponibile all'interno del codice gestito. I [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metodi dell'assembly di interoperabilità per le interfacce interessate risolvere il `null` problema definendo i parametri rilevanti come matrici perché CLR consente il passaggio di matrici.

 Le implementazioni gestite di `null` questi metodi devono inserire una matrice nel parametro quando non vi è nulla da restituire. In caso contrario, creare una matrice a un elemento del tipo corretto e inserire il valore restituito nella matrice.

 I metodi gestiti che ricevono informazioni dalle interfacce con parametri [out] facoltativi ricevono il parametro come matrice. Basta esaminare il valore del primo elemento della matrice. In caso `null`contrario, considerare il primo elemento come se fosse il parametro originale.

## <a name="passing-constants-in-pointer-parameters"></a>Passaggio di costanti nei parametri del puntatorePassing Constants in Pointer Parameters
 Cercare i parametri definiti come puntatori [in] nell'interfaccia COM, <xref:System.IntPtr> ma [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che sono definiti come tipo nel prototipo del metodo dell'assembly di interoperabilità.

 Un problema simile si verifica quando un'interfaccia COM passa un valore speciale, ad esempio 0, -1 o -2, anziché un puntatore a oggetto. A [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]differenza di , CLR non consente il cast delle costanti come oggetti. Al contrario, l'assembly [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di <xref:System.IntPtr> interoperabilità definisce il parametro come tipo.

 Le implementazioni gestite di questi metodi <xref:System.IntPtr> devono sfruttare il fatto che la classe dispone di entrambi `int` e `void *` costruttori per creare un <xref:System.IntPtr> da un oggetto o una costante integer, a seconda dei casi.

 I metodi <xref:System.IntPtr> gestiti che ricevono <xref:System.IntPtr> parametri di questo tipo devono utilizzare gli operatori di conversione dei tipi per gestire i risultati. Convertire innanzitutto il <xref:System.IntPtr> in `int` e testarlo rispetto alle costanti integer rilevanti. Se nessun valore corrisponde, convertirlo in un oggetto del tipo richiesto e continuare.

 Per esempi, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>e .

## <a name="ole-return-values-passed-as-out-parameters"></a>Valori restituiti OLE passati come parametri [out]
 Cercare i metodi `retval` che hanno un valore restituito nell'interfaccia COM, ma che hanno `int` [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] un valore restituito e un parametro di matrice [out] aggiuntivo nel prototipo del metodo dell'assembly di interoperabilità. Deve essere chiaro che questi metodi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] richiedono una gestione speciale perché i prototipi di metodo dell'assembly di interoperabilità hanno un parametro in più rispetto ai metodi dell'interfaccia COM.

 Molte interfacce COM che gestiscono l'attività OLE inviano informazioni sullo `retval` stato OLE al programma chiamante archiviato nel valore restituito dell'interfaccia. Anziché utilizzare un valore [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] restituito, i metodi dell'assembly di interoperabilità corrispondente inviano le informazioni al programma chiamante archiviato in un parametro di matrice [out].

 Le implementazioni gestite di questi metodi devono creare una matrice a elemento singolo dello stesso tipo del parametro [out] e inserirla nel parametro. Il valore dell'elemento della matrice deve `retval`essere lo stesso del COM appropriato.

 I metodi gestiti che chiamano interfacce di questo tipo devono estrarre il primo elemento dalla matrice [out]. Questo elemento può essere considerato `retval` come se fosse un valore restituito dall'interfaccia COM corrispondente.

## <a name="see-also"></a>Vedere anche
- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)
