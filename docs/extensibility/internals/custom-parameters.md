---
title: Parametri personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 101076eb863294fe84ffed26d308f67110b90a33
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499452"
---
# <a name="custom-parameters"></a>Parametri personalizzati
Parametri personalizzati controllano il funzionamento di una procedura guidata dopo che è stata avviata una procedura guidata. Un correlati *vsz* file fornisce una matrice di parametri definiti dall'utente che vengono compresse dall'ambiente di sviluppo integrato (IDE) e passato alla procedura guidata come una matrice di stringhe quando viene avviata la procedura guidata. Quindi, la procedura guidata analizza la matrice di stringhe e utilizza le informazioni di controllo del funzionamento effettivo della procedura guidata. In questo modo, una procedura guidata è possibile personalizzare la funzionalità in base al contenuto del *vsz* file.  
  
 I parametri di contesto, d'altra parte, definiscono lo stato del progetto quando viene avviata la procedura guidata. Per altre informazioni, vedere [parametri di contesto](../../extensibility/internals/context-parameters.md).  
  
 Seguito è riportato un esempio di un *vsz* file con parametri personalizzati:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 L'autore del *vsz* file aggiunge i valori dei parametri. Quando un utente seleziona **nuovo progetto** o **Aggiungi nuovo elemento** sul **File** dal menu o facendo clic su un progetto in **Esplora soluzioni**, l'IDE raccoglie i valori in una matrice di stringhe. L'IDE chiama quindi il progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metodo con il <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> flag set e le chiamate di progetto di <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> metodo che è responsabile dell'esecuzione della procedura guidata e la restituzione del risultato.  
  
 La procedura guidata è responsabile per la matrice di stringhe di analisi e agire sulle stringhe in modo appropriato. In questo modo, implementando parametri personalizzati è possibile creare una procedura guidata che consente di eseguire un'ampia gamma di funzioni. In altre parole, una procedura guidata potrebbe avere tre diversi *vsz* file. Ogni file passa diversi set di parametri personalizzati per controllare il comportamento della procedura guidata in varie situazioni.  
  
 Per altre informazioni, vedere [file della procedura guidata (con estensione vsz)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [File della procedura guidata (con estensione vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)