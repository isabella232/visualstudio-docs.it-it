---
title: Informazioni sulle estensioni di file | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- file extensions
- file name extensions
ms.assetid: 99f4f9ff-fb84-4258-9787-6890f308a57f
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 866a30279ca2c79f4a490a040f76bc3a86c6a6e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148039"
---
# <a name="about-file-name-extensions"></a>Informazioni sulle estensioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si registra un'estensione di file di un pacchetto VSPackage, questo viene associato a una versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Questo è importante se [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in un computer è installata più di una versione di.  
  
 Le estensioni di file per i pacchetti VSPackage sono registrate in HKEY_CLASSES_ROOT chiave con un valore predefinito che punta all'identificatore a livello di codice (ProgID) associato.  
  
 Di seguito è riportato un esempio delle informazioni di registrazione per l'estensione di file. vcproj:  
  
```  
HKEY_CLASSES_ROOT\  
   .vcproj\  
      (default)=" VisualStudio.vcproj.8.0"   
```  
  
 I file associati a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] devono disporre di un ProgID con versione, ad esempio `VisualStudio.vcproj.8.0` , per consentire installazioni affiancate del prodotto per mantenere le associazioni dell'estensione di file tra le versioni del prodotto. Un ProgID specifico della versione consente anche di usare verbi standard, ad esempio Open, Edit e così via, senza dover sovrascrivere o essere sovrascritti da altre applicazioni o versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 In alcuni casi, il ProgID associato a un'estensione di file non deve essere modificato. Il ProgID per l'estensione di file htm (ProgID = htmlfile), ad esempio, è hardcoded in numerose posizioni del sistema operativo ed è ampiamente noto e utilizzato in associazione ai file con estensione htm e HTML.  
  
## <a name="see-also"></a>Vedere anche  
 [Registrazione delle estensioni di file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Definizione dei gestori di file per le estensioni di file](../extensibility/specifying-file-handlers-for-file-name-extensions.md)
