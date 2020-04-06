---
title: Interfaccia della procedura guidata (IDTWizard) Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1c8d728a76097321e4e1f16640cab97599d6ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703268"
---
# <a name="wizard-interface-idtwizard"></a>Interfaccia della procedura guidata (IDTWizard)
L'ambiente di sviluppo integrato <xref:EnvDTE.IDTWizard> (IDE) utilizza l'interfaccia per comunicare con le procedure guidate. Le procedure guidate devono implementare questa interfaccia per essere installate nell'IDE.

 Il <xref:EnvDTE.IDTWizard.Execute%2A> metodo è l'unico <xref:EnvDTE.IDTWizard> metodo associato all'interfaccia. Le procedure guidate implementano questo metodo e l'IDE chiama il metodo sull'interfaccia. Nell'esempio seguente viene illustrata la firma del metodo.

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

 Il meccanismo di avvio è simile per le procedure guidate **Nuovo progetto** e **Aggiungi nuovo elemento.** Per avviare uno <xref:EnvDTE.IDTWizard> dei due, chiamare l'interfaccia definita in Dteinternal.h. L'unica differenza è il set di parametri di contesto e personalizzati che vengono passati all'interfaccia quando viene chiamata l'interfaccia.

 Le informazioni seguenti <xref:EnvDTE.IDTWizard> descrivono l'interfaccia che le [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] procedure guidate devono implementare per funzionare nell'IDE. L'IDE <xref:EnvDTE.IDTWizard.Execute%2A> chiama il metodo sulla procedura guidata, passando il seguente:

- L'oggetto DTE

     L'oggetto DTE è la radice del modello di automazione.

- Handle per la finestra di dialogo della `hwndOwner ([in] long)`finestra, come illustrato nel segmento di codice, .

     La procedura `hwndOwner` guidata lo utilizza come padre per la finestra di dialogo della procedura guidata.

- Parametri di contesto passati all'interfaccia come variant `[in] SAFEARRAY (VARIANT)* ContextParams`per SAFEARRAY, come illustrato nel segmento di codice, .

     I parametri di contesto contengono una matrice di valori specifici del tipo di procedura guidata avviata e dello stato corrente del progetto. L'IDE passa i parametri di contesto alla procedura guidata. Per ulteriori informazioni, vedere [Parametri di contesto](../../extensibility/internals/context-parameters.md).

- Parametri personalizzati passati all'interfaccia come variante per SAFEARRAY, come illustrato nel segmento di codice, `[in] SAFEARRAY (VARIANT)* CustomParams`.

     I parametri personalizzati contengono una matrice di parametri definiti dall'utente. Un file vsz passa parametri personalizzati all'IDE. I valori sono `Param=` determinati dalle istruzioni. Per ulteriori informazioni, vedere [Parametri personalizzati](../../extensibility/internals/custom-parameters.md).

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
