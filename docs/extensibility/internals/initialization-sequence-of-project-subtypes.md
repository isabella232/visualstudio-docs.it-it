---
title: Sequenza di inizializzazione di sottotipi di progetto | Microsoft Docs
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
ms.workload:
- vssdk
ms.openlocfilehash: 88a8aa39c513ed6317a6b57509810e16a58f192b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069543"
---
# <a name="initialization-sequence-of-project-subtypes"></a>Sequenza di inizializzazione dei sottotipi di progetto
L'ambiente costruisce un progetto chiamando l'implementazione della factory del progetto di base di <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> . La costruzione di un sottotipo di progetto viene avviata quando l'ambiente determina che l'elenco dei GUID del tipo di progetto per l'estensione di un file di progetto non è vuoto. L'estensione del file di progetto e il GUID del progetto specificano se il progetto è un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] tipo di progetto o. Ad esempio, l'estensione vbproj e {F184B08F-C81C-45F6-A57F-5ABD9991F28F} identificano un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] progetto.

## <a name="environments-initialization-of-project-subtypes"></a>Inizializzazione dell'ambiente dei sottotipi di progetto
 Nella procedura seguente viene illustrata la sequenza di inizializzazione per un sistema di progetto aggregato da più sottotipi di progetto.

1. L'ambiente chiama il progetto di base <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> e, mentre il progetto analizza il file di progetto, individua che l'elenco di GUID del tipo di progetto aggregato non lo è `null` . Il progetto viene interrotto direttamente creando il progetto.

2. Il progetto chiama `QueryService` il <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> servizio per creare un sottotipo di progetto usando l'implementazione dell'ambiente del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metodo. All'interno di questo metodo l'ambiente esegue chiamate di funzione ricorsive alle implementazioni <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> dei <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> metodi e mentre sta esaminando l'elenco dei GUID del tipo di progetto, a partire dal sottotipo di progetto più esterno.

     Di seguito vengono illustrati i passaggi di inizializzazione.

    1. L'implementazione dell'ambiente del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metodo chiama il `HrCreateInnerProj` metodo con la seguente dichiarazione di funzione:

         \<CodeContentPlaceHolder>0</CodeContentPlaceHolder>

         Quando questa funzione viene chiamata per la prima volta, ovvero per il sottotipo di progetto più esterno, i parametri `pOuter` e `pOwner` vengono passati come `null` e la funzione imposta il sottotipo di progetto più esterno `IUnknown` su `pOuter` .

    2. L'ambiente chiama quindi la `HrCreateInnerProj` funzione con il secondo GUID del tipo di progetto nell'elenco. Questo GUID corrisponde al secondo sottotipo di progetto interno che esegue l'istruzione verso il progetto di base nella sequenza di aggregazione.

    3. `pOuter`Punta ora all'oggetto `IUnknown` del sottotipo di progetto più esterno e chiama l' `HrCreateInnerProj` implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> seguita da una chiamata all'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> . Nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> metodo viene passato il controllo `IUnknown` del sottotipo di progetto più esterno, `pOuter` . Il progetto di proprietà (sottotipo di progetto interno) deve creare qui il relativo oggetto progetto aggregato. Nell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> implementazione del metodo passare un puntatore all'oggetto `IUnknown` del progetto interno da aggregare. Questi due metodi creano l'oggetto aggregazione e le implementazioni devono seguire le regole di aggregazione COM per garantire che un sottotipo di progetto non finisca di contenere un conteggio dei riferimenti a se stesso.

    4. `HrCreateInnerProj` chiama l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> . In questo metodo, il sottotipo di progetto esegue le operazioni di inizializzazione. È possibile, ad esempio, registrare gli eventi della soluzione in <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> .

    5. `HrCreateInnerProj` viene chiamato in modo ricorsivo fino a quando non viene raggiunto l'ultimo GUID (progetto di base) nell'elenco. Per ognuna di queste chiamate, i passaggi da c a d vengono ripetuti. `pOuter` punta al sottotipo di progetto più esterno `IUnknown` per ogni livello di aggregazione.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrata in dettaglio il processo programmatico in una rappresentazione approssimativa del <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> metodo implementato dall'ambiente. Il codice è solo un esempio. non è progettato per la compilazione e il controllo degli errori è stato rimosso per maggiore chiarezza.

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
