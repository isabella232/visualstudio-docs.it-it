---
title: "Procedura: registrare i tipi di file dell'editor | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - register file types
ms.assetid: 54846779-8290-48de-90ab-81011559d9a5
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8d22e61d88b5f6e3959a369f6957efbc824384b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204123"
---
# <a name="how-to-register-editor-file-types"></a>Procedura: Registrare i tipi di file dell'editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il modo più semplice per registrare i tipi di file di editor consiste nell'usare gli attributi di registrazione forniti come parte delle [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] classi del Framework di pacchetto gestito (MPF). Se il pacchetto viene implementato in modalità nativa [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] , è anche possibile scrivere uno script del registro di sistema che registra l'editor e le estensioni associate.  
  
## <a name="registration-using-mpf-classes"></a>Registrazione tramite le classi MPF  
  
#### <a name="to-register-editor-file-types-using-mpf-classes"></a>Per registrare i tipi di file dell'editor tramite le classi MPF  
  
1. Specificare la <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute> classe con i parametri appropriati per l'editor nella classe del pacchetto VSPackage.  
  
    ```  
    [Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute(typeof(EditorFactory), ".Sample", 32,   
         ProjectGuid = "{A2FE74E1-B743-11d0-AE1A-00A0C90FFFC3}",   
         TemplateDir = "..\\..\\Templates",   
         NameResourceID = 106)]  
    ```  
  
     Dove ". Sample "è l'estensione registrata per questo editor e" 32 "è il livello di priorità.  
  
     `projectGuid`È il GUID per i tipi di file esterni, definito in <xref:Microsoft.VisualStudio.VSConstants.CLSID.MiscellaneousFilesProject_guid> . Viene fornito il tipo di file vario, in modo che il file risultante non faccia parte del processo di compilazione.  
  
     `TemplateDir` rappresenta la cartella che contiene i file modello inclusi nell'esempio di editor Basic gestito.  
  
     `NameResourceID` viene definito nel file resources. h del progetto BasicEditorUI e identifica l'editor come "My Editor".  
  
2. Eseguire l'override del metodo <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Nell'implementazione del <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo chiamare il <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> metodo e passare l'istanza della factory dell'editor, come illustrato di seguito.  
  
    ```  
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
  
     Questo passaggio registra sia la factory dell'editor sia le estensioni di file dell'editor.  
  
3. Annulla la registrazione delle factory dell'editor.  
  
     Le factory dell'editor vengono annullate automaticamente quando il pacchetto VSPackage viene eliminato. Se l'oggetto factory dell'editor implementa l' <xref:System.IDisposable> interfaccia, il `Dispose` metodo viene chiamato dopo che è stata annullata la registrazione della factory con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="registration-using-a-registry-script"></a>Registrazione tramite uno script del registro di sistema  
 La registrazione di Factory Editor e tipi di file in nativo [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] viene eseguita utilizzando uno script del registro di sistema per scrivere nel registro di sistema di Windows, come illustrato di seguito.  
  
#### <a name="to-register-editor-file-types-using-a-registry-script"></a>Per registrare i tipi di file dell'editor utilizzando uno script del registro di sistema  
  
1. Nello script del registro di sistema definire la factory dell'editor e la stringa GUID della factory dell'editor, come illustrato nella `GUID_BscEditorFactory` sezione dello script del registro di sistema seguente. Definire anche l'estensione e la priorità dell'estensione dell'Editor:  
  
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
  
     L'estensione di file dell'editor in questo esempio è identificata come ". RTF" e la relativa priorità è "50". Le stringhe GUID sono definite nel file Resource. h del progetto di esempio BscEdit.  
  
2. Registrare il pacchetto VSPackage.  
  
3. Registrare la factory dell'editor.  
  
     La factory dell'editor è registrata nell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> implementazione di.  
  
    ```  
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
  
     Le stringhe GUID sono definite nel file Resource. h del progetto BscEdit.
