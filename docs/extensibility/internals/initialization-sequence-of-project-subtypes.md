---
title: Sequenza di inizializzazione di sottotipi di progetto Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 05a3c312f61dd2b2c63c3f38ef8bac2203b326db
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707623"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Sequenza di inizializzazione dei sottotipi di progetto
L'ambiente costruisce un progetto chiamando l'implementazione di base della factory del progetto di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>. La costruzione di un sottotipo di progetto inizia quando l'ambiente determina che l'elenco GUID del tipo di progetto per l'estensione di un file di progetto non è vuoto. L'estensione del file di progetto e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] il GUID del progetto specificano se il progetto è un tipo o di progetto. Ad esempio, l'estensione vbproj e F184B08F-C81C-45F6-A57F-5ABD9991F28F identificano un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] progetto.

## <a name="environments-initialization-of-project-subtypes"></a>Inizializzazione dell'ambiente dei sottotipi di progetto
 Nella procedura seguente viene descritta in dettaglio la sequenza di inizializzazione per un sistema di progetto aggregato da più sottotipi di progetto.

1. L'ambiente chiama <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>il progetto di base di , e mentre il progetto analizza il file `null`di progetto rileva che l'elenco DI GUID di tipo di progetto aggregato non è . Il progetto interrompe la creazione diretta del progetto.

2. Il progetto `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> chiama il servizio per creare un sottotipo <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> di progetto utilizzando l'implementazione dell'ambiente del metodo. All'interno di questo metodo l'ambiente effettua chiamate <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> funzione ricorsive alle implementazioni di , e metodi mentre si sta scorrendo l'elenco dei GUID di tipo di progetto, a partire dal sottotipo di progetto più esterno.

     I passaggi di inizializzazione seguenti sono descritti in dettaglio.

    1. L'implementazione dell'ambiente <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> del `HrCreateInnerProj` metodo chiama il metodo con la seguente dichiarazione di funzione:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Quando questa funzione viene chiamata per la prima volta, ovvero per `pOuter` il `pOwner` sottotipo `null` di progetto più esterno, i `IUnknown` `pOuter`parametri e vengono passati come e la funzione imposta il sottotipo di progetto più esterno su .

    2. Successivamente l'ambiente chiama `HrCreateInnerProj` la funzione con il secondo tipo di progetto GUID nell'elenco. Questo GUID corrisponde al secondo sottotipo di progetto interno che consente di passare al progetto di base nella sequenza di aggregazione.

    3. Il `pOuter` punta ora al `IUnknown` sottotipo di progetto più `HrCreateInnerProj` esterno e <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> chiama l'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>seguita da una chiamata all'implementazione di . Nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> metodo si passa `IUnknown` il controllo del sottotipo di progetto più esterno, `pOuter`. Il progetto di proprietà (sottotipo di progetto interno) deve creare qui il relativo oggetto di progetto di aggregazione. Nell'implementazione del <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> metodo si `IUnknown` passa un puntatore all'oggetto del progetto interno che viene aggregato. Questi due metodi creano l'oggetto di aggregazione e le implementazioni devono seguire le regole di aggregazione COM per garantire che un sottotipo di progetto non finisca per contenere un conteggio dei riferimenti.

    4. `HrCreateInnerProj`chiama l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>. In questo metodo, il sottotipo di progetto esegue il lavoro di inizializzazione. È possibile, ad esempio, <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>registrare gli eventi della soluzione in .

    5. `HrCreateInnerProj`viene chiamato in modo ricorsivo fino a quando non viene raggiunto l'ultimo GUID (il progetto di base) nell'elenco. Per ciascuna di queste chiamate, i passaggi, da c a d, vengono ripetuti. `pOuter`punta al sottotipo `IUnknown` di progetto più esterno per ogni livello di aggregazione.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato in dettaglio <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> il processo a livello di codice in una rappresentazione approssimativa del metodo come viene implementato dall'ambiente. Il codice è solo un esempio; non è destinato a essere compilato e tutto il controllo degli errori è stato rimosso per chiarezza.

```cpp
HRESULT CreateAggregateProject
(
    LPCOLESTR lpstrGuids,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    REFIID iidProject,
    void **ppvProject)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpunkProj;
    CComPtr<IVsAggregatableProject> srpAggProject;
    CComBSTR bstrGuids = lpstrGuids;
    BOOL fCanceled = FALSE;
    *ppvProject = NULL;

    HrCreateInnerProj(
         bstrGuids, NULL, NULL, pszFilename, pszLocation,
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);
    srpunkProj->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggProject));
    srpAggProject->OnAggregationComplete();
    srpunkProj->QueryInterface(iidProject, ppvProject);
}

HRESULT HrCreateInnerProj
(
    WCHAR *pwszGuids,
    IUnknown *pOuter,
    IVsAggregatableProject *pOwner,
    LPCOLESTR pszFilename,
    LPCOLESTR pszLocation,
    LPCOLESTR pszName,
    VSCREATEPROJFLAGS grfCreateFlags,
    IUnknown **ppInner,
    BOOL *pfCanceled
)
{
    HRESULT hr = NOERROR;
    CComPtr<IUnknown> srpInner;
    CComPtr<IVsAggregatableProject> srpAggInner;
    CComPtr<IVsProjectFactory> srpProjectFactory;
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;
    GUID guid = GUID_NULL;
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');
    WCHAR wszText[_MAX_PATH+150] = L"";

    if (pwszNextGuids)
    {
        *pwszNextGuids++ = 0;
    }

    CLSIDFromString(pwszGuids, &guid);
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(
        guid, &srpProjectFactory);
    srpProjectFactory->QueryInterface(
        IID_IVsAggregatableProjectFactory,
        (void **)&srpAggPF);
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);
    srpInner->QueryInterface(
        IID_IVsAggregatableProject, (void **)&srpAggInner);

    if (pOwner)
    {
        IfFailGo(pOwner->SetInnerProject(srpInner));
    }

    if (pwszNextGuids)
    {
        CComPtr<IUnknown> srpNextInner;
        HrCreateInnerProj(
            pwszNextGuids, pOuter ? pOuter : srpInner,
            srpAggInner, pszFilename, pszLocation, pszName,
            grfCreateFlags, &srpNextInner, pfCanceled);
    }

    return srpAggInner->InitializeForOuter(
        pszFilename, pszLocation, pszName, grfCreateFlags,
        IID_IUnknown, (void **)ppInner, pfCanceled);
}
```

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)
