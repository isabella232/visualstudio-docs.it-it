---
title: Parametri personalizzati | Microsoft Docs
description: Informazioni su come creare parametri personalizzati che controllano il funzionamento di una procedura guidata dopo l'avvio di una procedura guidata, modificando un file con estensione vsz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 3251b657d269a313cc160d041138aec0dba51235
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122063525"
---
# <a name="custom-parameters"></a>Parametri personalizzati
I parametri personalizzati controllano il funzionamento di una procedura guidata dopo l'avvio di una procedura guidata. Un file con estensione *vsz* correlato fornisce una matrice di parametri definiti dall'utente che vengono in pacchetto dall'ambiente di sviluppo integrato (IDE) e passati alla procedura guidata come matrice di stringhe all'avvio della procedura guidata. La procedura guidata analizza quindi la matrice di stringhe e usa le informazioni per controllare il funzionamento effettivo della procedura guidata. In questo modo, una procedura guidata può personalizzare le funzionalità a seconda del contenuto del file *con estensione vsz.*

 I parametri di contesto, d'altra parte, definiscono lo stato del progetto all'avvio della procedura guidata. Per altre informazioni, vedere [Parametri di contesto.](../../extensibility/internals/context-parameters.md)

 Di seguito è riportato un esempio di file *con estensione vsz* con parametri personalizzati:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 L'autore del file *con estensione vsz* aggiunge i valori dei parametri. Quando un utente seleziona Nuovo **Project** o Aggiungi nuovo elemento dal menu **File** o facendo clic con il pulsante destro del mouse su un progetto in **Esplora soluzioni**, l'IDE raccoglie questi valori in una matrice di stringhe.  L'IDE chiama quindi il metodo del progetto con il flag impostato e il progetto chiama il metodo responsabile dell'esecuzione della procedura guidata e <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> della restituzione del <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> risultato.

 La procedura guidata è responsabile dell'analisi della matrice di stringhe e dell'uso appropriato delle stringhe. In questo modo, implementando parametri personalizzati è possibile creare una procedura guidata che esegue un'ampia gamma di funzioni. In altre parole, una procedura guidata può avere tre diversi file con estensione *vsz.* Ogni file passa diversi set di parametri personalizzati per controllare il comportamento della procedura guidata in varie situazioni.

 Per altre informazioni, vedere [File della procedura guidata (con estensione vsz).](../../extensibility/internals/wizard-dot-vsz-file.md)

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Parametri di contesto](../../extensibility/internals/context-parameters.md)
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [File della procedura guidata (con estensione vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
