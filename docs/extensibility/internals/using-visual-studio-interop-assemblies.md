---
title: Uso Visual Studio assembly di interoperabilità | Microsoft Docs
description: Informazioni su Visual Studio assembly di interoperabilità consentono alle applicazioni gestite di accedere alle interfacce COM che forniscono Visual Studio estensibilità.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 108e2bf16cd109f954752207cb966c472241730e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034591"
---
# <a name="using-visual-studio-interop-assemblies"></a>Uso degli assembly di interoperabilità di Visual Studio
Visual Studio assembly di interoperabilità consentono alle applicazioni gestite di accedere alle interfacce COM che Visual Studio estendibilità. Esistono alcune differenze tra le interfacce COM dirette e le relative versioni di interoperabilità. Ad esempio, gli HRESULT sono in genere rappresentati come valori int e devono essere gestiti nello stesso modo delle eccezioni e i parametri (in particolare i parametri out) vengono trattati in modo diverso.

## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Gestione di valori HRESULT restituiti al codice gestito da COM
 Quando si chiama un'interfaccia COM dal codice gestito, esaminare il valore HRESULT e generare un'eccezione, se necessario. La classe <xref:Microsoft.VisualStudio.ErrorHandler> contiene il metodo <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, che genera un'eccezione COM, a seconda del valore HRESULT passato.

 Per impostazione predefinita, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> genera un'eccezione ogni volta che viene passato un valore HRESULT minore di zero. Nei casi in cui tali valori HRESULT sono valori accettabili e non deve essere generata alcuna eccezione, i valori HRESULT aggiuntivi devono essere passati a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> dopo essere stati testati. Se il valore HRESULT testato corrisponde a qualsiasi valore HRESULT passato in modo esplicito a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, non viene generata alcuna eccezione.

> [!NOTE]
> La classe contiene costanti per HRESULT comuni, ad esempio <xref:Microsoft.VisualStudio.VSConstants> <xref:Microsoft.VisualStudio.VSConstants.S_OK> e , e <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULTS, ad esempio <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> e <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> . <xref:Microsoft.VisualStudio.VSConstants> fornisce inoltre i metodi <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> e <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>, che corrispondono alle macro SUCCEEDED e FAILED in COM.

 Si consideri, ad esempio, la seguente chiamata di funzione, in cui <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> è un valore restituito accettabile, ma qualsiasi altro valore HRESULT minore di zero rappresenta un errore.

 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb" id="Snippet1":::
 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs" id="Snippet1":::

 Se ci sono più valori restituiti accettabili, è sufficiente aggiungere gli ulteriori valori HRESULT all'elenco nella chiamata a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.

 :::code language="vb" source="../../snippets/visualbasic/VS_Snippets_VSSDK/vssdkhresultinformation/vb/vssdkhresultinformationpackage.vb" id="Snippet2":::
 :::code language="csharp" source="../../snippets/csharp/VS_Snippets_VSSDK/vssdkhresultinformation/cs/vssdkhresultinformationpackage.cs" id="Snippet2":::

## <a name="returning-hresults-to-com-from-managed-code"></a>Restituzione di valori HRESULT a COM dal codice gestito
 Se non si verifica alcuna eccezione, il codice gestito restituisce <xref:Microsoft.VisualStudio.VSConstants.S_OK> alla funzione COM che lo ha chiamato. L'interoperabilità COM supporta eccezioni comuni fortemente tipizzate nel codice gestito. Ad esempio, un metodo che riceve un argomento `null` non accettabile, genera un'eccezione <xref:System.ArgumentNullException>.

 Se non si è certi di quale eccezione generare, ma si conosce il valore HRESULT che si vuole restituire a COM, è possibile usare il metodo <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> per generare un'eccezione appropriata. Ciò funziona anche con un errore non standard, ad esempio <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>. <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> prova a eseguire il mapping tra valore HRESULT passato e un'eccezione fortemente tipizzata. Se ciò non è possibile, genera un'eccezione COM generica. Il risultato finale è che il valore HRESULT passato a <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> dal codice gestito viene restituito alla funzione COM che lo ha chiamato.

> [!NOTE]
> Le eccezioni compromettono le prestazioni e servono per indicare condizioni anomale dei programmi. Le condizioni che si verificano spesso devono essere gestite inline, invece di generare un'eccezione.

## <a name="iunknown-parameters-passed-as-type-void"></a>Parametri IUnknown passati come Tipo void**
 Cercare i parametri [out] definiti come tipo nell'interfaccia COM, ma definiti come nel prototipo del metodo `void **` `[``iid_is``]` [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'assembly di interoperabilità.

 In alcuni casi, un'interfaccia COM `IUnknown` genera un oggetto e l'interfaccia COM lo passa come tipo `void **` . Queste interfacce sono particolarmente importanti perché se la variabile è definita come [out] nel file IDL, l'oggetto viene conteggiato con `IUnknown` il `AddRef` metodo . Si verifica una perdita di memoria se l'oggetto non viene gestito correttamente.

> [!NOTE]
> Un oggetto creato dall'interfaccia COM e restituito in una variabile [out] causa una perdita di memoria `IUnknown` se non viene rilasciato in modo esplicito.

 I metodi gestiti che gestiscono tali oggetti devono considerare come un puntatore a un oggetto e chiamare <xref:System.IntPtr> il metodo per ottenere `IUnknown` <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> l'oggetto. Il chiamante deve quindi eseguire il cast del valore restituito al tipo appropriato. Quando l'oggetto non è più necessario, chiamare <xref:System.Runtime.InteropServices.Marshal.Release%2A> per rilasciarlo.

 Di seguito è riportato un esempio di chiamata <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A> al metodo e di gestione corretta `IUnknown` dell'oggetto :

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
> I metodi seguenti sono noti per passare `IUnknown` puntatori a oggetti come tipo <xref:System.IntPtr> . Gestirli come descritto in questa sezione.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>

## <a name="optional-out-parameters"></a>Parametri facoltativi [out]
 Cercare i parametri definiti come tipo di dati [out] ( , e così via) nell'interfaccia COM, ma definiti come matrici dello stesso tipo di dati nel prototipo del metodo dell'assembly di `int` `object` [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interoperabilità.

 Alcune interfacce COM, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , trattano i parametri [out] come facoltativi. Se non è necessario un oggetto, queste interfacce COM restituiscono un puntatore come valore di tale parametro anziché creare `null` l'oggetto [out]. Questo si verifica per motivi strutturali. Per queste interfacce, i puntatori vengono presupposti come parte del comportamento corretto del pacchetto VSPackage e non `null` viene restituito alcun errore.

 Poiché CLR non consente che il valore di un parametro [out] sia , parte del comportamento progettato di queste interfacce non è disponibile direttamente all'interno `null` del codice gestito. I metodi dell'assembly di interoperabilità per le interfacce interessate consentono di risolvere il problema definendo i parametri pertinenti come matrici perché CLR consente il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] passaggio `null` di matrici.

 Le implementazioni gestite di questi metodi devono inserire `null` una matrice nel parametro quando non è necessario restituire alcun elemento. In caso contrario, creare una matrice con un elemento del tipo corretto e inserire il valore restituito nella matrice.

 I metodi gestiti che ricevono informazioni dalle interfacce con parametri [out] facoltativi ricevono il parametro come matrice. È sufficiente esaminare il valore del primo elemento della matrice. Se non è `null` , considerare il primo elemento come se fosse il parametro originale.

## <a name="passing-constants-in-pointer-parameters"></a>Passaggio di costanti nei parametri del puntatore
 Cercare i parametri definiti come puntatori [in] nell'interfaccia COM, ma definiti come tipo nel prototipo del metodo <xref:System.IntPtr> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'assembly di interoperabilità.

 Un problema simile si verifica quando un'interfaccia COM passa un valore speciale, ad esempio 0, -1 o -2, anziché un puntatore a oggetto. A [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] differenza di , CLR non consente il cast delle costanti come oggetti. Al contrario, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] l'assembly di interoperabilità definisce il parametro come <xref:System.IntPtr> tipo .

 Le implementazioni gestite di questi metodi devono sfruttare il fatto che la classe dispone di entrambi i costruttori e per creare un oggetto da un oggetto o da una costante <xref:System.IntPtr> `int` `void *` <xref:System.IntPtr> integer, in base alle esigenze.

 I metodi gestiti che ricevono <xref:System.IntPtr> parametri di questo tipo devono usare gli operatori di <xref:System.IntPtr> conversione dei tipi per gestire i risultati. Prima di tutto convertire <xref:System.IntPtr> in `int` e testarlo rispetto alle costanti Integer pertinenti. Se nessun valore corrisponde, convertirlo in un oggetto del tipo richiesto e continuare.

 Per esempi, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .

## <a name="ole-return-values-passed-as-out-parameters"></a>Valori restituiti OLE passati come parametri [out]
 Cercare i metodi che hanno un valore restituito nell'interfaccia COM, ma che hanno un valore restituito e un parametro di matrice [out] aggiuntivo nel prototipo del metodo `retval` `int` [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'assembly di interoperabilità. È chiaro che questi metodi richiedono una gestione speciale perché i prototipi dei metodi dell'assembly di interoperabilità hanno un parametro in più [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] rispetto ai metodi dell'interfaccia COM.

 Molte interfacce COM che si occupano dell'attività OLE inviano informazioni sullo stato OLE al programma chiamante archiviato nel `retval` valore restituito dell'interfaccia. Invece di usare un valore restituito, i metodi dell'assembly di interoperabilità corrispondenti inviano le informazioni al programma chiamante archiviato [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in un parametro di matrice [out].

 Le implementazioni gestite di questi metodi devono creare una matrice a elemento singolo dello stesso tipo del parametro [out] e inserire la matrice nel parametro . Il valore dell'elemento della matrice deve essere lo stesso dell'oggetto COM `retval` appropriato.

 I metodi gestiti che chiamano interfacce di questo tipo devono estrarre il primo elemento dalla matrice [out]. Questo elemento può essere considerato come se fosse un valore `retval` restituito dall'interfaccia COM corrispondente.

## <a name="see-also"></a>Vedi anche
- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)
