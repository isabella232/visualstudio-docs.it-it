---
title: Esposizione di oggetti di progetto Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708479"
---
# <a name="expose-project-objects"></a>Esporre gli oggetti del progetto

I tipi di progetto personalizzati possono fornire oggetti di automazione per consentire l'accesso al progetto tramite interfacce di automazione. Ogni tipo di progetto deve <xref:EnvDTE.Project> fornire l'oggetto <xref:EnvDTE.Solution>di automazione standard a cui si accede da , che contiene un insieme di tutti i progetti aperti nell'IDE. Ogni elemento del progetto deve essere <xref:EnvDTE.ProjectItem> esposto `Project.ProjectItems`da un oggetto a cui si accede con . Oltre a questi oggetti di automazione standard, i progetti possono scegliere di offrire oggetti di automazione specifici del progetto.

È possibile creare oggetti di automazione a livello di radice personalizzati `DTE.<customObjectName>` `DTE.GetObject("<customObjectName>")`a cui è possibile accedere ad associazione tardiva dall'oggetto DTE radice utilizzando o . Ad esempio, in Visual Cè viene creata una raccolta di progetti specifici `DTE.VCProjects` `DTE.GetObject("VCProjects")`del progetto C, denominata *VCProjects* a cui è possibile accedere utilizzando o . È inoltre possibile `Project.Object`creare un oggetto , univoco `Project.CodeModel`per il tipo di progetto, un oggetto `ProjectItem`, su `ProjectItem.Object` cui `ProjectItem.FileCodeModel`è possibile eseguire una query per l'oggetto più derivato, nonché un oggetto , che espone e un oggetto .

È una convenzione comune per i progetti esporre una raccolta di progetti personalizzata, specifica del progetto. Ad esempio, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] viene creata una raccolta di progetti `DTE.VCProjects` specifica `DTE.GetObject("VCProjects")`di C, a cui è possibile accedere utilizzando o . È inoltre possibile `Project.Object`creare un oggetto , univoco `Project.CodeModel`per il tipo di progetto, un oggetto `ProjectItem`, su `ProjectItem.Object`cui `ProjectItem.FileCodeModel`è possibile eseguire una query per l'oggetto più derivato, un oggetto che espone , e un oggetto .

## <a name="to-contribute-a-vspackage-specific-object-for-a-project"></a>Per contribuire a un oggetto specifico di VSPackage per un progettoTo contribute a VSPackage-specific object for a project

1. Aggiungere le chiavi appropriate al file *con estensione pkgdef* del pacchetto VSPackage.

     Di seguito, ad esempio, sono riportate le impostazioni *di .pkgdef* per il progetto di linguaggio C:

    ```
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\Automation]
    "VCProjects"=""
    [$RootKey$\Packages\{F1C25864-3097-11D2-A5C5-00C04F7968B4}\AutomationEvents]
    "VCProjectEngineEventsObject"=""
    ```

2. Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> codice nel metodo, come nell'esempio seguente.

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

     Nel codice, `g_wszAutomationProjects` è il nome della raccolta di progetti. Il `GetAutomationProjects` metodo crea un `Projects` oggetto che `IDispatch` implementa l'interfaccia e restituisce un puntatore all'oggetto chiamante, come illustrato nell'esempio di codice seguente.

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

     Scegliere un nome univoco per l'oggetto di automazione. I conflitti di nomi sono imprevedibili e i conflitti causano l'espulsioni arbitraria di un nome di oggetto in conflitto se più tipi di progetto utilizzano lo stesso nome. È necessario includere il nome dell'azienda o un aspetto univoco del nome del prodotto nel nome dell'oggetto di automazione.

     L'oggetto raccolta personalizzato `Projects` è un punto di ingresso pratico per la parte rimanente del modello di automazione del progetto. L'oggetto progetto è <xref:EnvDTE.Solution> accessibile anche dalla raccolta di progetti. Dopo aver creato il codice appropriato e le `Projects` voci del Registro di sistema che forniscono ai consumer gli oggetti di raccolta, l'implementazione deve fornire gli oggetti standard rimanenti per il modello di progetto. Per ulteriori informazioni, consultate [Modellazione del progetto.](../../extensibility/internals/project-modeling.md)

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>
