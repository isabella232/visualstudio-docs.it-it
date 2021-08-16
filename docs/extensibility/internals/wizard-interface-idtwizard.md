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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 08a1ec6e79624d3f1eb74f9b5251a73523a998c739c7ea215e3622643c5b9926
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359143"
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

 Il meccanismo di avvio è simile per le **procedure guidate Project** e **Aggiungi nuovo** elemento. Per iniziare, chiamare <xref:EnvDTE.IDTWizard> l'interfaccia definita in Dteinternal.h. L'unica differenza è il set di parametri di contesto e personalizzati passati all'interfaccia quando viene chiamata l'interfaccia .

 Le informazioni seguenti descrivono <xref:EnvDTE.IDTWizard> l'interfaccia che le procedure guidate devono implementare per funzionare nell'IDE. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] L'IDE chiama <xref:EnvDTE.IDTWizard.Execute%2A> il metodo nella procedura guidata, passando il codice seguente:

- Oggetto DTE

     L'oggetto DTE è la radice del modello di automazione.

- Handle per la finestra di dialogo della finestra, come illustrato nel segmento di codice `hwndOwner ([in] long)` .

     La procedura guidata lo usa `hwndOwner` come elemento padre per la finestra di dialogo della procedura guidata.

- Parametri di contesto passati all'interfaccia come variante per SAFEARRAY, come illustrato nel segmento di codice , `[in] SAFEARRAY (VARIANT)* ContextParams` .

     I parametri di contesto contengono una matrice di valori specifici del tipo di procedura guidata avviata e dello stato corrente del progetto. L'IDE passa i parametri di contesto alla procedura guidata. Per altre informazioni, vedere [Parametri di contesto.](../../extensibility/internals/context-parameters.md)

- Parametri personalizzati passati all'interfaccia come variante per SAFEARRAY, come illustrato nel segmento di codice , `[in] SAFEARRAY (VARIANT)* CustomParams` .

     I parametri personalizzati contengono una matrice di parametri definiti dall'utente. Un file con estensione vsz passa parametri personalizzati all'IDE. I valori sono determinati dalle `Param=` istruzioni . Per altre informazioni, vedere [Parametri personalizzati.](../../extensibility/internals/custom-parameters.md)

- I valori restituiti per l'interfaccia sono

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>Vedi anche
- [Parametri di contesto](../../extensibility/internals/context-parameters.md)
- [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)
- [Procedure guidate](../../extensibility/internals/wizards.md)
- [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)
