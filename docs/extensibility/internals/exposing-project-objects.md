---
title: Esposizione di oggetti di progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 81446fa582524872b03199ae707f658776787961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708479"
---
# <a name="expose-project-objects"></a>Esporre oggetti progetto

I tipi di progetto personalizzati possono fornire oggetti di automazione per consentire l'accesso al progetto mediante interfacce di automazione. Ogni tipo di progetto dovrebbe fornire l'oggetto di <xref:EnvDTE.Project> automazione standard a cui si accede <xref:EnvDTE.Solution> , che contiene una raccolta di tutti i progetti aperti nell'IDE. Ogni elemento del progetto dovrebbe essere esposto da un <xref:EnvDTE.ProjectItem> oggetto a cui si accede con `Project.ProjectItems` . Oltre a questi oggetti di automazione standard, i progetti possono scegliere di offrire oggetti di automazione specifici del progetto.

È possibile creare oggetti di automazione personalizzati a livello di radice a cui è possibile accedere ad associazione tardiva dall'oggetto DTE radice usando `DTE.<customObjectName>` o `DTE.GetObject("<customObjectName>")` . Ad esempio, Visual C++ crea una raccolta di progetti C++ specifica del progetto denominata *vcprojects* a cui è possibile accedere tramite `DTE.VCProjects` o `DTE.GetObject("VCProjects")` . È anche possibile creare un `Project.Object` oggetto, che è univoco per il tipo di progetto,, `Project.CodeModel` su cui è possibile eseguire una query per l'oggetto più derivato e un oggetto `ProjectItem` , che espone `ProjectItem.Object` e `ProjectItem.FileCodeModel` .

Si tratta di una convenzione comune per i progetti che espongono una raccolta di progetti personalizzata, specifica del progetto. Ad esempio, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] Crea una raccolta di progetti specifica di C++ a cui è possibile accedere usando `DTE.VCProjects` o `DTE.GetObject("VCProjects")` . È anche possibile creare un `Project.Object` oggetto, univoco per il tipo di progetto, `Project.CodeModel` che può essere sottoposto a query per l'oggetto più derivato,, `ProjectItem` che espone `ProjectItem.Object` e `ProjectItem.FileCodeModel` .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Per fornire un oggetto specifico di VSPackage per un progetto

1. Aggiungere le chiavi appropriate al file *. pkgdef* del pacchetto VSPackage.

     Ad esempio, di seguito sono riportate le impostazioni *. pkgdef* per il progetto di linguaggio C++:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Implementare il codice nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodo, come nell'esempio seguente.

    ```cpp
    STDMETHODIMP CVsPackage::GetAutomationObject(
    /* [in]  */ LPCOLESTR       pszPropName,
    /* [out] */ IDispatch **    ppIDispatch)
    {
    ExpectedPtrRet(pszPropName);
    ExpectedPtrRet(ppIDispatch);
    *ppIDispatch = NULL;

        if (m_fZombie)
            return E_UNEXPECTED;

        if (_wcsicmp(pszPropName, g_wszAutomationProjects) == 0)
        {
            return GetAutomationProjects(ppIDispatch);
        }
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectsEvents) == 0)
        {
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);
        }
        else if (_wcsicmp(pszPropName, g_wszAutomationProjectItemsEvents) == 0)
        {
            return CAutomationEvents::GetAutomationEvents(ppIDispatch);
        }
        return E_INVALIDARG;
    }
    ```

     Nel codice `g_wszAutomationProjects` è il nome della raccolta di progetti. Il `GetAutomationProjects` metodo crea un oggetto che implementa l' `Projects` interfaccia e restituisce un `IDispatch` puntatore all'oggetto chiamante, come illustrato nell'esempio di codice seguente.

    ```cpp
    HRESULT CVsPackage::GetAutomationProjects(/* [out] */ IDispatch ** ppIDispatch)
    {
        ExpectedPtrRet(ppIDispatch);
        *ppIDispatch = NULL;

        if (!m_srpAutomationProjects)
        {
            HRESULT hr = CACProjects::CreateInstance(&m_srpAutomationProjects);
            IfFailRet(hr);
            ExpectedExprRet(m_srpAutomationProjects != NULL);
        }
        return m_srpAutomationProjects.CopyTo(ppIDispatch);
    }
    ```

     Scegliere un nome univoco per l'oggetto di automazione. I conflitti di nomi sono imprevedibili e i conflitti provocano arbitrariamente il nome di un oggetto in conflitto se più tipi di progetto utilizzano lo stesso nome. Nel nome dell'oggetto di automazione è necessario includere il nome aziendale o un aspetto univoco del nome del prodotto.

     L' `Projects` oggetto raccolta personalizzata è un punto di ingresso pratico per la parte rimanente del modello di automazione del progetto. È anche possibile accedere all'oggetto progetto dalla <xref:EnvDTE.Solution> raccolta di progetti. Dopo aver creato il codice e le voci del registro di sistema appropriati che forniscono `Projects` agli utenti gli oggetti raccolta, l'implementazione deve fornire oggetti standard rimanenti per il modello di progetto. Per ulteriori informazioni, vedere Creazione di [modelli di progetto](../../extensibility/internals/project-modeling.md).

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
