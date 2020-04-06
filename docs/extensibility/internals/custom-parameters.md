---
title: Parametri personalizzati Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd52a49daa7d57a21d8cb0896f7108efa09e32b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708940"
---
# <a name="custom-parameters"></a>Parametri personalizzati
I parametri personalizzati controllano il funzionamento di una procedura guidata dopo l'avvio di una procedura guidata. Un file *vsz* correlato fornisce una matrice di parametri definiti dall'utente che vengono inseriti nel pacchetto dall'ambiente di sviluppo integrato (IDE) e passati alla procedura guidata come matrice di stringhe all'avvio della procedura guidata. La procedura guidata analizza quindi la matrice di stringhe e utilizza le informazioni per controllare il funzionamento effettivo della procedura guidata. In questo modo, una procedura guidata può personalizzare la funzionalità in base al contenuto del file *vsz.*

 I parametri di contesto, d'altra parte, definiscono lo stato del progetto all'avvio della procedura guidata. Per ulteriori informazioni, vedere [Parametri di contesto](../../extensibility/internals/context-parameters.md).

 Di seguito è riportato un esempio di file *vsz* con parametri personalizzati:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 L'autore del file *vsz* aggiunge i valori dei parametri. Quando un utente seleziona **Nuovo progetto** o Aggiungi **nuovo elemento** dal Menu **File** o facendo clic con il pulsante destro del mouse su un progetto in **Esplora soluzioni**, l'IDE raccoglie questi valori in una matrice di stringhe. L'IDE chiama quindi <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> il metodo <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> del progetto con il <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> flag impostato e il progetto chiama il metodo responsabile dell'esecuzione della procedura guidata e della restituzione del risultato.

 La procedura guidata è responsabile dell'analisi della matrice di stringhe e dell'azione sulle stringhe in modo appropriato. In questo modo, implementando parametri personalizzati è possibile creare una procedura guidata che esegue un'ampia gamma di funzioni. In altre parole, una procedura guidata potrebbe avere tre diversi file *vsz.* Ogni file passa diversi set di parametri personalizzati per controllare il comportamento della procedura guidata in varie situazioni.

 Per ulteriori informazioni, vedere [File della procedura guidata (con estensione vsz).](../../extensibility/internals/wizard-dot-vsz-file.md)

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Parametri di contesto](../../extensibility/internals/context-parameters.md)
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [File della procedura guidata (vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
