---
title: "Procedura: Registrare i tipi di File dell'Editor | Microsoft Docs"
ms.date: 03/22/2018
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f26b7421676081b32060dd4f342ee05098d90a7c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54980323"
---
# <a name="how-to-register-editor-file-types"></a>Procedura: Registrare i tipi di file dell'editor
Il modo più semplice per registrare i tipi di file editor consiste nell'usare gli attributi di registrazione forniti come parte di [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] classi framework (MPF) del pacchetto gestito. Se si implementa il pacchetto in native [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], è anche possibile scrivere uno script del Registro di sistema che si registra un editor e agli interni associati.

## <a name="registration-using-mpf-classes"></a>Registrazione tramite le classi MPF

### <a name="to-register-editor-file-types-using-mpf-classes"></a>Per registrare i tipi di file dell'editor con le classi MPF

1. Fornire il <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> classe con i parametri appropriati per l'editor nella classe del pacchetto VSPackage.

   ```
   [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,
        ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",
        TemplateDir = "..\\..\\Templates",
        NameResourceID = 106)]
   ```

    In cui *. Esempio* è l'estensione registrata per questo editor e "32" è il livello di priorità.

    Il `projectGuid` è il GUID per i tipi di file esterno, definito in <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid>. Viene fornito il tipo di file esterno, in modo che il file risultante non dovrà far parte del processo di compilazione.

    *TemplateDir* rappresenta la cartella che contiene i file di modello che sono inclusi con l'esempio di editor di base gestito.

    `NameResourceID` è definito nel *Resources.h* file del progetto BasicEditorUI e identifica l'editor come Editor"My".

2. Eseguire l'override del metodo <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> .

    Nell'implementazione del metodo di <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo, chiamare il <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> (metodo) e passare l'istanza della factory dell'editor come illustrato di seguito.

   ```csharp
   protected override void Initialize()
   {
       Trace.WriteLine (string.Format(CultureInfo.CurrentCulture,
       "Entering Initialize() of: {0}", this.ToString()));
       base.Initialize();
          //Create Editor Factory
       editorFactory = new EditorFactory(this);
       base.RegisterEditorFactory(editorFactory);
   }
   ```

    Questo passaggio registra la factory dell'editor sia le estensioni dell'editor.

3. Annullare la registrazione di factory dell'editor.

    Factory dell'editor viene automaticamente annullata quando viene eliminato il pacchetto VSPackage. Se l'oggetto della factory dell'editor implementa il <xref:System.IDisposable> interfaccia relativi `Dispose` viene chiamato dopo che la factory è stata annullarne la registrazione con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

## <a name="registration-using-a-registry-script"></a>Registrazione usando uno script del Registro di sistema
 La registrazione di factory dell'editor e tipi di file in native [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] viene eseguita usando uno script del Registro di sistema da scrivere nel Registro di sistema di windows, come illustrato di seguito.

### <a name="to-register-editor-file-types-using-a-registry-script"></a>Per registrare i tipi di file dell'editor tramite uno script del Registro di sistema

1.  Nello script del Registro di sistema, definire la factory dell'editor e la factory dell'editor stringa GUID come illustrato nel `GUID_BscEditorFactory` sezione dello script del Registro di sistema seguente. Inoltre, definire l'estensione e la priorità dell'estensione dell'editor:

    ```
          NoRemove Editors     {         %GUID_BscEditorFactory% = s 'RTF Editor'         {             val Package = s '%CLSID_Package%'             val DisplayName = s 'An RTF Editor'             val ExcludeDefTextEditor = d 1             val AcceptBinaryFiles = d 0

            LogicalViews
            {
                val %LOGVIEWID_TextView% = s ''
            }

            OpenWithEntries
            {
            }

            Extensions            {                val rtf = d 50            }
        }
    }
    ```

     L'estensione del file dell'editor in questo esempio viene identificato come *RTF* e la priorità è "50". Le stringhe GUID definite nelle *Resource. h* file BscEdit progetto di esempio.

2.  Registrare il pacchetto VSPackage.

3.  Registrare la factory dell'editor.

     La factory dell'editor è registrata nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implementazione.

    ```cpp
    // create editor factory.
    if (m_srpEdFact == NULL)
    {
        CComObject<CBscEditorFactory> *pEdFact = new CComObject<CBscEditorFactory>;
        if (NULL == pEdFact)
          return E_OUTOFMEMORY;

        if (!pEdFact->FInit(this))
          return E_UNEXPECTED;

        m_srpEdFact = (IVsEditorFactory *) pEdFact;    // Note: assignment to a smart pointer does an AddRef()
    }
    // Query service for IVsRegisterEditors, register the editor factory
    CComPtr<IVsRegisterEditors> srpRegEd;
    if ((SUCCEEDED(m_srpPkgSiteSP->QueryService(SID_SVsRegisterEditors, IID_IVsRegisterEditors,(void **)&srpRegEd ))) && (srpRegEd != NULL))
      {
        ATLTRACE(TEXT(">> CVsPackage, registering editor factory.\n"));
          if (FAILED(srpRegEd->RegisterEditor(GUID_BscEditorFactory,
                      m_srpEdFact, &m_dwEditorCookie)))
          {
             ATLTRACE(TEXT(">> CVsPackage, RegisterEditor() failed.\n"));
            return E_FAIL;
          }
      }
        return S_OK;
    }
    ```

     Le stringhe GUID definite nelle *Resource. h* file del progetto BscEdit.