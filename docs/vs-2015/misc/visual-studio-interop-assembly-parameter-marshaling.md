---
title: Marshalling del parametro dell'assembly di interoperabilità di Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- troubleshooting Visual Studio SDK interop assemblies
- interop assemblies, parameter marshaling
- interop assemblies, troubleshooting
ms.assetid: 89123eae-0fef-46d5-bd36-3d2a166b14e3
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: ac95c40b356c542da323a3ea3744827087f2d840
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686921"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Marshalling dei parametri degli assembly di interoperabilità di Visual Studio
I pacchetti VSPackage scritti in codice gestito potrebbero dover chiamare o essere chiamati da codice COM non gestito. Gli argomenti dei metodi vengono in genere trasformati o sottoposti a marshalling automaticamente dal gestore di marshalling di interoperabilità. Tuttavia, a volte gli argomenti non possono essere trasformati in modo semplice. In questi casi, i parametri del prototipo del metodo di assembly di interoperabilità vengono utilizzati per trovare il più vicino possibile i parametri della funzione COM. Per ulteriori informazioni, vedere [marshalling di interoperabilità](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Suggerimenti generali  
  
##### <a name="read-the-reference-documentation"></a>Leggi la documentazione di riferimento  
 Un modo efficace per rilevare i problemi di interoperabilità consiste nel leggere la documentazione di riferimento per ogni metodo.  
  
 La documentazione di riferimento per ogni metodo contiene tre sezioni pertinenti:  
  
- [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]Prototipo di funzione com.  
  
- Il prototipo del metodo di assembly di interoperabilità.  
  
- Elenco dei parametri COM e una breve descrizione di ognuno.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Individuare le differenze tra i due prototipi  
 La maggior parte dei problemi di interoperabilità derivano da mancate corrispondenze tra la definizione di un particolare tipo in un'interfaccia COM e la definizione dello stesso tipo negli [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] assembly di interoperabilità. Si consideri, ad esempio, la differenza nella possibilità di passare un `null` valore in un parametro [out]. È necessario verificare le differenze tra i due prototipi e prendere in considerazione le relative ramificazioni per i dati passati.  
  
##### <a name="read-the-parameter-definitions"></a>Leggere le definizioni dei parametri  
 Leggere le definizioni dei parametri. COM è meno restrittivo del Common Language Runtime (CLR) sulla combinazione di tipi diversi di dati in un singolo parametro. Le [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfacce com sfruttano pienamente questa flessibilità. Qualsiasi parametro che può passare o richiedere un valore o un tipo di dati non standard, ad esempio un valore costante in un parametro puntatore, deve essere descritto come tale nella documentazione.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>Oggetti IUnknown passati come tipo void * *  
 Cercare i parametri [out] definiti come tipo `void **` nell'interfaccia com, ma che sono definiti come `[``iid_is``]` nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo del metodo di assembly di interoperabilità.  
  
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
  
### <a name="optional-out-parameters"></a>Parametri [out] facoltativi  
 Cercare i parametri definiti come tipo di dati [out] ( `int` , `object` e così via) nell'interfaccia com, ma che sono definiti come matrici con lo stesso tipo di dati nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo del metodo di assembly di interoperabilità.  
  
 Alcune interfacce COM, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> , considerano i parametri [out] come facoltativi. Se un oggetto non è necessario, queste interfacce COM restituiscono un `null` puntatore come valore di tale parametro anziché creare l'oggetto [out]. Questo si verifica per motivi strutturali. Per queste interfacce, i `null` puntatori vengono considerati come parte del comportamento corretto del pacchetto VSPackage e non viene restituito alcun errore.  
  
 Poiché CLR non consente il valore di un parametro [out] `null` , parte del comportamento progettato di queste interfacce non è direttamente disponibile all'interno del codice gestito. I [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] metodi di assembly di interoperabilità per le interfacce interessate aggirano il problema definendo i parametri pertinenti come matrici perché CLR consente il passaggio di `null` matrici.  
  
 Le implementazioni gestite di questi metodi devono inserire una `null` matrice nel parametro quando non è presente alcun elemento da restituire. In caso contrario, creare una matrice a un elemento del tipo corretto e inserire il valore restituito nella matrice.  
  
 I metodi gestiti che ricevono informazioni dalle interfacce con i parametri [out] facoltativi ricevono il parametro come matrice. Esaminare semplicemente il valore del primo elemento della matrice. In caso contrario `null` , considerare il primo elemento come se fosse il parametro originale.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Passaggio di costanti nei parametri del puntatore  
 Cercare i parametri definiti come [in] puntatori nell'interfaccia COM, ma che sono definiti come <xref:System.IntPtr> tipo nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo del metodo di assembly di interoperabilità.  
  
 Un problema simile si verifica quando un'interfaccia COM passa un valore speciale, ad esempio 0,-1 o-2, anziché un puntatore a un oggetto. Diversamente da [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , CLR non consente il cast delle costanti come oggetti. Al contrario, l' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] assembly di interoperabilità definisce il parametro come <xref:System.IntPtr> tipo.  
  
 Le implementazioni gestite di questi metodi dovrebbero sfruttare il fatto che la <xref:System.IntPtr> classe dispone di entrambi `int` i `void *` costruttori e per creare un <xref:System.IntPtr> oggetto da un oggetto o da una costante Integer, a seconda dei casi.  
  
 I metodi gestiti che ricevono <xref:System.IntPtr> parametri di questo tipo devono usare gli <xref:System.IntPtr> operatori di conversione dei tipi per gestire i risultati. Convertire innanzitutto <xref:System.IntPtr> in `int` e testarlo rispetto alle costanti Integer pertinenti. Se nessun valore corrisponde, convertirlo in un oggetto del tipo richiesto e continuare.  
  
 Per esempi, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> .  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>Valori restituiti OLE passati come parametri [out]  
 Cercare i metodi che hanno un `retval` valore restituito nell'interfaccia com, ma che hanno un `int` valore restituito e un parametro di matrice [out] aggiuntivo nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo del metodo di assembly di interoperabilità. Dovrebbe essere chiaro che questi metodi richiedono una gestione speciale perché i [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipi dei metodi di assembly di interoperabilità hanno un parametro maggiore rispetto ai metodi dell'interfaccia com.  
  
 Molte interfacce COM che gestiscono l'attività OLE inviano informazioni sullo stato OLE al programma chiamante archiviato nel `retval` valore restituito dell'interfaccia. Anziché utilizzare un valore restituito, i [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] metodi di assembly di interoperabilità corrispondenti inviano le informazioni al programma chiamante archiviato in un parametro di matrice [out].  
  
 Le implementazioni gestite di questi metodi devono creare una matrice a elemento singolo dello stesso tipo del parametro [out] e inserirla nel parametro. Il valore dell'elemento di matrice deve essere uguale a quello dell'elemento COM appropriato `retval` .  
  
 I metodi gestiti che chiamano interfacce di questo tipo devono estrarre il primo elemento dalla matrice [out]. Questo elemento può essere considerato come se fosse un `retval` valore restituito dall'interfaccia com corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
 [Marshalling di interoperabilità](https://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Marshalling di interoperabilità](https://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Risoluzione dei problemi di interoperabilità](https://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [VSPackage gestiti](../misc/managed-vspackages.md)