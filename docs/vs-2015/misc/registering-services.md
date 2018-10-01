---
title: Registrazione di servizi | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, registering
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
manager: douge
ms.openlocfilehash: f56c73bbb09c659a76083e511d79d487402477ac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528626"
---
# <a name="registering-services"></a>Registrazione di servizi
Per supportare il caricamento su richiesta, un provider di servizi deve registrare i suoi servizi globali con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
 Durante lo sviluppo, provider di servizi gestiti registrano servizi e le sostituzioni di servizio aggiungendo attributi al codice sorgente per i pacchetti e quindi compilando i pacchetti [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE. Questo consente di eseguire l'utility RegPkg.exe sull'assembly risultante, registrare il pacchetto e prepararlo per la distribuzione. Per altre informazioni, vedere [procedura: registrare un servizio](../misc/how-to-register-a-service.md).  
  
 Provider di servizi non gestiti devono registrare i servizi che forniscono con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nei servizi di sezione o il servizio esegue l'override di sezione del Registro di sistema. Il frammento seguente del file REG mostra come potrebbe essere registrato il servizio SVsTextManager:  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 Nell'esempio precedente, numero di versione è la versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ad esempio 7.1 o 8.0, la chiave {F5E7E71D-1401-11d1-883B-0000F87579D2} è l'identificatore di servizio (SID) del servizio, SVsTextManager e le {il valore predefinito F5E7E720-1401-11D1-883B-0000F87579D2} è il GUID della gestione testo VSPackage, che fornisce il servizio del pacchetto.  
  
## <a name="remote-services-and-background-threads"></a>Servizi remoti e i thread in background  
 I servizi forniti non sono automaticamente disponibili in modalità remota o per i thread in background. Per renderli disponibili, è necessario compilare e registrare una libreria dei tipi.  
  
 Dal codice non gestito che usa la Libreria di Visual Studio (VSL), è possibile registrare la libreria dei tipi come nell'esempio che segue:  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE  
#include <VSLPackageDllEntryPoints.cpp>  
```  
  
 Dal codice gestito, è possibile aggiungere un passaggio post-compilazione come segue:  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Uso e fornitura di servizi](../extensibility/using-and-providing-services.md)   
 [Nozioni fondamentali sui servizi](../extensibility/internals/service-essentials.md)