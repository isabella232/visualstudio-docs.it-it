---
title: Parametro di Assembly di interoperabilità di Visual Studio marshalling | Microsoft Docs
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
ms.openlocfilehash: 209f5956d77e714f7f663693f9ac22241d428480
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105066"
---
# <a name="visual-studio-interop-assembly-parameter-marshaling"></a>Marshalling dei parametri degli assembly di interoperabilità di Visual Studio
Pacchetti VSPackage che vengono scritti in codice gestito potrebbero essere necessario chiamare o essere chiamato da codice COM non gestito. In genere, gli argomenti del metodo vengono trasformati o sottoposto a marshalling, automaticamente per il marshalling di interoperabilità. Tuttavia, talvolta argomenti non è possibile trasformare in modo semplice. In questi casi, vengono utilizzati i parametri del prototipo metodo assembly di interoperabilità corrispondente ai parametri di funzione COM fedelmente possibile. Per altre informazioni, vedere [marshalling di interoperabilità](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a).  
  
## <a name="general-suggestions"></a>Suggerimenti generali  
  
##### <a name="read-the-reference-documentation"></a>Leggere la documentazione di riferimento  
 Per rilevare i problemi di interoperabilità in modo efficace è leggere la documentazione di riferimento per ogni metodo.  
  
 La documentazione di riferimento per ogni metodo contiene tre sezioni rilevanti:  
  
- Il [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] prototipo di funzione COM.  
  
- Il prototipo di metodo di assembly di interoperabilità.  
  
- Un elenco di parametri di COM e una breve descrizione della ognuno.  
  
##### <a name="look-for-differences-between-the-two-prototypes"></a>Cercare le differenze tra i due prototipi  
 La maggior parte dei problemi di interoperabilità derivano da mancate corrispondenze tra la definizione di un determinato tipo in un'interfaccia COM e la definizione dello stesso tipo nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] gli assembly di interoperabilità. Ad esempio, si consideri la differenza tra la possibilità di passare un `null` valore nel parametro [out]. È necessario ricercare le differenze tra i due prototipi e prendere in considerazione le implicazioni per i dati passati.  
  
##### <a name="read-the-parameter-definitions"></a>Leggere le definizioni dei parametri  
 Leggere le definizioni dei parametri. COM è meno rigorosa rispetto a common language runtime (CLR) per la combinazione di diversi tipi di dati in un singolo parametro. Il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] interfacce COM sfruttano questa flessibilità. Qualsiasi parametro che può passare o richiedono un valore non standard o un tipo di dati, ad esempio un valore costante in un parametro del puntatore, deve essere descritto come tali nella documentazione.  
  
### <a name="iunknown-objects-passed-as-type-void"></a>IUnknown gli oggetti passati come tipo void * *  
 Cercare [i parametri che sono definiti come out] `void **` in COM interfaccia, ma che sono definite come `[``iid_is``]` nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo di metodo di assembly di interoperabilità.  
  
 In alcuni casi, un'interfaccia COM genera un `IUnknown` oggetto e l'interfaccia COM quindi lo passa come tipo `void **`. Queste interfacce sono particolarmente importanti perché se la variabile viene definita come [out] nel file IDL, la `IUnknown` oggetto è conteggio dei riferimenti con il `AddRef` (metodo). Se l'oggetto non viene gestita correttamente, si verifica una perdita di memoria.  
  
> [!NOTE]
>  Un `IUnknown` oggetto creato dall'interfaccia COM e restituiti in una variabile [out] causa una perdita di memoria se non viene rilasciato in modo esplicito.  
  
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
>  I metodi seguenti sono note come passare `IUnknown` puntatori dell'oggetto come tipo <xref:System.IntPtr>. È necessario gestirle come descritto in questa sezione.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
### <a name="optional-out-parameters"></a>[Out] i parametri facoltativi  
 Cercare i parametri che sono definiti come [out] tipo di dati (`int`, `object`e così via) in COM interfaccia, ma che sono definiti come matrici dello stesso tipo di dati nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo di metodo di assembly di interoperabilità.  
  
 Interfacce di alcuni COM, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, considerare [i parametri come facoltativi out]. Se non è necessario un oggetto, le interfacce COM restituiscono un `null` come il valore del parametro anziché creare l'oggetto [out] puntatore a. Si tratta di un comportamento correlato alla progettazione. Per queste interfacce, `null` i puntatori vengono considerati come parte del comportamento corretto del pacchetto VSPackage, e viene restituito alcun errore.  
  
 Poiché Common Language Runtime non supporta il valore di parametro [out] sia `null`, parte del comportamento progettato di queste interfacce non è disponibili direttamente nel codice gestito. Il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] metodi di assembly di interoperabilità per interfacce interessate risolvere il problema definendo i parametri come matrici in quanto CLR consente il passaggio di `null` matrici.  
  
 Le implementazioni gestite di questi metodi devono essere inseriti un `null` matrice nel parametro quando non c'è niente da restituire. In caso contrario, creare una matrice a un elemento del tipo corretto e inserire il valore restituito nella matrice.  
  
 Metodi che ricevono informazioni dalle interfacce con [out] facoltativo gestiti parametri ricevano il parametro sotto forma di matrice. È sufficiente esaminare il valore del primo elemento della matrice. Se non è `null`, considerare il primo elemento, come se fosse il parametro originale.  
  
### <a name="passing-constants-in-pointer-parameters"></a>Costanti passando nei parametri di puntatore  
 Cercare i parametri che vengono definite come [in] i puntatori dell'interfaccia COM, ma che sono definiti come un <xref:System.IntPtr> digitare il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo di metodo di assembly di interoperabilità.  
  
 Un problema simile si verifica quando un'interfaccia COM passa un valore speciale, ad esempio 0, -1 o -2, anziché un puntatore all'oggetto. A differenza di [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], Common Language Runtime non supporta le costanti per eseguire il cast come oggetti. Al contrario, il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] assembly di interoperabilità definisce il parametro come un <xref:System.IntPtr> tipo.  
  
 Implementazioni gestite di questi metodi devono sfruttare il fatto che il <xref:System.IntPtr> classe dispone di entrambe `int` e `void *` costruttori per creare un <xref:System.IntPtr> da un oggetto o una costante integer, come appropriato.  
  
 Gestito i metodi che ricevono <xref:System.IntPtr> devono usare parametri di questo tipo di <xref:System.IntPtr> digitare gli operatori di conversione per gestire i risultati. Convertire innanzitutto le <xref:System.IntPtr> a `int` e verificarne il funzionamento in costanti integer pertinenti. Se i valori non corrispondono, convertirlo in un oggetto del tipo richiesto e continuare.  
  
 Per esempi, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.  
  
### <a name="ole-return-values-passed-as-out-parameters"></a>OLE restituiscono i valori passati come [parametri out]  
 Cerca i metodi che hanno una `retval` valore restituito nell'interfaccia COM, ma che hanno un' `int` valore restituito e un altro [parametro di matrice in out] il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipo di metodo di assembly di interoperabilità. Dovrebbe essere chiaro che questi metodi richiedono una gestione speciale in quanto il [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] prototipi di assembly di interoperabilità (metodo) hanno un parametro di più rispetto ai metodi di interfaccia COM.  
  
 Numero di interfacce COM che trattano di attività OLE invia le informazioni sullo stato OLE al programma chiamante archiviato nel `retval` valore restituito di interfaccia. Invece di usare un valore restituito, corrispondente [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i metodi di assembly di interoperabilità restituire le informazioni al programma chiamante archiviato in un [out] parametro di matrice.  
  
 Implementazioni gestite di questi metodi devono creare una matrice a elemento singolo dello stesso tipo di parametro [out] e inserirlo nel parametro. Il valore dell'elemento della matrice deve essere lo stesso come il componente COM appropriato `retval`.  
  
 Metodi gestiti che chiamano le interfacce di questo tipo devono inserire il primo elemento all'esterno della matrice [out]. Questo elemento può essere considerato come se fosse un `retval` valore restituito dall'interfaccia COM corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
 [Marshalling di interoperabilità](http://msdn.microsoft.com/a95fdb76-7c0d-409e-a77e-0349b1ea1490)   
 [Marshalling di interoperabilità](http://msdn.microsoft.com/library/115f7a2f-d422-4605-ab36-13a8dd28142a)   
 [Risoluzione dei problemi di interoperabilità](http://msdn.microsoft.com/library/b324cc1e-b03c-4f39-aea6-6a6d5bfd0e37)   
 [VSPackage gestiti](../misc/managed-vspackages.md)