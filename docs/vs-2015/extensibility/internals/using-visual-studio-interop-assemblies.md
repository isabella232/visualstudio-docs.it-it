---
title: Tramite assembly di interoperabilità | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 34
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 60ae3ad958ca97250ba74ac2c7aada7dddcf91d8
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434792"
---
# <a name="using-visual-studio-interop-assemblies"></a>Uso degli assembly di interoperabilità di Visual Studio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Assembly di interoperabilità Visual Studio consentono alle applicazioni gestite di accesso alle interfacce COM che forniscono l'estensibilità di Visual Studio. Esistono alcune differenze tra le interfacce COM rette e le versioni di interoperabilità. Ad esempio, HRESULT sono in genere rappresentati come valori int e devono essere gestiti nello stesso modo come eccezioni e i parametri (in particolare i parametri out) vengono considerati in modo diverso.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Gestione di valori HRESULT restituiti al codice gestito da COM
 Quando si chiama un'interfaccia COM dal codice gestito, esaminare il valore HRESULT e generare un'eccezione, se necessario. La classe <xref:Microsoft.VisualStudio.ErrorHandler> contiene il metodo <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, che genera un'eccezione COM, a seconda del valore HRESULT passato.

 Per impostazione predefinita, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> genera un'eccezione ogni volta che viene passato un valore HRESULT minore di zero. Nei casi in cui tali valori HRESULT sono valori accettabili e non deve essere generata alcuna eccezione, i valori HRESULT aggiuntivi devono essere passati a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> dopo essere stati testati. Se il valore HRESULT testato corrisponde a qualsiasi valore HRESULT passato in modo esplicito a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, non viene generata alcuna eccezione.

> [!NOTE]
> Il <xref:Microsoft.VisualStudio.VSConstants> classe contiene costanti per valori HRESULT comuni, ad esempio, <xref:Microsoft.VisualStudio.VSConstants.S_OK> e <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, e [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] HRESULT, ad esempio <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> e <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>. <xref:Microsoft.VisualStudio.VSConstants> fornisce inoltre i metodi <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> e <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, che corrispondono alle macro SUCCEEDED e FAILED in COM.

 Si consideri, ad esempio, la seguente chiamata di funzione, in cui <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> è un valore restituito accettabile, ma qualsiasi altro valore HRESULT minore di zero rappresenta un errore.

 [!code-csharp[VSSDKHRESULTInformation#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#1)]
 [!code-vb[VSSDKHRESULTInformation#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#1)]

 Se ci sono più valori restituiti accettabili, è sufficiente aggiungere gli ulteriori valori HRESULT all'elenco nella chiamata a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.

 [!code-csharp[VSSDKHRESULTInformation#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs#2)]
 [!code-vb[VSSDKHRESULTInformation#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb#2)]

## <a name="returning-hresults-to-com-from-managed-code"></a>Restituzione di valori HRESULT a COM dal codice gestito
 Se non si verifica alcuna eccezione, il codice gestito restituisce <xref:Microsoft.VisualStudio.VSConstants.S_OK> alla funzione COM che lo ha chiamato. L'interoperabilità COM supporta eccezioni comuni fortemente tipizzate nel codice gestito. Ad esempio, un metodo che riceve un argomento `null` non accettabile, genera un'eccezione <xref:System.ArgumentNullException>.

 Se non si è certi di quale eccezione generare, ma si conosce il valore HRESULT che si vuole restituire a COM, è possibile usare il metodo <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> per generare un'eccezione appropriata. Ciò funziona anche con un errore non standard, ad esempio <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> prova a eseguire il mapping tra valore HRESULT passato e un'eccezione fortemente tipizzata. Se ciò non è possibile, genera un'eccezione COM generica. Il risultato finale è che il valore HRESULT passato a <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> dal codice gestito viene restituito alla funzione COM che lo ha chiamato.

> [!NOTE]
> Le eccezioni compromettono le prestazioni e servono per indicare condizioni anomale dei programmi. Le condizioni che si verificano spesso devono essere gestite inline, invece di generare un'eccezione.

## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown parametri passati come tipo void **
 Cercare [i parametri che sono definiti come out] `void **` in COM interfaccia, ma che sono definite come `[``iid_is``]` nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prototipo di metodo di assembly di interoperabilità.

 In alcuni casi, un'interfaccia COM genera un `IUnknown` oggetto e l'interfaccia COM quindi lo passa come tipo `void **`. Queste interfacce sono particolarmente importanti perché se la variabile viene definita come [out] nel file IDL, la `IUnknown` oggetto è conteggio dei riferimenti con il `AddRef` (metodo). Se l'oggetto non viene gestita correttamente, si verifica una perdita di memoria.

> [!NOTE]
> Un `IUnknown` oggetto creato dall'interfaccia COM e restituiti in una variabile [out] causa una perdita di memoria se non viene rilasciato in modo esplicito.

 Metodi gestiti che gestiscono tali oggetti devono trattare <xref:System.IntPtr> come puntatore a un `IUnknown` dell'oggetto e chiamare il <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> metodo per ottenere l'oggetto. Il chiamante deve quindi eseguire il cast del valore restituito in qualsiasi tipo è appropriato. Quando l'oggetto non è più necessario, chiamare <xref:System.Runtime.InteropServices.Marshal.Release%2A> rilasciarlo.

 Seguito è riportato un esempio della chiamata al metodo il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> metodo e la gestione il `IUnknown` oggetto correttamente:

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
> I metodi seguenti sono note come passare `IUnknown` puntatori dell'oggetto come tipo <xref:System.IntPtr>. È necessario gestirle come descritto in questa sezione.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>[Out] i parametri facoltativi
 Cercare i parametri che sono definiti come [out] tipo di dati (`int`, `object`e così via) in COM interfaccia, ma che sono definiti come matrici dello stesso tipo di dati nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prototipo di metodo di assembly di interoperabilità.

 Interfacce di alcuni COM, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, considerare [i parametri come facoltativi out]. Se non è necessario un oggetto, le interfacce COM restituiscono un `null` come il valore del parametro anziché creare l'oggetto [out] puntatore a. Si tratta di un comportamento correlato alla progettazione. Per queste interfacce, `null` i puntatori vengono considerati come parte del comportamento corretto del pacchetto VSPackage, e viene restituito alcun errore.

 Poiché Common Language Runtime non supporta il valore di parametro [out] sia `null`, parte del comportamento progettato di queste interfacce non è disponibili direttamente nel codice gestito. Il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] metodi di assembly di interoperabilità per interfacce interessate risolvere il problema definendo i parametri come matrici in quanto CLR consente il passaggio di `null` matrici.

 Le implementazioni gestite di questi metodi devono essere inseriti un `null` matrice nel parametro quando non c'è niente da restituire. In caso contrario, creare una matrice a un elemento del tipo corretto e inserire il valore restituito nella matrice.

 Metodi che ricevono informazioni dalle interfacce con [out] facoltativo gestiti parametri ricevano il parametro sotto forma di matrice. È sufficiente esaminare il valore del primo elemento della matrice. Se non è `null`, considerare il primo elemento, come se fosse il parametro originale.

## <a name="passing-constants-in-pointer-parameters"></a>Costanti passando nei parametri di puntatore
 Cercare i parametri che vengono definite come [in] i puntatori dell'interfaccia COM, ma che sono definiti come un <xref:System.IntPtr> digitare il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prototipo di metodo di assembly di interoperabilità.

 Un problema simile si verifica quando un'interfaccia COM passa un valore speciale, ad esempio 0, -1 o -2, anziché un puntatore all'oggetto. A differenza di [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], Common Language Runtime non supporta le costanti per eseguire il cast come oggetti. Al contrario, il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] assembly di interoperabilità definisce il parametro come un <xref:System.IntPtr> tipo.

 Implementazioni gestite di questi metodi devono sfruttare il fatto che il <xref:System.IntPtr> classe dispone di entrambe `int` e `void *` costruttori per creare un <xref:System.IntPtr> da un oggetto o una costante integer, come appropriato.

 Gestito i metodi che ricevono <xref:System.IntPtr> devono usare parametri di questo tipo di <xref:System.IntPtr> digitare gli operatori di conversione per gestire i risultati. Convertire innanzitutto le <xref:System.IntPtr> a `int` e verificarne il funzionamento in costanti integer pertinenti. Se i valori non corrispondono, convertirlo in un oggetto del tipo richiesto e continuare.

 Per esempi, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.

## <a name="ole-return-values-passed-as-out-parameters"></a>OLE restituiscono i valori passati come [parametri out]
 Cerca i metodi che hanno una `retval` valore restituito nell'interfaccia COM, ma che hanno un' `int` valore restituito e un altro [parametro di matrice in out] il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prototipo di metodo di assembly di interoperabilità. Dovrebbe essere chiaro che questi metodi richiedono una gestione speciale in quanto il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] prototipi di assembly di interoperabilità (metodo) hanno un parametro di più rispetto ai metodi di interfaccia COM.

 Numero di interfacce COM che trattano di attività OLE invia le informazioni sullo stato OLE al programma chiamante archiviato nel `retval` valore restituito di interfaccia. Invece di usare un valore restituito, corrispondente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i metodi di assembly di interoperabilità restituire le informazioni al programma chiamante archiviato in un [out] parametro di matrice.

 Implementazioni gestite di questi metodi devono creare una matrice a elemento singolo dello stesso tipo di parametro [out] e inserirlo nel parametro. Il valore dell'elemento della matrice deve essere lo stesso come il componente COM appropriato `retval`.

 Metodi gestiti che chiamano le interfacce di questo tipo devono inserire il primo elemento all'esterno della matrice [out]. Questo elemento può essere considerato come se fosse un `retval` valore restituito dall'interfaccia COM corrispondente.

## <a name="see-also"></a>Vedere anche
 [Interoperabilità con codice non gestito](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
