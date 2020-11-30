---
title: Parametri personalizzati | Microsoft Docs
description: Informazioni su come creare parametri personalizzati che controllano l'operazione di una procedura guidata dopo l'avvio di una procedura guidata, modificando un file con estensione vsz.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: f2fd2ba746f10094a79f1b37e57ba4ca90ff117b
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/30/2020
ms.locfileid: "96328444"
---
# <a name="custom-parameters"></a>Parametri personalizzati
I parametri personalizzati controllano l'operazione di una procedura guidata dopo l'avvio di una procedura guidata. Un file con *estensione vsz* correlato fornisce una matrice di parametri definiti dall'utente che vengono inseriti in un pacchetto dall'Integrated Development Environment (IDE) e passati alla procedura guidata come una matrice di stringhe quando viene avviata la procedura guidata. La procedura guidata analizza quindi la matrice di stringhe e usa le informazioni per controllare l'effettivo funzionamento della procedura guidata. In questo modo, una procedura guidata può personalizzare le funzionalità in base al contenuto del file con *estensione vsz* .

 I parametri di contesto, invece, definiscono lo stato del progetto quando viene avviata la procedura guidata. Per ulteriori informazioni, vedere [parametri di contesto](../../extensibility/internals/context-parameters.md).

 Di seguito è riportato un esempio di un file con *estensione vsz* con parametri personalizzati:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 L'autore del file con *estensione vsz* aggiunge i valori dei parametri. Quando un utente seleziona **nuovo progetto** o **Aggiungi nuovo elemento** dal menu **file** o facendo clic con il pulsante destro del mouse su un progetto in **Esplora soluzioni**, l'IDE raccoglie tali valori in una matrice di stringhe. L'IDE chiama quindi il metodo del progetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> con il <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> flag impostato e il progetto chiama il <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> Metodo responsabile dell'esecuzione della procedura guidata e la restituzione del risultato.

 La procedura guidata è responsabile dell'analisi della matrice di stringhe e della corretta azione delle stringhe. In questo modo, implementando parametri personalizzati è possibile creare una procedura guidata che esegue un'ampia gamma di funzioni. In altre parole, una procedura guidata potrebbe avere tre diversi file con *estensione vsz* . Ogni file passa set diversi di parametri personalizzati per controllare il comportamento della procedura guidata in varie situazioni.

 Per ulteriori informazioni, vedere [file della procedura guidata (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md).

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Parametri di contesto](../../extensibility/internals/context-parameters.md)
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [File della procedura guidata (VSZ)](../../extensibility/internals/wizard-dot-vsz-file.md)
