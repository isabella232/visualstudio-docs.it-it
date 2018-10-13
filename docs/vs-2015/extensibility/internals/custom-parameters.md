---
title: Parametri personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e8831517b7b679762e12356927b39e244a2a5dd1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305402"
---
# <a name="custom-parameters"></a>Parametri personalizzati
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Parametri personalizzati controllano il funzionamento di una procedura guidata dopo che è stata avviata una procedura guidata. Un file con estensione vsz correlati fornisce una matrice di parametri definiti dall'utente che vengono compresse dall'ambiente di sviluppo integrato (IDE) e passato alla procedura guidata come una matrice di stringhe quando viene avviata la procedura guidata. Quindi, la procedura guidata analizza la matrice di stringhe e utilizza le informazioni di controllo del funzionamento effettivo della procedura guidata. In questo modo, una procedura guidata può personalizzare la funzionalità in base al contenuto del file con estensione vsz.  
  
 I parametri di contesto, d'altra parte, definiscono lo stato del progetto quando viene avviata la procedura guidata. Per altre informazioni, vedere [parametri di contesto](../../extensibility/internals/context-parameters.md).  
  
 Ecco un esempio di un file con estensione vsz con parametri personalizzati:  
  
```  
VSWIZARD 8.0  
Wizard=VsWizard.VsWizard_Engine  
Param="WIZARD_NAME = Sample Wizard"  
Param="WIZARD_UI = FALSE"  
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"  
Param="PREPROCESS_FUNCTION = CanAddATLSupport"  
Param="PROJECT_TYPE = CSPROJ"  
```  
  
 L'autore del file con estensione vsz aggiunge i valori dei parametri. Quando un utente seleziona **nuovo progetto** oppure **Aggiungi nuovo elemento** dal menu File o facendo clic su un progetto in **Esplora**, l'IDE raccoglie i valori in una matrice di stringhe. L'IDE chiama quindi il progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> metodo con il <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> flag set e le chiamate di progetto di <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> metodo che è responsabile dell'esecuzione della procedura guidata e la restituzione del risultato.  
  
 La procedura guidata è responsabile per la matrice di stringhe di analisi e agire sulle stringhe in modo appropriato. In questo modo, implementando parametri personalizzati è possibile creare una procedura guidata che consente di eseguire un'ampia gamma di funzioni. In altre parole, una procedura guidata può avere tre file con estensione vsz diversi. Ogni file passa diversi set di parametri personalizzati per controllare il comportamento della procedura guidata in varie situazioni.  
  
 Per altre informazioni, vedere [Wizard (. File vsz)](../../extensibility/internals/wizard-dot-vsz-file.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>   
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)

