---
title: Interfaccia della procedura guidata (IDTWizard) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fb811f0ea6ae3d1be01b5d00f6359503d8f0d581
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526987"
---
# <a name="wizard-interface-idtwizard"></a>Interfaccia della procedura guidata (IDTWizard)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [interfaccia della procedura guidata (IDTWizard)](https://docs.microsoft.com/visualstudio/extensibility/internals/wizard-interface-idtwizard).  
  
L'ambiente di sviluppo integrato (IDE) usa il <xref:EnvDTE.IDTWizard> interfaccia per comunicare con le procedure guidate. Procedure guidate devono implementare questa interfaccia per essere installate nell'IDE.  
  
 Il <xref:EnvDTE.IDTWizard.Execute%2A> metodo è l'unico metodo associato il <xref:EnvDTE.IDTWizard> interfaccia. Procedure guidate implementano questo metodo e l'IDE chiama il metodo sull'interfaccia. Nell'esempio seguente viene indicata la firma del metodo.  
  
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
  
 Il meccanismo di avvio è simile per entrambi i **nuovo progetto** e **Aggiungi nuovo elemento**procedure guidate. Per avviare uno, si chiama il <xref:EnvDTE.IDTWizard> interfaccia definita nella Dteinternal.h. L'unica differenza è il set di contesto e i parametri personalizzati che vengono passati all'interfaccia quando viene chiamato l'interfaccia.  
  
 Le informazioni seguenti descrivono le <xref:EnvDTE.IDTWizard> interfaccia che devono implementare le procedure guidate per lavorare nel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE. Le chiamate dell'IDE di <xref:EnvDTE.IDTWizard.Execute%2A> metodo nella procedura guidata, passandogli quanto segue:  
  
-   L'oggetto DTE  
  
     L'oggetto DTE è la radice del modello di automazione.  
  
-   L'handle per la finestra di dialogo come illustrato nel segmento di codice, `hwndOwner ([in] long)`.  
  
     La procedura guidata Usa questo `hwndOwner` come elemento padre per la finestra di dialogo della procedura guidata.  
  
-   I parametri di contesto passato all'interfaccia di variant per SAFEARRAY come illustrato nel segmento di codice, `[in] SAFEARRAY (VARIANT)* ContextParams`.  
  
     I parametri di contesto contengono una matrice di valori specifici per il tipo di procedura guidata in corso l'avvio e lo stato corrente del progetto. L'IDE passa i parametri di contesto per la procedura guidata. Per altre informazioni, vedere [parametri di contesto](../../extensibility/internals/context-parameters.md).  
  
-   Parametri personalizzati passata all'interfaccia come variante per SAFEARRAY come illustrato nel segmento di codice, `[in] SAFEARRAY (VARIANT)* CustomParams`.  
  
     Parametri personalizzati contengono una matrice di parametri definiti dall'utente. Un file con estensione vsz passa parametri personalizzati all'IDE. I valori vengono determinati dal `Param=` istruzioni. Per altre informazioni, vedere [parametri personalizzati](../../extensibility/internals/custom-parameters.md).  
  
-   Valori restituiti per l'interfaccia sono  
  
    ```  
    wizardResultSuccess = -1,  
    wizardResultFailure = 0  
    wizardResultCancel = 1  
    wizardResultBackout = 2  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Parametri di contesto](../../extensibility/internals/context-parameters.md)   
 [Parametri personalizzati](../../extensibility/internals/custom-parameters.md)   
 [Procedure guidate](../../extensibility/internals/wizards.md)   
 [File (con estensione vsz) della procedura guidata](../../extensibility/internals/wizard-dot-vsz-file.md)

