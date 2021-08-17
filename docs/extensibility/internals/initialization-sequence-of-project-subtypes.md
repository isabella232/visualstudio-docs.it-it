---
title: Sequenza di inizializzazione Project sottotipi | Microsoft Docs
description: Informazioni sulla sequenza di inizializzazione nell'ambiente Visual Studio per un sistema di progetto aggregato da più sottotipi di progetto.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project subtypes, initialization sequence
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2a7458d2529511362b832a85819d758c26dc3cdf
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122094802"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Sequenza di inizializzazione dei sottotipi di progetto
L'ambiente costruisce un progetto chiamando l'implementazione factory del progetto di base di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> . La costruzione di un sottotipo di progetto inizia quando l'ambiente determina che l'elenco GUID del tipo di progetto per l'estensione di un file di progetto non è vuoto. L'estensione del file di progetto e il GUID del progetto specificano se il progetto è di [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] tipo o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] . Ad esempio, l'estensione vbproj e {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identificano un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] progetto.

## <a name="environments-initialization-of-project-subtypes"></a>Inizializzazione dell'ambiente di Project secondari
 La procedura seguente illustra in dettaglio la sequenza di inizializzazione per un sistema di progetto aggregato da più sottotipi di progetto.

1. L'ambiente chiama il metodo del progetto di base e, mentre il progetto analizza il file di progetto, rileva che l'elenco di GUID del tipo di progetto aggregato <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> non è `null` . Il progetto interrompe la creazione diretta del progetto.

2. Il progetto chiama `QueryService` il servizio per creare un <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> sottotipo di progetto usando l'implementazione dell'ambiente del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metodo . All'interno di questo metodo l'ambiente esegue chiamate di funzione ricorsive alle implementazioni dei metodi e mentre esegue l'elenco dei GUID del tipo di progetto, a partire dal sottotipo di progetto più <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> esterno.

     Di seguito sono descritti in dettaglio i passaggi di inizializzazione.

    1. L'implementazione dell'ambiente del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metodo chiama il metodo con la dichiarazione di funzione `HrCreateInnerProj` seguente:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Quando questa funzione viene chiamata per la prima volta, per il sottotipo di progetto più esterno, i parametri e vengono passati come e la funzione imposta il sottotipo di progetto più esterno `pOuter` `pOwner` su `null` `IUnknown` `pOuter` .

    2. L'ambiente chiama quindi `HrCreateInnerProj` la funzione con il secondo GUID del tipo di progetto nell'elenco. Questo GUID corrisponde al secondo sottotipo di progetto interno che si avvicina al progetto di base nella sequenza di aggregazione.

    3. punta ora al sottotipo di progetto più esterno e chiama l'implementazione di seguita da una `pOuter` `IUnknown` chiamata `HrCreateInnerProj` <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> all'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> . Nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> metodo si passa il controllo del `IUnknown` sottotipo di progetto più esterno, `pOuter` . Il progetto di proprietà (sottotipo di progetto interno) deve creare qui il relativo oggetto di progetto aggregato. <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>Nell'implementazione del metodo si passa un puntatore `IUnknown` all'oggetto del progetto interno che viene aggregato. Questi due metodi creano l'oggetto di aggregazione e le implementazioni devono seguire le regole di aggregazione COM per assicurarsi che un sottotipo di progetto non consegua un conteggio dei riferimenti a se stesso.

    4. `HrCreateInnerProj` chiama l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> . In questo metodo, il sottotipo di progetto esegue il lavoro di inizializzazione. È possibile, ad esempio, registrare gli eventi della soluzione in <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> .

    5. `HrCreateInnerProj` viene chiamato in modo ricorsivo finché non viene raggiunto l'ultimo GUID (il progetto di base) nell'elenco. Per ognuna di queste chiamate, i passaggi da c a d vengono ripetuti. `pOuter` punta al sottotipo di progetto più esterno `IUnknown` per ogni livello di aggregazione.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato in dettaglio il processo a livello di codice in una rappresentazione approssimativa del metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> implementato dall'ambiente. Il codice è solo un esempio. non deve essere compilato e tutti i controlli degli errori sono stati rimossi per maggiore chiarezza.

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

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.Shell.Flavor>
- [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md)
