---
title: Interfaccia della procedura guidata (IDTWizard) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f571fbd0a68ddbf56b637071ac250159461f61d1
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72721535"
---
# <a name="wizard-interface-idtwizard"></a>Interfaccia della procedura guidata (IDTWizard)
Il Integrated Development Environment (IDE) utilizza l'interfaccia <xref:EnvDTE.IDTWizard> per comunicare con le procedure guidate. Le procedure guidate devono implementare questa interfaccia per poter essere installate nell'IDE.

 Il metodo <xref:EnvDTE.IDTWizard.Execute%2A> è l'unico metodo associato all'interfaccia <xref:EnvDTE.IDTWizard>. Le procedure guidate implementano questo metodo e l'IDE chiama il metodo sull'interfaccia. Nell'esempio seguente viene illustrata la firma del metodo.

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

 Il meccanismo di avvio è simile per le procedure guidate **nuovo progetto** e **Aggiungi nuovo elemento** . Per iniziare, chiamare l'interfaccia <xref:EnvDTE.IDTWizard> definita in Dteinternal. h. L'unica differenza è rappresentata dal set di parametri di contesto e personalizzati passati all'interfaccia quando viene chiamata l'interfaccia.

 Le informazioni seguenti descrivono l'interfaccia <xref:EnvDTE.IDTWizard> che devono essere implementate dalle procedure guidate per lavorare nell'IDE di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. L'IDE chiama il metodo <xref:EnvDTE.IDTWizard.Execute%2A> nella procedura guidata, passandogli quanto segue:

- Oggetto DTE

     L'oggetto DTE è la radice del modello di automazione.

- Handle per la finestra di dialogo della finestra, come illustrato nel segmento di codice, `hwndOwner ([in] long)`.

     Questa `hwndOwner` viene utilizzata dalla procedura guidata come elemento padre per la finestra di dialogo della procedura guidata.

- Parametri di contesto passati all'interfaccia come Variant per SAFEARRAY, come illustrato nel segmento di codice, `[in] SAFEARRAY (VARIANT)* ContextParams`.

     I parametri di contesto contengono una matrice di valori specifici del tipo di procedura guidata avviata e dello stato corrente del progetto. L'IDE passa i parametri di contesto alla procedura guidata. Per ulteriori informazioni, vedere [parametri di contesto](../../extensibility/internals/context-parameters.md).

- Parametri personalizzati passati all'interfaccia come Variant per SAFEARRAY, come illustrato nel segmento di codice, `[in] SAFEARRAY (VARIANT)* CustomParams`.

     I parametri personalizzati contengono una matrice di parametri definiti dall'utente. Un file con estensione vsz passa parametri personalizzati all'IDE. I valori sono determinati dalle istruzioni `Param=`. Per ulteriori informazioni, vedere [parametri personalizzati](../../extensibility/internals/custom-parameters.md).

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