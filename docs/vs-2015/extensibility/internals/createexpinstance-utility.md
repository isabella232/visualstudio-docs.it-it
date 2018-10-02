---
title: Utilità CreateExpInstance | Microsoft Docs
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
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f9b08ba5ac68a09f6c44937634375add3065e5e8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525933"
---
# <a name="createexpinstance-utility"></a>Utilità CreateExpInstance
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CreateExpInstance Utility](https://docs.microsoft.com/visualstudio/extensibility/internals/createexpinstance-utility).  
  
Usare l'utilità CreateExpInstance per creare, reimpostare, o eliminare un'istanza sperimentale di Visual Studio. È possibile utilizzare l'istanza sperimentale per eseguire il debug e testare le estensioni di Visual Studio senza modificare il prodotto sottostante.  
  
## <a name="syntax"></a>Sintassi  
  
```  
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix  
```  
  
#### <a name="parameters"></a>Parametri  
 / Creazione  
 Crea l'istanza sperimentale.  
  
 / Reset  
 Elimina l'istanza sperimentale e quindi ne crea uno nuovo.  
  
 /Clean  
 Elimina l'istanza sperimentale.  
  
 / VSInstance  
 Il nome della directory che contiene l'istanza di Visual Studio di base da copiare.  
  
 / RootSuffix  
 Suffisso da aggiungere al nome della directory istanza sperimentale.  
  
## <a name="remarks"></a>Note  
 Quando si lavora in un'estensione di Visual Studio, è possibile premere F5 per aprire l'istanza sperimentale predefinita e installare l'estensione corrente. Se non è disponibile alcuna istanza sperimentale, Visual Studio crea una con le impostazioni predefinite.  
  
 Il percorso predefinito dell'istanza sperimentale dipende dal numero di versione di Visual Studio. Ad esempio, per Visual Studio 2015, il percorso è %localappdata%\Microsoft\VisualStudio\14.0Exp\ tutti i file nel percorso della directory sono considerati parte di tale istanza. Eventuali altre istanze sperimentali non verranno caricate da Visual Studio a meno che non viene modificato il nome della directory nel percorso predefinito.  
  
 Visual Studio non accedere Registro di sistema quando si apre l'istanza sperimentale. Questo comportamento differisce dalle versioni precedenti di Visual Studio, che è usata una versione sperimentale dell'hive del Registro di sistema.  
  
 L'utilità CreateExpInstance sostituisce l'utilità VsRegEx.  
  
 L'esempio seguente ripristina l'istanza sperimentale predefinita di Visual Studio.  
  
 **CreateExpInstance.exe /Reset /VSInstance = 14.0 /RootSuffix Exp =**  
  
## <a name="see-also"></a>Vedere anche  
 [Il rilascio di un prodotto](../../misc/releasing-a-visual-studio-integration-product.md)

