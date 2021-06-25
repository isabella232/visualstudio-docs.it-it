---
title: Esposizione di oggetti di progetto | Microsoft Docs
description: Informazioni su come esporre oggetti per i tipi di progetto personalizzati in Visual Studio fornendo oggetti di automazione che consentono l'accesso al progetto usando le interfacce di automazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- project objects, exposing
- extensibility, project objects
ms.assetid: 5bb24967-434a-4ef4-87a0-2f3250c9e22d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c3e89b4c80d64bedb77e68c648ba993794f8b658
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898292"
---
# <a name="expose-project-objects"></a>Esporre oggetti di progetto

I tipi di progetto personalizzati possono fornire oggetti di automazione per consentire l'accesso al progetto tramite le interfacce di automazione. Ogni tipo di progetto deve fornire l'oggetto di automazione standard a cui si accede da , che contiene una raccolta di tutti i progetti <xref:EnvDTE.Project> <xref:EnvDTE.Solution> aperti nell'IDE. Ogni elemento del progetto deve essere esposto da un oggetto a cui <xref:EnvDTE.ProjectItem> si accede con `Project.ProjectItems` . Oltre a questi oggetti di automazione standard, i progetti possono scegliere di offrire oggetti di automazione specifici del progetto.

È possibile creare oggetti di automazione a livello di radice personalizzati a cui è possibile accedere ad associazione tardiva dall'oggetto DTE radice usando `DTE.<customObjectName>` o `DTE.GetObject("<customObjectName>")` . Ad esempio, Visual C++ crea una raccolta di progetti C++ specifica del progetto denominata *VCProjects* a cui è possibile accedere usando `DTE.VCProjects` o `DTE.GetObject("VCProjects")` . È anche possibile creare un oggetto , univoco per il tipo di progetto, un oggetto , su cui è possibile eseguire query per l'oggetto derivato più di uno, e un oggetto , che espone `Project.Object` `Project.CodeModel` e `ProjectItem` `ProjectItem.Object` `ProjectItem.FileCodeModel` .

È una convenzione comune per i progetti esporre una raccolta di progetti personalizzata e specifica del progetto. Ad esempio, crea una raccolta di [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] progetti specifica C++ a cui è possibile accedere usando `DTE.VCProjects` o `DTE.GetObject("VCProjects")` . È anche possibile creare un oggetto , univoco per il tipo di progetto, un oggetto , su cui è possibile eseguire query per il relativo oggetto derivato più, un oggetto , che espone `Project.Object` `Project.CodeModel` e `ProjectItem` `ProjectItem.Object` `ProjectItem.FileCodeModel` .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Per contribuire a un oggetto specifico di VSPackage per un progetto

1. Aggiungere le chiavi appropriate al file *con estensione pkgdef* del pacchetto VSPackage.

     Ad esempio, ecco le impostazioni *PKGDEF* per il progetto di linguaggio C++:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Implementare il codice nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> metodo , come nell'esempio seguente.

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

     Nel codice è `g_wszAutomationProjects` il nome della raccolta di progetti. Il metodo crea un oggetto che implementa l'interfaccia e restituisce un puntatore all'oggetto `GetAutomationProjects` `Projects` `IDispatch` chiamante, come illustrato nell'esempio di codice seguente.

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

     Scegliere un nome univoco per l'oggetto di automazione. I conflitti di nomi sono imprevedibili e le collisioni causano l'arbitraria rimozione arbitraria di un nome di oggetto in conflitto se più tipi di progetto usano lo stesso nome. È necessario includere il nome aziendale o alcuni aspetti univoci del nome del prodotto nel nome dell'oggetto di automazione.

     `Projects`L'oggetto raccolta personalizzato è un punto di ingresso comodo per la parte rimanente del modello di automazione del progetto. L'oggetto del progetto è accessibile anche dalla <xref:EnvDTE.Solution> raccolta di progetti. Dopo aver creato il codice e le voci del Registro di sistema appropriate che forniscono agli utenti oggetti raccolta, l'implementazione deve fornire gli oggetti `Projects` standard rimanenti per il modello di progetto. Per altre informazioni, vedere [Modellazione di progetti](../../extensibility/internals/project-modeling.md).

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
