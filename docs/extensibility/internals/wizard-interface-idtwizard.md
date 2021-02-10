---
title: Interfaccia della procedura guidata (IDTWizard) | Microsoft Docs
description: L'IDE utilizza l'interfaccia IDTWizard per comunicare con le procedure guidate. Le procedure guidate devono implementare questa interfaccia per l'installazione nell'IDE.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: dc33d2fb37db7e021ce1752c642492a80956b61f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99935937"
---
# <a name="wizard-interface-idtwizard"></a>Interfaccia della procedura guidata (IDTWizard)
Il Integrated Development Environment (IDE) usa l' <xref:EnvDTE.IDTWizard> interfaccia per comunicare con le procedure guidate. Le procedure guidate devono implementare questa interfaccia per poter essere installate nell'IDE.

 Il <xref:EnvDTE.IDTWizard.Execute%2A> metodo è l'unico metodo associato all' <xref:EnvDTE.IDTWizard> interfaccia. Le procedure guidate implementano questo metodo e l'IDE chiama il metodo sull'interfaccia. Nell'esempio seguente viene illustrata la firma del metodo.

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

 Il meccanismo di avvio è simile per le procedure guidate **nuovo progetto** e **Aggiungi nuovo elemento** . Per iniziare, chiamare l' <xref:EnvDTE.IDTWizard> interfaccia definita in Dteinternal. h. L'unica differenza è rappresentata dal set di parametri di contesto e personalizzati passati all'interfaccia quando viene chiamata l'interfaccia.

 Le informazioni seguenti descrivono l' <xref:EnvDTE.IDTWizard> interfaccia che deve essere implementata dalle procedure guidate per lavorare nell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. L'IDE chiama il <xref:EnvDTE.IDTWizard.Execute%2A> metodo nella procedura guidata, passando il codice seguente:

- Oggetto DTE

     L'oggetto DTE è la radice del modello di automazione.

- Handle per la finestra di dialogo della finestra, come illustrato nel segmento di codice, `hwndOwner ([in] long)` .

     Questa procedura guidata viene utilizzata `hwndOwner` come elemento padre per la finestra di dialogo della procedura guidata.

- Parametri di contesto passati all'interfaccia come Variant per SAFEARRAY, come illustrato nel segmento di codice, `[in] SAFEARRAY (VARIANT)* ContextParams` .

     I parametri di contesto contengono una matrice di valori specifici del tipo di procedura guidata avviata e dello stato corrente del progetto. L'IDE passa i parametri di contesto alla procedura guidata. Per ulteriori informazioni, vedere [parametri di contesto](../../extensibility/internals/context-parameters.md).

- Parametri personalizzati passati all'interfaccia come Variant per SAFEARRAY, come illustrato nel segmento di codice, `[in] SAFEARRAY (VARIANT)* CustomParams` .

     I parametri personalizzati contengono una matrice di parametri definiti dall'utente. Un file con estensione vsz passa parametri personalizzati all'IDE. I valori sono determinati dalle `Param=` istruzioni. Per ulteriori informazioni, vedere [parametri personalizzati](../../extensibility/internals/custom-parameters.md).

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
