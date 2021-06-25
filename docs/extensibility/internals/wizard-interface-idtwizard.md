---
title: Interfaccia della procedura guidata (IDTWizard) | Microsoft Docs
description: L'IDE usa l'interfaccia IDTWizard per comunicare con le procedure guidate. Le procedure guidate devono implementare questa interfaccia per essere installate nell'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 930996de7fa5366463ec2d60f7cf96d941f6c243
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898617"
---
# <a name="wizard-interface-idtwizard"></a>Interfaccia della procedura guidata (IDTWizard)
L'ambiente di sviluppo integrato (IDE) usa <xref:EnvDTE.IDTWizard> l'interfaccia per comunicare con le procedure guidate. Le procedure guidate devono implementare questa interfaccia per poter essere installate nell'IDE.

 Il <xref:EnvDTE.IDTWizard.Execute%2A> metodo è l'unico metodo associato <xref:EnvDTE.IDTWizard> all'interfaccia . Le procedure guidate implementano questo metodo e l'IDE chiama il metodo sull'interfaccia . Nell'esempio seguente viene illustrata la firma del metodo .

```
/* IDTWizard Method */
STDMETHOD(Execute)(THIS_
   /* [in] */ IDispatch *Application,
   /* [in] */ long hwndOwner,
   /* [in] */ SAFEARRAY * *ContextParams,
   /* [in] */ SAFEARRAY * *CustomParams,
   /* [out] [in] */ wizardResult *RetVal
   );
```

 Il meccanismo di avvio è simile  per le **procedure guidate Nuovo progetto** e Aggiungi nuovo elemento. Per iniziare, chiamare <xref:EnvDTE.IDTWizard> l'interfaccia definita in Dteinternal.h. L'unica differenza è il set di parametri di contesto e personalizzati passati all'interfaccia quando viene chiamata l'interfaccia .

 Le informazioni seguenti descrivono <xref:EnvDTE.IDTWizard> l'interfaccia che le procedure guidate devono implementare per funzionare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nell'IDE. L'IDE chiama <xref:EnvDTE.IDTWizard.Execute%2A> il metodo nella procedura guidata, passando il codice seguente:

- Oggetto DTE

     L'oggetto DTE è la radice del modello di automazione.

- Handle per la finestra di dialogo, come illustrato nel segmento di codice , `hwndOwner ([in] long)` .

     La procedura guidata lo usa `hwndOwner` come elemento padre per la finestra di dialogo della procedura guidata.

- Parametri di contesto passati all'interfaccia come variante per SAFEARRAY, come illustrato nel segmento di codice, `[in] SAFEARRAY (VARIANT)* ContextParams` .

     I parametri di contesto contengono una matrice di valori specifici del tipo di procedura guidata avviata e dello stato corrente del progetto. L'IDE passa i parametri di contesto alla procedura guidata. Per altre informazioni, vedere [Parametri di contesto](../../extensibility/internals/context-parameters.md).

- Parametri personalizzati passati all'interfaccia come variante per SAFEARRAY, come illustrato nel segmento di codice, `[in] SAFEARRAY (VARIANT)* CustomParams` .

     I parametri personalizzati contengono una matrice di parametri definiti dall'utente. Un file vsz passa parametri personalizzati all'IDE. I valori sono determinati dalle `Param=` istruzioni . Per altre informazioni, vedere [Parametri personalizzati](../../extensibility/internals/custom-parameters.md).

- I valori restituiti per l'interfaccia sono

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>Vedere anche
- [Parametri di contesto](../../extensibility/internals/context-parameters.md)
- [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)
